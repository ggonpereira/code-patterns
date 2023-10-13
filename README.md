## Padrões no Front-End

#### 1 - Editorconfig

Aplica configurações para o editor do dev.

- **root:** define se o arquivo do .editorconfig está no top-level do seu projeto ou não (pasta root).
- **[x]:** em qual tipo de arquivo a regra vai ser aplicada. Ex.: [\*], [\*.jsx], [\*.{css, html}]

#### 2 - Eslint

- **yarn create @eslint/config**
- Diz que não está usando TS
- Pede pra usar um famoso e seleciona Airbnb

**Pra fazer funcionar com TS:**

Instala:

- @typescript-eslint/eslint-plugin @typescript-eslint/parser eslint-import-resolver-typescript

#### 3 - Prettier

Instala:

- prettier eslint-config-prettier eslint-plugin-prettier

Depois:

- Adiciona o "prettier" no .eslintrc.json dentro de "extends", "plugin" e em "rules", adicione:
  _"prettier/prettier": "error"_
- Cria um arquivo ".prettierrc" e adiciona o "{ singleQuote: true }"

#### 4 - Lint Staged

Roda algum comando nos arquivos que estão em stage no Git.

Instala:

- lint-staged

Depois:

- Cria um arquivo .lintstagedrc.json no root e adiciona:
  {
  "\*.{ts,tsx}": ["prettier --write"]
  }
- Roda `yarn lint-staged`

#### 5 - Husky

Cria gatilhos específicos em algum ciclo de vida dos nossos commits.

Roda:

- npx husky-init
- yarn

Abre o `.husky/pre-commit` e configura os scripts que quer rodar antes de executar um commit. Nesse caso, adicione `yarn lint-staged`

#### 6 - Conventional Commits

Padroniza commits no código com o que eles fazem.

Instala:

- @commitlint/{cli,config-conventional}

Depois:

- Cria um arquivo `.commitlintrc` e adiciona:
  {
  "extends": ["@commitlint/config-conventional"]
  }
- Depois roda:
  `yarn husky add .husky/commit-msg 'yarn commitlint --edit ${1}'`
