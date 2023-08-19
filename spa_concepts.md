Este artigo tem como intuito resumir alguns conceitos relacionados ao single-spa, framework usado para construção de microfrontends. Os conceitos foram divididos em tópicos explicando o que é e como fazer algumas configurações em uma aplicação single-spa.

_Não_ será criada uma aplicação de exemplo no decorrer do artigo.

_Observação: A versão do single-spa considerada neste artigo foi a 5.x_

## Tabela de conteúdos

- [O que é?](#o-que-é)
- [Como usar?](#como-usar)
- [Como funciona?](#como-funciona)
- [Como Adicionar o filho ao root?] (#adicionar-filho)
- [Passar props ao app filho a partir do root?](#props)
- [Como associar um filho a uma rota?](#rota)
- [Como definir a ordem de exibição de filhos em mesma rota?](#ordem)
- [Como funciona o processo de deploy?](#deploy)

### 1.O que é? <a name="o-que-é"></a>

Framework para criação de microfrontends, com suporte a frameworks e bibliotecas usados para construir frontends, como react, svelte etc. Com isto é possibilitado construir aplicações menores de forma isolada e combinar em uma aplicação maior/completa, além de poder usar frameworks diferentes dentro de uma mesma aplicação principal, por exemplo podemos ter um filho usando vue e outro usando react que compõem a mesma aplicação principal.

### 2.Como usar? <a name="como-usar"></a>

O framework tem instruções por linha de comando (CLI) onde é possível construir as aplicações, seja a casca ou aplicação filho. Com ela é possível selecionar o tipo de aplicação e o que irá usar, seja o framework, gerenciador de pacotes, typescript etc.

![Opcoes 1](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/bwzb89mrhwt67pk08mm3.png)
![Alt Text](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/k4bkudmxlayuu1hzh24u.png)
![Alt Text](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/ks4c3zbjxv6h0adotw25.png)

### 3.Como funciona? <a name="como-funciona"></a>

É necessário criar no mínimo duas aplicações, uma root que será usada como casca para juntar os apps e um filho, que irá compor o root. No momento de criação do root define-se um nome de organização que será usado como prefixo no nome do app filho. Não é obrigatório o uso da CLI para construir os apps, na documentação explicita o que precisa para funcionar (dentre eles métodos específicos e algumas dependências), então pode-se usar um aplicativo já existente e muda-lo para single-spa.

Mais informações: [https://single-spa.js.org/docs/migrating-existing-spas](https://single-spa.js.org/docs/migrating-existing-spas)

### 4.Como adicionar um app filho ao root? <a name="adicionar-filho"></a>

Cadastra-se um nome que será associado a esse filho, quando local irá apontar para a url de localhost e em produção aponta para onde está hospedado. Após essa associação, adiciona-se um novo aplicativo com o nome dado anteriormente como aplicação no mesmo arquivo ou usando o método registerApplication do single-spa.

```js
//index.ejs
<% if (isLocal) { %>
    <script type="systemjs-importmap">
      {
        "imports": {
          "@wps/root-config": "//localhost:9000/wps-root-config.js",
          "@wps/home": "http://localhost:8080/wps-home.js"
        }
      }
    </script>
    <% } %>
<main>
    <route default>
      <application name="@wps/home"></application>
    </route>
</main>

//componente.js
registerApplication({
  name: "@wps/home",
  app: () => System.import("@wps/home"),
  activeWhen: ["/"],
});
//ou
// especificado para rodar apenas no '/'
registerApplication({
  name: "@wps/home",
  app: () => System.import("@wps/home"),
  activeWhen: location => location.pathname === '/',
});
```

### 5.Como passar props ao app filho a partir do root? <a name="props"></a>

A função registerApplication tem parâmetros para passar dados customizados em forma de objeto quando está se registrando por meio da propriedade "customProps".

```js
registerApplication({
  name: "@wps/home",
  app: () => System.import("@wps/home"),
  activeWhen: ["/"],
  customProps: { authToken: "d83jD63UdZ6RS6f70D0" },
})
```

### 6.Como associar um filho a uma rota? <a name="rota"></a>

Essa associação é feita por meio da propriedade "activeWhen" quando o registro é feito no arquivo javascript ou pela tag "route" no arquivo ejs.

```jsx
registerApplication({
  name: "@wps/home",
  app: () => System.import("@wps/home"),
  activeWhen: ["/home"],
  customProps: { authToken: "d83jD63UdZ6RS6f70D0" },
})
```

```html
<!-- index.ejs -->
<route path="home">
  <application name="@wps/home"></application>
</route>
```

### 7.Como definir a ordem de exibição de filhos em mesma rota? <a name="ordem"></a>

Usando customProps e passando o elemento do dom a que deseja associar aquele app.

```html
<main>
  <div id="home"></div>
</main>
```

```jsx
registerApplication({
  name: "@wps/home",
  app: () => System.import("@wps/home"),
  activeWhen: ["/home"],
  customProps: { domElement: document.getElementById("home") },
})
```

### 8.Como funciona o processo de deploy? <a name="deploy"></a>

Cada microfrontend é hospedado na nuvem, usando por exemplo o s3, e pode ter uma CI para realizar o processo de integrar atualizações que serão disponibilizadas.

Nesse processo é importante criar um import map correto que referencie os nossos microfrontends já hospedados, assim como nossas dependências compartilhadas, podemos fazer isso por meio de um arquivo json e importar no root na tag do script "systemjs-importmap".

Referências:

[How to Develop and Deploy Micro-Frontends with Single-SPA](https://www.freecodecamp.org/news/developing-and-deploying-micro-frontends-with-single-spa/)

[Site Oficial do Single-SPA](https://single-spa.js.org/)
