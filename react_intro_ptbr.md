**O que é React?**

React é um biblioteca criada pelo facebook, que permite criar interfaces de usuário, usando componentes customizados, construidos a partir de elementos do html. É baseada no conceito de single page application (SPA), que seria um aplicação onde tudo seria uma única página, trocando os elementos da mesma para construir novas páginas, sem precisar recarregar a página.

Por ser uma biblioteca, não vem com todas as ferramentas necessárias, sendo assim necessário fazer uso de outras bibliotecas. No React não é dito como deve ser construida a interface e sim o que se deseja ser construido, então o react irá transformar o código escrito para ser interpretado. Também é considerada reativa, pois reage a evento, sobrecarga de requisições etc e responde de maneira adequada.

**Por que usar?**

- Reutilização de componentes
- Performance
- Abstração

**O que preciso saber antes de começar a estudar?**

- Html
- Css
- Javascript
  - Arrow functions
  - Spread/ Rest operator
  - Map, reduce e filter

**Virtual DOM**

O virtual DOM seria uma representação na memória do DOM criado, o que permite que o DOM não precise ser atualizado por completo com novas modificações, o react compara o DOM com o virtual DOM e altera apenas os elementos que forem diferentes entre eles.

**JSX**

O JSX é um javascript extendindo que permite escrever html em conjunto com o javascript, ele é usado para facilitar a escrita da codificação.

Após ser compilado, é transformado em chamadas de função, que retornam objetos.

```js
const header = <h1 className="header">Hello</h1>
```

```js
const header = React.createElement(
  'h1',
  props: {
  className: 'header',
  children: 'Hello'
  }
);
```

**Componentes**

O componente é um bloco de construção, que funcionam como funções, recebendo parâmetros e retornando elementos React. Para criar um componente é necessário criar uma função ou uma classe, colocando o nome com letra inicial maiúscula. Os componentes permitem isolar e reaproveitar código, pois os parâmetros que recebem, também chamados de props, possibilitam usar diferentes valores para serem exibidos, assim como passar outros componentes. A reutilização de código deve ser feita usando o conceito de composição invés de herança, pois assim será considerado o que será feito com o valor, não o seu tipo.
O componente permite usar props padrão, para caso onde não seja passada uma dada props. Isto ocorre por meio do uso do _defaultProps_

```js
element.defaultProps = {
  color: "Red",
}
```

- funcionais

  Componentes funcionais são construidos a partir de funções, que devem agir como funções pura, não modificando os valores de entrada.

```js
import React from "react"

const Hello = () => <h2>Hello</h2>

export default Hello
```

- Baseados em classes

  Os componentes baseados em classe possuem mais funcionalidades que os componentes funcionais, pois estendem o Component. Esses componentes devem conter um método _render_ obrigatoriamente, pois esse método é responsável pela renderização.

```js
import React, { Component } from "react"

class Hello extends Component {
  render() {
    return <h2>Hello</h2>
  }
}

export default Hello
```

    Além dessa propriedade, os componentes de classe tem a string _displayName_, que é usada para depuração. Existe também a API _forceUpdate_, que não checa o resultado do método _shouldComponentUpdate_ e força uma renderização.

```js
component.forceUpdate(callback)
```

- Ciclo de vida

  - Montagem

    Componente está sendo montando, Dom sendo montado. Ideal para fazer requisições de dados e para inicializar dados no construtor.

    _Métodos disponíveis:_

          - constructor
          - static getDerivedStateFromProps
          - render
          - componentDidMount

  - Atualização

    É causada por uma alteração em estado ou props

    _Métodos disponíveis:_

          - static getDerivedStateFromProps
          - shouldComponentUpdate
          - render
          - getSnapshotBeforeUpdate
          - componentDidUpdate

  - Desmontagem

    Componente será removido do DOM.

    _Métodos disponíveis:_

          - componentWillUnmount

  - Tratamento de erros

    Erros na renderização, método do ciclo de vida, ou construtor de componente filho.

    _Métodos disponíveis:_

          - static getDerivedStateFromError
          - componentDidCatch


- Propriedades

  As propriedades dos componentes, mais conhecidas como props, são elementos passados de um componente pai para um filho. Elas permitem passar qualquer tipo de dado, pois não é necessário especificar o tipo e sim sua identificação.
  Em componentes de class é necessário que elas sejam inicializadas no construtor, pois assim o _this_ será referenciado corretamente e terá acesso a elas dentro da classe.

```js
  constructor(super) {
        super(props);
 }
```

- Estado

  O estado é responsável por ser um indicador de atualização da interface, assim como guarda algumas informações. O estado é assíncrono, assim só terá seu valor atualizado na atualização seguinte, portanto não deve ser alterado diretamente.

  Para componentes de classe, eles são inicializados no construtor, sendo um objeto que é alterado por meio da função setState. Essa função recebe o nome e valor e acrescenta ao objeto já existente. O setState também aceita que seja recebido uma função que irá atualizar o estado e uma callback, a ser executada após o estado ter sido definido.

```js
   constructor(props){
       super(props);
       this.state: {
           message: 'Hello'
       }
   }

   this.setState({ name: 'Person' }); // forma 1
   this.setState(state => ({name: 'Person'}), callback); // forma 2

```

    Para componentes funcionais, o estado é inicializado e modificado usando o hook useState, que recebe como parâmetro o valor inicial da propriedade, caso seja um valor ou recebe um objeto.

```js
let [message, setMessage] = useState("Hello")
let [state, setState] = useState({ message: "Hello", name: "Person" })
```
