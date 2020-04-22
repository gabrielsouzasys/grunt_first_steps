## Instalação
Será necessário possuir o Node.js e o NPM instalados em sua máquina

Depois disso você precisa instalar o cliente por linha de comando do Grunt:

###### Importante: caso possua uma versão antiga do Grunt, recomenda-se que seja removida com o comando npm uninstall -g grunt antes de realizar uma nova instalação. É possível verificar se o Grunt está instalado na sua máquina com o comando grunt -v.


`npm install -g grunt-cli`


Como você percebe, foi instalado o grunt-cli não o grunt. O grunt-cli é uma interface que disponibiliza os comandos Grunt pelo terminal a partir de qualquer local.

Esse -g avisa para o NPM que a instalação deve ser Global, isso significa que ele não será instalado somente para um projeto, mas sim em sua máquina, estando disponível sempre que precisar rodando o comando grunt. Esse comando irá configurar o seu $PATH e nós podemos prosseguir.

Agora é necessário configurar as tarefas que o Grunt irá executar.


________________________________________________________________________________________________
PROJETOS EXISTENTES
Para projetos com o Grunt já configurado, basta você navegar até a pasta onde está localizado o arquivo package.json e executar o comando npm install. Com isso, todas as suas dependências serão instaladas e você estará apto a rodar suas tarefas no Grunt.
________________________________________________________________________________________________

INSTALAÇÃO DAS DEPENDÊNCIAS DO GRUNT
Para instalar as dependências, é preciso executar o comando npm install <nome da dependencia> --save-dev. Entretanto, a primeira dependência a ser instalada deve ser o Grunt. Executando o comando npm install grunt --save-dev você estará instalando (de fato) o Grunt localmente no seu projeto.

Você pode estar se perguntando qual a necessidade em se fazer isso. Simples. Toda vez que o seu projeto for manuseado por outro desenvolvedor, ou até mesmo por uma equipe diferente, a versão do grunt estará intacta. Isto vai evitar possíveis conflitos de versões do Grunt no seu projeto.

___________________________________________________________________________________________________

### Configurando as tarefas
###### Package.json
Primeiro, no diretório do seu projeto, será necessário possuir o package.json, aquele arquivinho de dependências do NPM, pois todo plugin do Grunt que você instalar precisa ser referenciado como dependência nesse arquivo. Isso vai diminuir muito seu trampo depois, pois só com um comando npm install será tudo instalado, ao invés de ficar rodando tudo de novo.

pode executar o npm init na pasta do projeto para criar o package.json 

###### Feito isso você pode instalar os plugins no seu projeto (Instalação Local).

* (Um exemplo de instalação de Plugin (Não precisa fazer isso agora): npm install grunt-contrib-cssmin --save-dev)


Com isso, o plugin seria instalado na pasta do seu projeto e ficaria salvo como dependência no package.json. Isso por que você passou o parâmetro –save-dev.

Para que o Grunt funcione, você precisa telo instalado no projeto (Você tem uma instalação Global do cliente via terminal com o -g e agora vai instalar o Grunt localmente), para isso execute o comando:

`npm install grunt --save-dev`



## Gruntfile.js
Depois disso, temos tudo pronto para começar a baixar os plugins e configurar o Grunt para rodar eles. 
A configuração das tarefas do Grunt ficam no arquivo Gruntfile.js e você pode criar ele.

`grunt init`

* Um exemplo de configuração básica do arquivo é o seguinte:

`module.exports = function(grunt) {
// Configuração do Projeto
grunt.initConfig({
    pkg: grunt.file.readJSON('package.json'),
    uglify: {
      options: {
        banner: '/*! &lt;%= pkg.name %&gt; &lt;%= grunt.template.today("yyyy-mm-dd") %&gt; */\n'
      },
    build: {
      src: 'src/&lt;%= pkg.name %&gt;.js',
      dest: 'build/&lt;%= pkg.name %&gt;.min.js'
    }
 }
});

// Carrega o Plugin para executar a tarefa "uglify"
grunt.loadNpmTasks('grunt-contrib-uglify');

// Tarefas
grunt.registerTask('default', ['uglify']);

};`



A linha grunt.initConfig(config) especifica onde iniciam as configurações das tarefas.

Todo plugin instalado, deve ser carregado, como mostrado na expressão: grunt.LoadNpmTask(‘grunt-contrib-uglify’);.

As tarefas que serão executadas com o comando grunt (sem passar nenhum parâmetro) no terminal são registradas como na expessão grunt.registerTask(‘default’, [‘uglify’]); onde foi configurado a tarefa ‘default’ (que é executada automaticamente com o comando grunt) que, nesse caso, chamou uma tarefa uglify, mas da para chamar várias ao mesmo tempo.

Se você quisesse executar somente a tarefa uglify, poderia rodar o comando grunt com o parâmtro uglify:


`grunt uglify`


Se existisse outra tarefa com o nome cssmin, você executaria grunt cssmin ou configuraria a tarefa ‘default’ para chamar também a cssmin:

`grunt.registerTask('default', ['uglify', 'cssmin']);`


### Dica: O que é instalação Local e Global

Global é a instalação do Plugin em seu sistema operacional. Assim ele fica disponível em qualquer projeto bastando executar o comando respectivo, como exemplo do Bower. Local é a instalação do plugin em seu projeto - Na pasta do seu projeto. Todo projeto criado deverá possuir os plugins instalados localmente para funcionar.

Ai vem a duvida: Mas pra que ficar instalando localmente e sobrecarregando o HD do meu PC se eu posso instalar uma vez só Globalmente e usar em todos os projetos?

A resposta é: Imagine que você usa a versão 1.0 de determinado plugin em todos os seus projetos. Meses se passam e você agora utiliza a versão 2.0 onde muita coisa mudou e, de repente, você precisa mexer em um projeto antigo. A tarefa configurada não vai funcionar, você vai ter de configurar de novo.

Você pode pensar: Tá, mas é só copiar o Gruntfile.js de um projeto novo para um antigo. Sim! Isso se for para um projeto, para um plugin, imagina esse cenário acontecendo para diversos projetos e vários plugins.

Portanto é melhor instalar os plugins localmente e com o comando –save-dev para salvar como dependência e deixar mais fácil a próxima instalação. ;)





Referencias:
[First Step's Grunt COMPLETO](https://nandovieira.com.br/usando-gruntjs)

[Você devia estar usando](https://tableless.com.br/grunt-voce-deveria-estar-usando/)
[Grunt na prática - Tarefas de e-mails e reutilizando pacotes Dependencies](https://webdesign.tutsplus.com/pt/tutorials/using-grunt-to-make-your-email-design-workflow-fun-again--cms-22223)
[Boilerplate](https://github.com/vagnervjs/grunt-boilerplate)
[Automação de build de front-end com Grunt.js](https://blog.caelum.com.br/automacao-de-build-de-front-end-com-grunt-js/)
[Projeto Pastel - Boilerplate GRUNT Gruntfile.js & Package.Json](https://github.com/woliveiras/pastel)
[Grunt Converter MD para PDF](https://github.com/alanshaw/grunt-markdown-pdf)
[Grunt]()
[Grunt]()
[Grunt]()





IMG
![Markdown Da2k](https://blog.da2k.com.br/uploads/2015/02/markdown.png)

