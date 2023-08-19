Hi there!

This article intends to explain a bit about nuvigator, building a simple application to demostrate how to navigate from one screen to another and how to send parameters. Enjoy it!

## What's nuvigator?

Nuvigator is a flutter package for navigation, written on top of flutter navigation. It's a package that was created by nubank and wants do add new functionalities, such as deep links, also have support for nested routes and can help with modular apps. [Check additional info here](https://github.com/nubank/nuvigator/)

## Example

For this example, we're going to create an app `nuvigatorexample` using the flutter cli:

`flutter create nuvigatorexample`

### Installing the package

The current version of nuvigator is 0.7.2, that's does not support null safety and will throw an error when trying to run the app, so it's necessary to change the sdk version.

Inside pubspec.yaml, change the sdk version:

`sdk: ">=2.11.0 <3.0.0"`

and add nuvigator to dependencies:

```dart
dependencies:
  flutter:
    sdk: flutter
  nuvigator:
```

Now install the package, you can use your ide or type the following command on terminal:

`flutter pub get`

### Building the app

Let's build an example using nuvigator to navigate between two screens.

The first screen, Home, will have a button that navigates to the second screen, Details.

Our home_screen.dart:

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

Our details_screen.dart:

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

Our main.dart:

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

[Commit with these changes](https://github.com/wps13/nuvigator-example/commit/05a829b62bf96efb5b71b6d7ad28b3e9927418bd)

![Gif showing a screen with white background, blue app bar with the text home and a button written 'Navigate to details', then shows a second screen showing a app bar with the title 'details' and a text](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/6vpuginwm932zux1azg6.gif)

### Using a router

Inside our home_screen, we gonna add a new class that will extend a NuRoute:

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

We're going to do the same for our details_screen:

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

Now we must create our router inside main.dart, creating a new class that extends NuRouter and changing the MaterialApp home:

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

This should have the same result as the previous navigation.

[Commit with changes](https://github.com/wps13/nuvigator-example/commit/7222e6f2db9b3731584b5bceb3823ca6eea4d79b)

### Passing parameters to details screen

Now, let's send a personalized text to our details screen.

First, we must define the text as a parameter in the pushNamed function:

```
nuvigator.pushNamed('details', arguments: {'message': 'Hello world'});
```

Then, we must get this parameter inside our details screen, using nuvigator settings raw parameters.

Insider the DetailsRoute build method, let's get the message:

```dart
final String message = settings.rawParameters['message'];
```

and then inside our DetailsScreen, we're going do add a new prop called message and use it to render:

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

[Commit with changes](https://github.com/wps13/nuvigator-example/commit/82a5c520917008a08861fd760a071ad8e15ecd9b)

Result:

![Gif showing an app with a screen with blue app bar and a button with 'Navigate to details', then a second screen with the text 'hello world'](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/ux6oedjhuddn9b4jwicn.gif)
