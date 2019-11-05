vs插件

- indent-rainbow 

- Turbo Console Log

- Trailing Spaces

- Prettier - Code formatter

- Path Intellisense

- Live Server

- language-stylus

- HTML CSS Support

- GitLens — Git supercharged

- ESLint

- Document This

- CSS Peek

- Color Highlight

- Code Runner

- Chinese (Simplified) Language Pack for Visual Studio Code

- Bracket Pair Colorizer

- Beautify

- Auto Rename Tag

- Auto Close Tag

- Atom One Light Theme

- Atom One Dark Theme

- vscode-icons

- Vetur

- Vue 2 Snippets

- Vue Peek

- vscode-element-helper

  react

- Typescript React code snippets

- Reactjs code snippets

- React-Native/React/Redux snippets for es6/es7

- React Redux ES6 Snippets

-    ES7 React/Redux/GraphQL/React-Native snippets



vspre

vs创建模板

 https://blog.csdn.net/weixin_38628686/article/details/80284892 

```json
{
	// Place your snippets for vue here. Each snippet is defined under a snippet name and has a prefix, body and 
	// description. The prefix is what is used to trigger the snippet and the body will be expanded and inserted. Possible variables are:
	// $1, $2 for tab stops, $0 for the final cursor position, and ${1:label}, ${2:another} for placeholders. Placeholders with the 
	// same ids are connected.
	// Example:
	"Print to console": {
		"prefix": "log",
		"body": [
			"console.log('$1')",
		],
		"description": "Log output to console"
    },
    "vue-js-template": {
        "prefix": "vueJs",
        "body": [
          "<template>",
          "  <div class=\"\">",
          "",
          "  </div>",
          "</template>",
          "",
          "<script>",
          "export default {",
          "  name: '$1',",
          "  components: {",
          "",
          "  },",
          "  props: {",
          "  // 必须写默认值和数据类型",
          "  },",
          "",
          "  data() {",
          "    return {",
          "",
          "    }",
          "  },",
          "",
          "  computed: {",
          "",
          "  },",
          "",
          "  watch: {",
          "",
          "  },",
          "",
          "  mounted() {",
          "",
          "  },",
          "",
          "  methods: {",
          "",
          "  }",
          "}",
          "</script>",
          "",
          "<style lang=\"\" scoped>",
          "",
          "</style>",
          ""
        ],
        "description": "my vue template"
      },
      "vue-ts-template": {
        "prefix": "vueTs",
        "body": [
          "<template>",
          "  <div class=\"\">",
          "",
          "  </div>",
          "</template>",
          "",
          "<script lang='ts'>",
          "import { Component, Vue, Prop, Watch } from 'vue-property-decorator'",
          "@Component({",
          "  name: '$1'",
          "})",
          "export default class extends Vue {",
          "  /**",
          "  *eg:  @Prop({default: ''}) private xxx!:type",
          "  *data",
          "  */",
          "",
          "  /**",
          "  *eg: pravite xxx:Array<number> = []",
          "  *data",
          "  */",
          "",
          "  /**",
          "  *eg: get sidebar() {return AppModule.sidebar}",
          "  *computed",
          "  */",
          "",
          "  /**",
          "  *eg: @Watch('filterText')",
          "  *private onFilterTextChange(value: string) {",
          "  *  (this.$refs.tree2 as ElTree).filter(value)",
          "  *}",
          "  *watch",
          "  */",
          "",
          "  /**",
          "  *eg: mounted() {}",
          "  *lifecycle",
          "  */",
          "",
          "  /**",
          "  *eg: private xxx() {}",
          "  *methods",
          "  */",
          "",
          "}",
          "</script>",
          "",
          "<style lang=\"\" scoped>",
          "",
          "</style>",
          ""
        ],
        "description": "my vue template"
      }
}
```

setting

```json
{
  "workbench.colorTheme": "Atom One Dark",
  "breadcrumbs.enabled": true,
  "editor.fontSize": 20,
  "workbench.editor.showTabs": true,
  "workbench.editor.enablePreview": false,
  "explorer.confirmDelete": false,
  "window.zoomLevel": 0,
  "editor.detectIndentation": false,
  "workbench.sideBar.location": "left",
  "git.autofetch": true,
  "javascript.updateImportsOnFileMove.enabled": "always",
  "code-runner.executorMap": {
    "javascript": "node",
    "php": "C:\\php\\php.exe",
    "python": "python",
    "perl": "perl",
    "ruby": "C:\\Ruby23-x64\\bin\\ruby.exe",
    "go": "go run",
    "html": "\"C:\\Program Files (x86)\\Google\\Chrome\\Application\\chrome.exe\"",
    "java": "cd $dir && javac $fileName && java $fileNameWithoutExt",
    "c": "cd $dir && gcc $fileName -o $fileNameWithoutExt && $dir$fileNameWithoutExt"
  },
  // eslint 配置
  "eslint.enable": true,
  "workbench.colorCustomizations": {},
  "eslint.autoFixOnSave": true,
  "eslint.options": {
    "extensions": [
      ".ts",
      ".js",
      ".jsx",
      ".vue"
    ]
  },
  "eslint.validate": [
    "typescript",
    "javascript",
    "javascriptreact",
    {
      "language": "vue",
      "autoFix": true
    }
  ],
  // prettire配置
  // "editor.formatOnSave": true,
  //Enable per-language
  "[typescript]": {
      "editor.formatOnSave": true,
      "editor.defaultFormatter": "vscode.typescript-language-features"
  },
  // "[javascript]": {
  //   "editor.formatOnSave": true,
  //   "editor.defaultFormatter": "esbenp.prettier-vscode"
  // },
  "prettier.eslintIntegration": true,
  "prettier.singleQuote": true,
  "prettier.trailingComma": "none",
  "prettier.semi": false,
  "prettier.tabWidth": 2,
  "editor.quickSuggestions": {
    "strings": true
  },
  //由于prettier不能格式化vue文件template  所以使用js-beautify-html格式化
  "vetur.format.defaultFormatter.html": "js-beautify-html",
  "vetur.format.defaultFormatterOptions": {
    "js-beautify-html": {
      "wrap_attributes": "force-aligned" //属性强制折行对齐
    }
},
"editor.tabSize": 2,
"workbench.iconTheme": "vscode-icons",
}
```

