# NodeJS

Todos arquivos node.js, que podemos chamar de módulos, tem seu próprio escopo. E por padrão suas variáveis se limitam a ele.

**module.exports** define que algo ficará disponível fora do escopo do módulo. Podendo ser um objeto, uma classe, uma variável.

**npm install** recria a pasta node_modules, se a mesma tiver sido deletada ou o projeto recém baixado.

**npm install -g** instala um módulo direto no sistema operacional, afetando todos os projetos, sem afetar seus respectivos package.json. Recomendado utilizar sudo nessa operação para evitar problemas.

Diferenca entre builders e handlers.
