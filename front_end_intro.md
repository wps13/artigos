A ideia aqui é explicar sucintamente o que é o front-end, quais tópicos engloba, além de comentar sobre a história da web e como isso o impactou.

## O que é front-end

É uma das áreas do desenvolvimento, responsável pela interação com o usuário. Poderíamos dizer então que é o visual de uma aplicação.

## A base

A base seriam as tecnologias que são usadas como pilar para o que vai ser desenvolvido, seja de forma isolada ou com o uso de frameworks, considerada por onde seria ideal começar a estudar ao ingressar na área. No front-end temos como base o html, o CSS e o JavaScript.

- Html

      Sigla para HyperText Markup Language ou Linguagem de marcação de hipertexto, é uma linguagem usada para estruturar o código e ser interpretada pelo browser para gerar a representação visual do que foi feito. Essa interpretação gera um interface, chamada DOM, que permite alterar os dados de forma dinâmica.

      Exemplo:

  ![<h1>Hello, world</h1>](https://dev-to-uploads.s3.amazonaws.com/i/bh8frsrim6lj4u735l7u.png)

      Resultado:

![Resultado da interpretação do código html <h1>Hello, world</h1>](https://dev-to-uploads.s3.amazonaws.com/i/zgmpzv2ykp7st1zh19vk.png)

- CSS

  Sigla para Cascading Style Sheet, é uma linguagem usada para definir estilos, nos permitindo definir cores para textos, imagens de fundos e como ela vai ser posicionada, colocar espaçamentos entre parágrafos, animações dentre várias outras coisas. Ele pode usado diretamente no componente, também pode ficar dentro da parte de estilo do html ou em arquivo separado.

  Exemplo:

![<h1 style="color:red;" >hello, world</h1>](https://dev-to-uploads.s3.amazonaws.com/i/mjxeuap47rn9xdwrvn5f.png)
Resultado:

![Resultado da interpretação do código <h1 style="color:red;" >hello, world</h1>](https://dev-to-uploads.s3.amazonaws.com/i/15nhxo6xdtkh782bxya5.png)

- Javascript

      O javascript é uma linguagem de programação usada para dar dinamismo a página, nos possibilitando fazer ainda mais coisas quando aliada ao html e css.

      Por exemplo, vamos imaginar uma página de compras, uma cliente escolhe um produto e compra 2 unidades do mesmo e precisamos calcular o valor total, como vai fazer essa conta e mostrar para ela quanto iremos gastar?

      Ai que entra o javascript, podemos pegar da página o preço por unidade e quantas unidades foram selecionadas, multiplicar os dois valores e inserir na página o resultado.

      Exemplo:

  ![Trecho de código em javascript, que mostra uma função printMessage e imprime no console 'hello, world'](https://dev-to-uploads.s3.amazonaws.com/i/m3qr5urnmcgy4xmw9g95.png "Trecho de código em javascript, que mostra uma função printMessage e imprime no console 'hello, world'")

## História da web

A inspiração surgiu na década de 60, onde tinha-se uma rede local criada pelo departamento de defesa dos Estados Unidos e usada para interesses militares, onde desejava-se manter a fluência na comunicação.
A ideia de web como temos hoje foi apresentada em 1989 por Tim Berners-Lee, que tinha como objetivo compartilhar informações entre cientistas do CERN (Centro Europeu de Pesquisa Nuclear).

- Primeiro site
  O primeiro site foi o [http://info.cern.ch/hypertext/WWW/TheProject.html](http://info.cern.ch/hypertext/WWW/TheProject.html), criado pelo Tim Berners-Lee. Era usado pelo CERN em 1991 e tinha como objetivo explicar como funcionaria a internet, nesse momento Tim observou que a internet deveria ser livres de custos de uso para se tornar popular.
  ![primeiro site da internet](https://dev-to-uploads.s3.amazonaws.com/i/5f8k7h0z4inz0ote0i9i.png "primeiro site da internet, feito em 1989")

A partir dai, a internet foi evoluindo e aumentando o número de usuários, levando então ao surgimento de blogs (The Globe), redes sociais.
Alguns das primeiras redes sociais:

- _Classmates_: Usada para usuários encontrarem seus colegas de diferentes níveis de ensino.
  ![Classmates.com print](https://dev-to-uploads.s3.amazonaws.com/i/w1e4msd9djw89chixjlv.png "Página inicial do Classmates")<br />

- _Fotolog_: usado para postar fotos com um breve texto, geralmente uma por dia, similar ao instagram. Surgiu em 2012, tendo saido do ar 4 anos depois.
  ![Fotolog homepage](https://dev-to-uploads.s3.amazonaws.com/i/ko0vtw3hk65hylhbelds.jpeg "Página inicial do fotolog")<br />

- _LinkedIn_: rede social voltada para profissionais, surgiu em 2013 e segue no ar até os dias atuais.
  ![Página inicial do linkedIn quando fundado](https://dev-to-uploads.s3.amazonaws.com/i/yrbert1w58mlgmbfk6l9.png "Página inicial do linkedIn quando fundado")<br />

- _MySpace_: rede social fundada em 2003.
  ![Primeira versão da página inicial do MySpace](https://dev-to-uploads.s3.amazonaws.com/i/psqxkaqsv2stoe0qy6nx.jpeg "Primeira versão da página inicial do MySpace")<br />

- _Orkut_: rede social que permitia a criação de perfil personalizado e participação/criação de comunidade.
  ![Orkut página de login em 2010](https://dev-to-uploads.s3.amazonaws.com/i/5ebky5qfbql71pshlhr8.png "Orkut página de login em 2010")<br />

- _Facebook_: rede social fundada em 2004.
  ![Primeira versão da tela de login do facebook](https://dev-to-uploads.s3.amazonaws.com/i/dop7i4u9qtvbkatpkoi4.png "Versão 1 - Login do Facebook")<br />

No Brasil, chegou através das universidades brasileiras trocavam informações com os Estados Unidos. De 1989 em diante que foi divulgando e expandindo por todo o país.

## Como o front-end evoluiu com a web

O front-end começou com os webdesign e webmaster, que cuidavam do design e interação com o usuário no caso do primeiro, e interação com servidor e banco de dados no caso do segundo. Surgiram então os plugins que permitiam fazer mais coisas, como lidar com multimídia (vídeos, imagens, animações mais avançadas), alguns exemplos: flash, real player, quickTime.

Posteriormente, tivemos a popularização dos celulares, que levou a surgimento de bibliotecas e frameworks focados no desenvolvimento mobile e preocupação com suporte a várias resoluções.

Outra evolução que tivemos foi com relação ao css, que ficou mais poderoso. Algumas mudanças: - Propriedades e seletores: surgiram novos que possibilitaram mais opções de display (flex e grid), novas medidas de referência (vh, vw, rem), seletores de filhos e vários outros - Pré e pós processadores: - Pré: atua antes da compilação, adiciona funcionalidades extras e altera como será construído o código - Pós: atua na manutenção dos códigos, removendo comentários, gerando versões de acordo com o navegador

## Frameworks/bibliotecas atuais

Os frameworks surgiram como uma forma de agilizar a construção de sites e mudaram a forma como o usuário interage, como as SPA (single page application), que fazem toda a aplicação em uma única página e navega-se dentro dela, não necessitando de carregamento por completo quando algo for alterado.

Para começar a usar esses frameworks é necessária uma base boa em html, CSS e JavaScript, já que são usados para construir a aplicação. É importante lembrar que por mais que a base entre os frameworks seja a mesma e possuam alguns conceitos em comum, eles diferem em como os arquivos são estruturados internamente, como lidam com as atualizações e com adição de novas funcionalidades.

Pensando assim, existem frameworks específicos para problemas específicos, por exemplo: existem alguns que seriam mais adequados para construir um blog, outros para uma aplicação financeira.

Exemplos de frameworks/libs:

- React
- Vue
- Gatsby
- Svelte
- E vários outros

## O que engloba o front-end

- Acessibilidade

  É importante que todas as pessoas com algum tipo de restrição( baixa, nenhuma visão, deficiência física entre outras) consigam acessar a página normalmente, para isso usamos descrições adequadas para elementos da página, texto alternativo para imagens dentre outras técnicas e podemos ter um indicativo de quão acessível nossa página está usando ferramentas, como o lighthouse da google, que está disponível no google chrome ao inspecionar.

- Performance

  Garantir que quem esteja usando não tenha problemas de lentidão.

- Testes

  Ajudam a verificar o comportamento esperado do o que foi feito. Exemplo: um campo de entrada mudou com o valor passado no teste corretamente.

- Responsividade

  Permite visualizar a aplicação da melhor forma dependendo do tipo de dispositivo que está (celular, tablet, pc etc)

- Segurança

  Prevenir ataques de pessoas mal-intencionadas. Exemplo: alguém tenta roubar dados de um formulário.

## Referências

[https://stackoverflow.blog/2020/02/03/is-it-time-for-a-front-end-framework/](https://stackoverflow.blog/2020/02/03/is-it-time-for-a-front-end-framework/)

[https://news.comschool.com.br/primeiro-site-do-mundo-completa-26-anos/](https://news.comschool.com.br/primeiro-site-do-mundo-completa-26-anos/)

[https://magazine.softerize.com.br/artigos/outros-artigos/revolucao-front-end-nos-ultimos-10-anos](https://magazine.softerize.com.br/artigos/outros-artigos/revolucao-front-end-nos-ultimos-10-anos)

[https://www.weblink.com.br/blog/historia-da-internet/](https://www.weblink.com.br/blog/historia-da-internet/)
