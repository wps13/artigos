This article is a compilation of setup that I made in VSCode to look better and have the functionalities that I consider the minimum necessary to development.

The final result:

![Screenshot for visual studio code on personal computer](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/i08gybkbk0n6q95zfemd.png)

_Table of Contents_

1. [ Improving visual hiding lateral bar, title bar and minimap](#visual)
   1.1. [Adding keyboard shortcuts](#keyboard-shortcuts)
   1.2. [Hiding the bars in settings](#hiding-bars)

2. [Adding JetBrains Mono with ligatures](#font)
   2.1. [Installing the font on your computer](#install-font)
   2.2. [Using it on VSCode](#using-font)

3. [Additional Settings](#extra)
4. [Adding extensions](#extensions)

4.1 [General](#general)
4.2 [React Development](#react)
4.3 [Themes](#themes)
4.4 [Flutter](#flutter)

PS: If you are using macbook, replace ctrl with cmd.

## 1. Improving visual hiding lateral bar, title bar and minimap <a name="visual"></a>

### 1.1. Adding keyboard shortcuts <a name="keyboard-shorcuts"></a>

Open the command search using the shortcut `ctrl + shift + p` and type 'keyboard shortcuts', then select 'Preferences: Open Keyboard Shortcuts (JSON)' as showed in the image bellow.

![Screenshot for visual studio code command option, showing an input field and the option 'Preferences: Open Keyboard Shortcuts (JSON)' highlighted](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/nrfj608ojmcuvr45ihi1.png)

Then add the following code in the opened file:

```json
// Place your key bindings in this file to override the defaults
[
  /**
   * Activity Bar
   **/
  {
    "key": "ctrl+k ctrl+e",
    "command": "workbench.view.explorer"
  },
  {
    "key": "ctrl+k ctrl+g",
    "command": "workbench.view.scm"
  },
  {
    "key": "ctrl+k ctrl+d",
    "command": "workbench.view.debug"
  },
  {
    "key": "ctrl+k ctrl+x",
    "command": "workbench.extensions.action.showInstalledExtensions"
  }
]
```

### 1.2 Hiding the bars in settings <a name="hiding-bars"></a>

Open the settings similar to how we did previously, using the shortcut `ctrl + shift + p` and searching for 'Preferences: Open Settings (JSON).

![Screenshot for visual studio code command option, showing an input field and the option 'Preferences: Open Settings (JSON)' highlighted](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/ev00gskk1zichyjzg1go.png)

In the JSON file, add the following options:

```json
  "window.titleBarStyle": "custom",
  "workbench.activityBar.visible": false,
  "editor.minimap.enabled": false,
```

## 2. Adding JetBrains Mono with ligatures <a name="font"></a>

### 2.1 Installing the font on your computer <a name="install-font"></a>

Head to https://www.jetbrains.com/lp/mono/, download the font and install it according to your operating system.

### 2.2. Using it on VSCode <a name="using-font"></a>

Open the settings.json (explained in step 1.2) and add the following content inside the file:

```json
    "editor.fontLigatures": true,
    "editor.fontFamily": "'JetBrains Mono','Droid Sans Mono', 'monospace', monospace, 'Droid Sans Fallback'",
```

## 3. Additional settings <a name="extra"></a>

The following settings are for improving git usage, editor update import, enable bracket pair ([Check VSCode update for more info](https://code.visualstudio.com/updates/v1_60#_high-performance-bracket-pair-colorization)), format on save, define default formatter. "Compact folders" is for when the folder only have one nested folder, when disabled, won't show inline.

Compact Folders disabled:
![Compact folder disabled on vscode](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/ly75ji2adr05ehv90shk.png)

Compact Folders enabled:
![Compact folder enabled on vscode](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/rdkjp5sz7famad4k2iwt.png)

```json
    "editor.suggestSelection": "first",
    "vsintellicode.modify.editor.suggestSelection": "automaticallyOverrodeDefaultValue",
    "git.enableSmartCommit": true,
    "git.confirmSync": false,
    "git.autofetch": true,
    "explorer.compactFolders": false,
    "editor.wordWrap": "on",
    "extensions.ignoreRecommendations": true,
    "javascript.updateImportsOnFileMove.enabled": "always",
    "typescript.updateImportsOnFileMove.enabled": "always",
    "diffEditor.ignoreTrimWhitespace": false,
    "editor.bracketPairColorization.enabled": true,
    "editor.codeActionsOnSave": {
        "source.fixAll.eslint": true
      },
    "eslint.validate": [
      "javascript"
    ],
    "eslint.format.enable": true,
    "[typescriptreact]": {
      "editor.defaultFormatter": "dbaeumer.vscode-eslint"
    },
    "[javascript]": {
      "editor.defaultFormatter": "dbaeumer.vscode-eslint"
    }
```

## 4. Adding extensions <a name="extensions"></a>

These are the main extensions that I'm currently using:

### 4.1 General: <a name="general"></a>

- [Color Highlight](https://marketplace.visualstudio.com/items?itemName=naumovs.color-highlight)

![Screenshot for Color Highlight on Marketplace vscode](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/1uqjk2dv22x9p7vyvpih.png)

- [EditorConfig for VSCode](https://marketplace.visualstudio.com/items?itemName=EditorConfig.EditorConfig)

![Screenshot for EditorConfig on Marketplace vscode](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/lfz34f69c7e3y9hz7z79.png)

- [ESLint](https://marketplace.visualstudio.com/items?itemName=dbaeumer.vscode-eslint)

![Screenshot for Eslint on Marketplace vscode](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/bnv6r09lzr3zp1duy7le.png)

- [Highlight Matching Tag](https://marketplace.visualstudio.com/items?itemName=vincaslt.highlight-matching-tag)

![Screenshot for Highlight Matching Tag on Marketplace vscode](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/7fn4wlxejbtfo8osnaxk.png)

- [Image Preview](https://marketplace.visualstudio.com/items?itemName=kisstkondoros.vscode-gutter-preview)

![Screenshot for Image Preview on Marketplace vscode](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/rnwfrups605ju77tj2r7.png)

- [Import Cost](https://marketplace.visualstudio.com/items?itemName=wix.vscode-import-cost)

![Screenshot for Imoport Cost on Marketplace vscode](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/czby6ixmbo0wa1nmn3ho.png)

- [Gitlens](https://marketplace.visualstudio.com/items?itemName=eamodio.gitlens)

![Screenshot for GitLens on Marketplace vscode](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/mq5rv59qz1rhenyzyu44.png)

- [vscode-styled-components](https://marketplace.visualstudio.com/items?itemName=jpoissonnier.vscode-styled-components)

![Screenshot for vscode-styled-components on Mricrosoft store ](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/8xhcf4fhmqmofsl5xnfy.png)

### 4.2 React Development: <a name="react"></a>

- [ES7 React/Redux/GraphQL/React-Native snippets](https://marketplace.visualstudio.com/items?itemName=dsznajder.es7-react-js-snippets)
  ![Screenshot for Snippets on Marketplace vscode](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/q1m83hubfcz5y0b6h6fz.png)

### 4.3 Themes: <a name="themes"></a>

- [Panda Theme](https://marketplace.visualstudio.com/items?itemName=tinkertrain.theme-panda)

![Screenshot for Panda Theme on Marketplace vscode](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/oil1byuutjz09y7modmh.png)

- [Lukin Theme](https://marketplace.visualstudio.com/items?itemName=lukinco.lukin-vscode-theme)

![Screenshot for Lukin Theme on Marketplace vscode](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/wj2mgk3qobjak3xktxir.png)

- [Eva Theme](https://marketplace.visualstudio.com/items?itemName=fisheva.eva-theme)

![Screenshot for Eva Theme on Marketplace vscode](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/h58nq9fuphy26gfhfyx1.png)

- [Material Icon Theme](https://marketplace.visualstudio.com/items?itemName=PKief.material-icon-theme)

![Screenshot for Material Icon Theme on Marketplace vscode](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/3rqbp9yqc9igcvd9m0yv.png)

### 4.4 Flutter: <a name="flutter"></a>

- [Awesome Flutter Snippets](https://marketplace.visualstudio.com/items?itemName=Nash.awesome-flutter-snippets)

![Screenshot for Awesome Flutter Snippets on Marketplace vscode](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/uvfptom9l0fja6ecllrw.png)

- [Dart](https://marketplace.visualstudio.com/items?itemName=Dart-Code.dart-code)

![Screenshot for Dart on Marketplace vscode](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/jdzogumg96591rssx8bb.png)
