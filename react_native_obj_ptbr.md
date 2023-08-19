Olá!

Quando trabalhamos com dados no React native, normalmente usamos arrays, que são mais fáceis de usar com flatlists. Modificar qualquer dado em um array é uma tarefa computacional complexa, especialmente a medida que o conjunto de dados cresce. Por exemplo, se temos um array de strings e queremos encontrar uma string, teríamos que percorrer todo o array para encontra-la, então quanto maior o array maior o tempo gasto nesta operação.

Para corrigir o problema acima é possível usar objetos com identificadores únicos, que seria bem mais fácil e rápido de manipular o conjunto de dados.

Então, como faremos isso?

Primeiro, vamos dar uma olhada no seguinte exemplo:

```javascript
const App = () => {
  const [data] = useState([
    {
      name: "Joao",
      job: "Developer",
    },
    {
      name: "Maria",
      job: "CEO",
    },
  ])

  const _renderItem = ({ item }) => {
    return (
      <View style={styles.view}>
        <Text style={[styles.text, styles.titleText]}>{item?.name}</Text>
        <Text style={styles.text}>{item?.job}</Text>
      </View>
    )
  }

  const _keyExtractor = (item) => {
    return item.name
  }

  return (
    <SafeAreaView>
      <FlatList
        renderItem={_renderItem}
        data={data}
        keyExtractor={_keyExtractor}
      />
    </SafeAreaView>
  )
}
```

Que renderizará a seguinte tela:

![Screenshot de um emulador android, mostrando cards azuis, o primeiro tem o texto Joao Developer e o segundo Maria CEO](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/iobw3nmgn56swlbjz6xq.png)

Para converter para objeto, nós teríamos que mudar como inicializamos os dados e como a flatlist o usa.

Começando com a inicialização, poderíamos usar um identificar único, nesse caso vamos usar o padrão 'user-x', onde x é um inteiro, resultando no seguinte formato:

```javascript
{
    'user-1': {
      name: 'Joao',
      job: 'Developer',
    },
    'user-2': {
      name: 'Maria',
      job: 'CEO',
    },
  }
```

Então, nós deveríamos mudar as props da flatlist, já que temos um objeto e a props de data espera um array, poderíamos usar object.entries para obter um array, por exemplo se tivéssemos um objeto assim:

```javascript
const data = { "user-1": { name: "Maria" } }
```

Object.entries nos retornaria:

```javascript
;[["user-1", { name: "Maria" }]]
```

Este resultado mostra que também teriam que mudar a função render item, já que o item recebido da flatlist é agora um array:

```js
const _renderItem = ({ item }) => {
  const [_, itemData] = item

  return (
    <View style={styles.view}>
      <Text style={[styles.text, styles.titleText]}>{itemData?.name}</Text>
      <Text style={styles.text}>{itemData?.job}</Text>
    </View>
  )
}
```

O código completo:

```javascript
const App = () => {
  const [data] = useState({
    "user-1": {
      name: "Joao",
      job: "Developer",
    },
    "user-2": {
      name: "Maria",
      job: "CEO",
    },
  })

  const _renderItem = ({ item }) => {
    const [_, itemData] = item

    return (
      <View style={styles.view}>
        <Text style={[styles.text, styles.titleText]}>{itemData?.name}</Text>
        <Text style={styles.text}>{itemData?.job}</Text>
      </View>
    )
  }

  const _keyExtractor = (item) => {
    const [key] = item

    return key
  }

  return (
    <SafeAreaView>
      <FlatList
        renderItem={_renderItem}
        data={Object.entries(data)}
        keyExtractor={_keyExtractor}
      />
    </SafeAreaView>
  )
}
```

## Vantagens de usar objeto

Como mencionado acima, usar um objeto seria melhor para performance, especialmente quando modificando os dados. Por exemplo, se esta lista tivesse opção para remover um item ou adicionar um novo, seria mais rápido remover o dado do objeto considerando que já teríamos o identificado.
