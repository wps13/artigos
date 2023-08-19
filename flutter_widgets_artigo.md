O flutter funciona combinando widgets como se fossem legos para conseguir um determinado layout. Neste artigo, irei apresentar alguns widgets que permitem construir uma variedade de telas quando combinados.

## Widgets essenciais

### Text

Text renderiza um texto na tela, onde o texto pode ser dinâmico ou estático. É possível customizar o estilo, mudando várias propriedades como fonte, peso, além de definir como o texto será tratado em caso de overflow, se irá dar wrap entre outros.

Exemplo com texto estático

```dart
Text('olá mundo');
```

Exemplo com dado dinâmico

```dart
const greeting = (name) => 'Olá, $name';

Text(greeting('Maria'));
```

![Renderização de um widget Text no flutter](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/tobdrq9uob5lok1mnpjd.png)

### Container

O Container é um widget que possui apenas um filho e pode ter diferentes propriedades, como `color` que pode ser usada para pintar o fundo e `decoration` que nos permite criar bordas, é possível usar color ou decoration, um de cada vez.

Exemplo usando cor de fundo:

```dart
Container(
	color: Colors.red,
  child: Text('Container'),
);
```

Exemplo usando decoration para definir a cor de fundo:

```dart
Container(
        decoration: BoxDecoration(
          color: Colors.red,
        ),
        child: const Text('Container'),
);
```

![Renderização de um widget Container vermelho com texto Container no flutter](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/wv12d9x1vud2dgnfj65p.png)

### SizedBox

SizedBox é um widget que nos permite criar um widget com altura, largura ou ambos fixos. É um widget que tem apenas uma criança que é opcional.

```dart
SizedBox(height: 6);
```

![Renderização de um sized box no flutter](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/cmmj82ps57kq2pl0jagz.png)

### Padding

O Padding é um widget que cria espaço dentro de um widget, similar ao padding do CSS.

```dart
Padding(
	padding: EdgeInsets.all(16),
	child: Text('Widget A'),
);
```

![Exemplo de uso do Padding no flutter](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/2qjx2hou5iu2rivyfwec.png)

### Column

Column é um widget que empilha os widgets verticalmente. É um widget do tipo flex, então toma todo o espaço que tiver sobrando.

Exemplo de uso:

```dart
Column(
  children: [
		Container(color: Colors.red),
		Container(color: Colors.blue),
	],
);
```

Exemplo mais completo:

```dart
class MyWidget extends StatelessWidget {
  const MyWidget({super.key});

  @override
  Widget build(BuildContext context) {
    return SizedBox(
      height: 620,
      child: Column(
        mainAxisAlignment: MainAxisAlignment.spaceBetween,
        crossAxisAlignment: CrossAxisAlignment.stretch,
        children: [
          Container(
            height: 150,
            alignment: Alignment.center,
            child: const Text('Widget A'),
          ),
          const Divider(
            height: 1,
            color: Colors.black,
          ),
          Container(
            height: 150,
            alignment: Alignment.center,
            child: const Text('Widget B'),
          ),
          const Divider(
            height: 1,
            color: Colors.black,
          ),
          Container(
            height: 150,
            alignment: Alignment.center,
            child: const Text('Widget C'),
          ),
          const Divider(
            height: 1,
            color: Colors.black,
          ),
          Container(
            height: 150,
            alignment: Alignment.center,
            child: const Text('Widget D'),
          ),
          const Divider(
            height: 1,
            color: Colors.black,
          ),
        ],
      ),
    );
  }
}
```

![Renderização de widget de column](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/x46ysn3vb7v3tntsiccl.png)

### Row

Similar ao Column, o Row empilha os itens horizontalmente.

```dart
Row(
  children: [
		Container(color: Colors.red),
		Container(color: Colors.blue),
	],
);
```

Exemplo mais completo:

```dart
class MyWidget extends StatelessWidget {
  const MyWidget({super.key});

  @override
  Widget build(BuildContext context) {
    return Container(
      height: 300,
      width: 600,
      decoration: BoxDecoration(border: Border.all()),
      child: Row(
        mainAxisAlignment: MainAxisAlignment.spaceBetween,
        crossAxisAlignment: CrossAxisAlignment.stretch,
        children: [
          Container(
            width: 150,
            alignment: Alignment.center,
            child: const Text('Widget A'),
          ),
          Container(
            width: 1,
            color: Colors.black,
          ),
          Container(
            width: 150,
            alignment: Alignment.center,
            child: const Text('Widget B'),
          ),
          Container(
            width: 1,
            color: Colors.black,
          ),
          Container(
            width: 150,
            alignment: Alignment.center,
            child: const Text('Widget C'),
          ),
          Container(
            width: 1,
            color: Colors.black,
          ),
        ],
      ),
    );
  }
}


```

![Renderização de widget de row](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/iyqi4ze751ca3bhswvc2.png)

### SingleChildScrolView

SingleChildScrollView cria um widget rolável com apenas um filho, útil quando o tamanho do filho é dinâmico.

Exemplo de uso

```dart
SingleChildScrollView(
	child: Text('long text here')
);
```

Exemplo mais completo

```dart
class MyWidget extends StatelessWidget {
  const MyWidget({super.key});

  @override
  Widget build(BuildContext context) {
    return SingleChildScrollView(
      child: SizedBox(
        height: MediaQuery.of(context).size.height * 2,
        child: Column(
          mainAxisAlignment: MainAxisAlignment.spaceBetween,
          crossAxisAlignment: CrossAxisAlignment.stretch,
          mainAxisSize: MainAxisSize.min,
          children: [
            Flexible(
              child: Container(
                color: Colors.blue,
                alignment: Alignment.center,
                child: const Text('Widget A'),
              ),
            ),
            Flexible(
              child: Container(
                color: Colors.green,
                alignment: Alignment.center,
                child: const Text('Widget B'),
              ),
            ),
            Flexible(
              child: Container(
                color: Colors.yellow,
                alignment: Alignment.center,
                child: const Text('Widget C'),
              ),
            ),
          ],
        ),
      ),
    );
  }
}

```

![Renderização de SingleChildScrollView no flutter](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/qv9irzdgp0vpkjog6jvg.png)
