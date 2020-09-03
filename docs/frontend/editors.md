# Editors

When it comes to working with frontend there are a couple of choices, though I
personally recommend to use either VSCode or WebStorm.

## Keybinding notes

I'll write the keys as Windows/Linux specific commands (i.e. using ++ctrl++
instead of ++cmd++), so for anyone using macOS you should in most cases be able
to simply use that instead of what I'm writing. Fair warning though, JetBrains
products have very different keybindings between macOS and Windows/Linux so it
is less applicable there.

## VSCode

VSCode is a fairly simple and barebones editor by default, so it's recommended
that you install a couple of extensions. To install press ++ctrl+shift+p++,
write `Install extension` and then the name of the extension.

| Extension   | Name                                     | What                                                  |
|-------------|------------------------------------------|-------------------------------------------------------|
| ESLint      | `dbaeumer.vscode-eslint`                 | Shows linting errors and enables autofixing in VSCode |
| Prettier    | `esbenp.prettier-vscode`                 | Show styling errors and autoformatting of code        |
| JS/TS       | `mgmcdermott.vscode-language-babel`      | Syntax highlighting for JS, TS, GraphQL and TSX       |
| Docker      | `ms-azuretools.vscode-docker`            | Enables Docker support                                |
| Dotenv      | `mikestead.dotenv`                       | Automatic handling of `.env` files                    |
| SASS        | `syler.sass-indented`                    | SASS and SCSS support                                 |
| IntelliCode | `VisualStudioExptTeam.vscodeintellicode` | Experimental plugin for better autocompletion         |

You should also add a few recommended settings to your `settings.json` file. Run
++ctrl+comma++ to open the settings and paste in the following:

```json
{
  "editor.formatOnSave": true,
  "editor.formatOnPaste": true,
  "editor.codeActionsOnSave": {
    "source.fixAll": true
  },
  "typescript.updateImportsOnFileMove.enabled": "always",
  "editor.defaultFormatter": "esbenp.prettier-vscode",
  "[javascript]": {
    "editor.defaultFormatter": "esbenp.prettier-vscode"
  },
  "[typescript]": {
    "editor.defaultFormatter": "esbenp.prettier-vscode"
  }
}
```

You should also take a quick look at the
[documentation](https://code.visualstudio.com/docs) for VSCode, especially the
`Get Started` section.

## WebStorm

Compared to VSCode WebStorm is a full-fledged IDE with nearly everything
supported out of the box. To start, open the settings by pressing
++ctrl+alt+s++ and do the following steps:

<figure>
  <img src="/images/webstorm-graphql.png" />
  <figcaption>Install the GraphQL plugin.</figcaption>
</figure>

<figure>
  <img src="/images/webstorm-eslint.png" />
  <figcaption>Enable and configure ESLint.</figcaption>
</figure>

<figure>
  <img src="/images/webstorm-prettier.png" />
  <figcaption>Enable and configure Prettier. <strong>NOTE:</strong> We updated the "Run for files" field too.</figcaption>
</figure>

If you want to learn to use WebStorm, and JetBrain's products in general, I
recommend installing the `Features Trainer` plugin and following that to get a
feel for how to work in an IDE.

<figure>
  <img src="/images/webstorm-trainer.png" />
  <figcaption>Install the Features Trainer.</figcaption>
</figure>
