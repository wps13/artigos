A propriedade `display` define o modo como os elementos irão ser posicionados.

Valores:

1.Block

Posiciona o elemento como se ele fosse um elemento de bloco, ocupando todo o espaço possível. É o padrão de elementos como `div` e `p`.

```html
<div class="example">
  <p>Paragrafo 1</p>
  <p>Paragrafo 2</p>
  <p>Paragrafo 3</p>
  <p></p>
</div>
```

![Display block](https://thepracticaldev.s3.amazonaws.com/i/mepksu9vf5nxa43mvb5w.png)

2.Inline

Posiciona o elemento fazendo-o ocupar o menor espaço possível.

```html
<div class="example inline">
  <p>Paragrafo 1</p>
  <p>Paragrafo 2</p>
  <p>Paragrafo 3</p>
  <p></p>
</div>
```

```css
.example.inline p {
  display: inline;
}
```

![Display inline](https://thepracticaldev.s3.amazonaws.com/i/kirro9gr2j2dow7wvhey.png)

3.Inline-block

Posiciona combinando as propriedade dos `display` block e inline.

```html
<div class="example inline-block">
  <p>Paragrafo 1</p>
  <p>Paragrafo 2</p>
  <p>Paragrafo 3</p>
  <p></p>
</div>
```

```css
.example.inline-block p {
  display: inline-block;
}
```

![Display inline-block](https://thepracticaldev.s3.amazonaws.com/i/78v4h9qgoeunr8ybw7lu.png)

4.flex

Permite criar um `display` flexível, considerando por padrão que todos estão em linha, permite definir como os elementos vão ser alinhados tanto verticalmente como horizontalmente e como deve se comporta em casos que não tiver espaço suficiente, além de como deve ser o seu crescimento de acordo com o espaço disponível.

```html
<div class="example flex">
  <p>Paragrafo 1</p>
  <p>Paragrafo 2</p>
  <p>Paragrafo 3</p>
  <p></p>
</div>
```

```css
.example.flex {
  display: flex;
}
```

![Display flex](https://thepracticaldev.s3.amazonaws.com/i/qmi1i6iiz90kzohjgf85.png)

5.grid

Permite criar `display` composto por linhas e colunas, sendo possível definir o tamanho de cada espaço e o espaçamento entre eles.

```html
<div class="example grid">
  <p>Paragrafo 1</p>
  <p>Paragrafo 2</p>
  <p>Paragrafo 3</p>
  <p></p>
</div>
```

```css
.example.grid {
  display: grid;
}
```

![Display grid](https://thepracticaldev.s3.amazonaws.com/i/hlztp6qmn3eme2ul662t.png)

6.none

Constroi o elemento no `dom`, mas não o renderiza na página.

```html
<div class="example none">
  <p>Paragrafo 1</p>
  <p>Paragrafo 2</p>
  <p>Paragrafo 3</p>
  <p></p>
</div>
```

```css
.example.none {
  display: none;
}
```

![Display none](https://thepracticaldev.s3.amazonaws.com/i/f7e1ny8lw0vqals102su.png)

Os display block, inline, inline-block e none são aplicados tanto a nivel de elemento como de bloco, enquanto que o flex e grid são aplicados a nivel de bloco.

Todos os exemplos mencionados estão disponiveis no [codepen](https://codepen.io/willanepaiva/pen/ZEYqRRa).
