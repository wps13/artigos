Olá!

Este artigo tem como objetivo explicar um pouco sobre o nuvigator, construindo uma aplicação simples para mostrar como navegar de uma tela para outra e como enviar parâmetros.

## O que é o nuvigator?

Nuvigator é um pacote flutter para navegação, feito em cima do flutter navigation. É um pacote que foi criado pelo Nubank e que tem como objetivo adicionar novas funcionalidades, como deep links, também tem suporte a rotas aninhadas e pode ajudar com aplicativos modulares. [Confira aqui mais sobre o pacote](https://github.com/nubank/nuvigator/)

## Exemplo

Para este exemplo, nós criaremos um app `nuvigatorexample` usando a cli do flutter:

`flutter create nuvigatorexample`

### Instalando o pacote

A versão atual do nuvigator é 0.7.2, que não tem suporte ao null safety, e irá disparar um erro ao tentar rodar o app, então é necessário mudar a versão do sdk.

Dentro do arquivo pubspec.yaml, mude a versão do sdk:

`sdk: ">=2.11.0 <3.0.0"`

e adicione o nuvigator nas dependências:

```dart
dependencies:
  flutter:
    sdk: flutter
  nuvigator:
```

Agora instale o pacote, você pode usar sua IDE ou digitar o seguinte comando no terminal:

`flutter pub get`

### Construindo o app

Vamos criar um exemplo usando nuvigator para navegar entre duas telas.

A primeira tela, Home, vai ter um botão que navega para a segunda tela, Details.

Nossa home_screen.dart:

```dart
import 'package:flutter/material.dart';

class HomeScreen extends StatelessWidget {
  final Function onPressed;

  const HomeScreen({Key key, this.onPressed}) : super(key: key);

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: const Text('Home')),
      body: Center(
          child: ElevatedButton(
        onPressed: onPressed,
        child: const Text('Navigate to details'),
      )),
    );
  }
}
```

Nossa details_screen.dart:

```dart
import 'package:flutter/material.dart';

class DetailsScreen extends StatelessWidget {
  const DetailsScreen({Key key}) : super(key: key);

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: const Text('Details')),
      body: const Center(child: Text('Details screen')),
    );
  }
}
```

Nosso main.dart:

```dart
import 'package:flutter/material.dart';
import 'package:nuvigator/next.dart';
import 'package:nuvigatorexample/screens/details_screen.dart';
import 'package:nuvigatorexample/screens/home_screen.dart';

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({Key key}) : super(key: key);

  // This widget is the root of your application.
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Flutter Demo',
      theme: ThemeData(
        primarySwatch: Colors.blue,
      ),
      home: Nuvigator.routes(initialRoute: 'home', routes: [
        NuRouteBuilder(path: 'home', builder: (BuildContext contextNuvigator, __, ___) => HomeScreen(onPressed: (){
          Nuvigator.of(contextNuvigator).open('details');
        },), screenType: materialScreenType),
        NuRouteBuilder(
            path: 'details', builder: (_, __, ___) => const DetailsScreen(), screenType: materialScreenType)
      ]),
    );
  }

}
```

[Commit com essas mudanças](https://github.com/wps13/nuvigator-example/commit/05a829b62bf96efb5b71b6d7ad28b3e9927418bd)

![Gif mostrando uma tela com fundo branco, app bar azul com o texto 'home' e um botão escrito 'Navigate to details', então mostra uma segunda tela mostrando uma app bar com o titulo 'details' e um texto](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/6vpuginwm932zux1azg6.gif)

### Usando um router

Dentro da nossa home_screen, vamos adicionar uma nova classe que estende NuRoute:

```dart
import 'package:nuvigator/next.dart';

class HomeRouter extends NuRoute {
  @override
  Widget build(BuildContext context, NuRouteSettings<Object> settings) {
    return HomeScreen(onPressed: (){
      nuvigator.pushNamed('details');
    },);
  }

  @override
  String get path => 'home';

  @override
  ScreenType get screenType => materialScreenType;

}
```

Vamos fazer o mesmo para a details_screen:

```dart
import 'package:nuvigator/next.dart';

class DetailsRoute extends NuRoute {
  @override
  Widget build(BuildContext context, NuRouteSettings<Object> settings) {
    return DetailsScreen();
  }

  @override
  String get path => 'details';

  @override
  ScreenType get screenType => materialScreenType;

}
```

Agora devemos criar nosso router dentro do main.dart, criando uma nova classe que estende NuRouter e mudando o MaterialApp home:

```dart
class Router extends NuRouter{
  @override
  String get initialRoute => 'home';

  @override
  List<NuRoute<NuRouter, Object, Object>> get registerRoutes => [
    HomeRouter(),
    DetailsRoute()
  ];

}

class MyApp extends StatelessWidget {
  const MyApp({Key key}) : super(key: key);

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Flutter Demo',
      theme: ThemeData(
        primarySwatch: Colors.blue,
      ),
      home: Nuvigator(router: Router()),
    );
  }

}
```

Isto deve ter o mesmo resultado que a navegação anterior.

[Commit com as mudanças](https://github.com/wps13/nuvigator-example/commit/7222e6f2db9b3731584b5bceb3823ca6eea4d79b)

### Passando parâmetros para a tela de details

Agora, vamos enviar um texto personalizado para a tela details.

Primeiro, nos devemos definir um texto como parâmetro na função pushNamed:

```
nuvigator.pushNamed('details', arguments: {'message': 'Hello world'});
```

Então, conseguimos recuperar este parâmetro dentro da tela details, usando os raw parameters do nuvigator settings.

Vamos recuperar a mensagem dentro do método build do DetailsRoute:

```dart
final String message = settings.rawParameters['message'];
```

E então dentro da nossa DetailsScreen, vamos adicionar uma nova prop chamada `message` e usar para renderizar a mensagem:

```dart
class DetailsScreen extends StatelessWidget {
  final String message; // text from route
  const DetailsScreen({Key key, this.message}) : super(key: key);

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: const Text('Details')),
      body: Center(child: Text(message)),
    );
  }
}
```

[Commit com as mudanças](https://github.com/wps13/nuvigator-example/commit/82a5c520917008a08861fd760a071ad8e15ecd9b)

Resultado:

![Gif mostrando um app com a tela com uma app bar azul e um botão 'Navigate  to details', e então uma segunda tela com o tela com o texto 'Hello World'](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/ux6oedjhuddn9b4jwicn.gif)
