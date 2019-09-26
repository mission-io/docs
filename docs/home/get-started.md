## Prerequisites

1. Install the [Nodejs](#node-js)

2. Install the [git](#git)

3. install the [VSCode](#vs-code)

4. Install [mysql](https://dev.mysql.com/downloads/) or [posgresql](https://www.postgresql.org/download/) database

5. Install the following npm modules globally
  
    1.  typescript
    2.  tslint
    3.  rimraf 
    
    ```
    npm i typescript tslint rimraf mission.cli -g
    ```

### Verify the installatioin
```shell
tsc -v  #shows typescript version number
tslint -v #shows typescript lint version number
node -v #shows nodejs version number
git version #shows git version number
mio version # shows mission command line interface version nubmer
```
### Software stack

1. Sequelize
2. Typescript
3. Express js
4. Redis
5. MySQL 
6. MongoDb *
7. puppeteer *
8. bull *

!!! note "*"
    These modules not required for all projects.

[Architecture Overview](architecture.md)
## Recomended Tools

### [VS Code](https://code.visualstudio.com/download)
Visual Studio Code is a lightweight but powerful source code editor which runs on your desktop and is available for Windows, macOS and Linux. It comes with built-in support for JavaScript, TypeScript and Node.js and has a rich ecosystem of extensions for other languages (such as C++, C#, Java, Python, PHP, Go) and runtimes (such as .NET and Unity)

#### Recomended VS Code Plugins

1. [DotENV](https://marketplace.visualstudio.com/items?itemName=mikestead.dotenv)

2. [Docker](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vscode-docker)

3. [Open API](https://marketplace.visualstudio.com/items?itemName=42Crunch.vscode-openapi)

4. [TS Lint](https://marketplace.visualstudio.com/items?itemName=eg2.tslint)

5. [Typescript Import Sorter](https://marketplace.visualstudio.com/items?itemName=mike-co.import-sorter)

6. [MySQL](https://marketplace.visualstudio.com/items?itemName=formulahendry.vscode-mysql)

#### Optional VS Code Plugins

1. [Handlebars](https://marketplace.visualstudio.com/items?itemName=andrejunges.Handlebars)

2. [Fix JSON](https://marketplace.visualstudio.com/items?itemName=oliversturm.fix-json)
### Node Js

Node.js® is a JavaScript runtime built on Chrome's V8 JavaScript engine.

[Node Js Download](https://nodejs.org/en/download/current/)

### Git

Git is a free and open source distributed version control system designed to handle everything from small to very large projects with speed and efficiency.

[Git Download](https://git-scm.com/downloads)

### MySql database
[MySql Download](https://dev.mysql.com/downloads/) 
 
### PosgreSql database
[PosgreSql Download](https://www.postgresql.org/download/) 

### npm modules
Essential JavaScript development tools that help you go to market faster and build powerful applications using modern open source code.

```shell
npm install typescript tslint rimraf mission.cli -g
```
[View npm modules](https://www.npmjs.com/)

## Optional Tools
### Docker
The fastest, easiest, and most secure way to deliver containerized applications from development to production.

[Docker Download](https://www.docker.com/products/docker-desktop)