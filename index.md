# Aula 1: The Unix Shell

## Arquivos para a lição:

1. Download do arquivo data-shell.zip e mover para Desktop.
2. Descompactar arquivo na mesma pasta.
3. Abrir terminal e se direcionar para o arquivo ~/Desktop/data-shell/

## Introdução ao Shell/Terminal

Em alto nível, computadores realizam 4 procedimentos principais:

* rodam programas
* guardam dados
* se comunicam entre si
* interagem com usuário

Em geral, utilizamos **interfaces gráficas** para indicar quais tarefas desejamos que sejam feitas pela máquina (GUI - Graphical usar interface), sendo possível realizar para **tarefas simples**.  

Porém tarefas mais complexas exigem que tenhamos um maior conhecimento de comando e gramática específicas. 

Shell/terminal - linguagem simples e interface de linha de comando. 

REPL - _read-evaluate-print_ loop

### Shell

É um programa responsável por rodar programas ao invés de realizar seus próprios cálculos. O terminal Unix mais popular é o *Bash* (Stephen Bourne).

### Como funciona


    $ ls -F \ 

* Terminal espera por algum comando de entrada
* Para executar uma tarefa, digitar um comando na estrutura: **comando + flag (opções) + argumento**.
  * flags começam com - e mudam o comportamento do comando.
  * o argumento diz onde o comando deve operar
  * um comando pode conter mais de uma flag e argumentos. 
* Testar:

      $ ls-F
      
      $LS
    
## Como o terminal sabe o qual é o comando e o que cada flag significa:

Cada comando é um programa alocado em algum lugar do computador, sendo que a shell mantém uma lista de lugares onde procura pelos comandos. Como descrito, o terminal realiza o seguinte loop:

1. Lê o comando de entrada.
2. Utiliza os espaços para identificar os elementos do código (comando+flag+argumento)
3. Encontra o programa, no caso ls, executa-o passando pelos suas flags e argumentos.
4. Imprime em tela o resultado. 
5. Retorna ao estado de espera por próximo comando. 

**A gramática de um terminal permite combinar ferramentas em pipelines e lidar com um grande volume de dados automaticamente. Sequências de comandos podem ser escritas em scripts, aumentando a reprodutibilidade e  facil repetição. É essencial seu entendimento para comunicação com máquinas remotas e supercomputadores.**


## Nelle's Pipeline

Nelle Nemo, uma biologa marinha, acabou de retornar de um levantamento de seis meses no _Giro Pacífico Norte_, onde estava pegando amostras de vida marinha gelatinosa na  _Grande Porção de Lixo do Pacífico_. Ela conseguiu 1520 amostras e agora precisa de:

1. Rodar cada amostra em uma máquina de ensaio que medirá a abundância relativa de 300 proteinas diferentes. Cada saida da máquina para cada amostra é um arquivo com uma linha para cada proteina. 

2. Calcular estaísticas para cada proteina separadamente usando um programa de seu supervisor denominado **goostats**.

3. Anotar os resultados. 


Seu supervisor sugeriu **muito** para que ela termine até o fim do mês para que seu paper apareça na revista _Aquatic Goo Letters_.

Projeções:

* Leva aproximadamente 30 minutos para que a máquina de ensaio processo cada amostra. A boa notícia é que leva-se 2 minutos para definir cada uma.
* Seu laboratório possui 8 máquinas de ensaio que podem ser usadas em paralelo: esse procedimento pode ser realizado em 2 semanas. 
* Ela precisa rodar o programa goostats: ela necessita entrar com os nomes dos arquivos e clicar enter (total de 1520 ações).
* 30 segundos por amostra: 12h (assumindo que nova entrada é realizada imediatamente).

E agora????

# Navegando nos arquivos e diretórios

Para que Nelle possa cumprir seu prazo, ela utilizar do conhecimento na linguagem de linhas de comando para que sua comunicação com o computador seja mais otimizada possível. 

A parte do sistema operacional responsável pelo gerenciamento de arquivos e diretóros e denominado sistema de arquivos. Nos arquivos estão localizados os dados necessários para o funcionamento o computador, e os diretórios, ou também denominados pastas, são os locais onde se encontram esses arquivos. 

Essas pastas e arquivos podem ser manipulados utilizando um terminal. Inicialmente, desejamos descobrir em qual diretório encontra-se o terminal, pois os comandos já discutidos agem nos arquivos de um diretório previamente dado. Podemos digitar o comando pwd (print working directory)

        pwd

 
## Organização de diretórios no sistema Unix.

Para entender a saida do comando acima, discutamos como se encontra organizado o sistema de arquivos no sistema Unix. Observemos o sistema de arquivos do computador de Nelle

Imagem computador de Nelle

No topo, encontra-se o **root directory** (diretório raiz), caracterizado pelo primeiro **/**.

No diretório raiz encontram-se outros diretórios, como por exemplo:

* bin
* data
* users
* tmp

Existem portanto dois signficados para a barra /: quando aparece na frente de um arquivo ou diretório, refere-se ao diretório raiz, quando aparece dentro de um nome, significa apenas um separador (ou refere-se que o arquivo/diretório à direta, está localizado no diretório à esquerda).

Dentro da pasta \Users, observamos que existem três usuários: o de Nelle (nelle), e duas pastas referentes a sua colegas Mummy(imhotep) e Wolfram(larry). Tipicamente, ao abrir o terminal de comando, ele iniciará no diretório home. 

###ls
Novamente, utilizemos o comando de listagem para observar os arquivos e pastas presentem no atual diretório.

        ls
 
 Como observamos, esse comando imprime em tela a lista de arquivos e pastas na tela. Podemos adicionar a seguinte flag para se tornar mais compreensível.
 
        ls -F
        
-F caracteriza-se como uma flag que torna evidente que tipo de objeto estamos analisando. Porém, existe uma série de diferentes flags disponíveis para este comando. Podemos descobrí-los e obter descrições por dois comandos diferentes:

        $ ls --help
        
        $ man ls
        
Não podemos esquecer que tais comandos podem ser pesquisados na internet. [http://www.gnu.org/manual/manual.html]

Flags interessantes:

    $ ls -g
    
    $ ls -R
    
 Quando tenta-se utilzar de uma flag não existente:
 
    $ ls -j

### man

Tornará o terminal em uma página com a descrição do comando desejado e sua opções, e para alguns casos alguns exemplos. É necessário os botes up e down para navegar pela página. b leva ao início da página, e barra de espaço leva ao final da página. 

/palavra -> busca no man

Para sair, digite q.

##### Exercício 1:

O que as flags -l e -h fazem?


##### Exercício 2:

-R : descrição de subdiretórios e subsubdiretórios.
-t: lista por ordem de modificação.

Em que ordem ls -R -t funciona?

Objetos que nao apresentam barras no fim do nome são arquivos antigos. 

ALém disso, mesmo estando dentro de um determinado diretório, podemos listar o conteudo de outras pastas

    $ ls -F Desktop

Portanto, para utilizar o terminal, temos que ter em mente que os arquivos estão organizados de forma hierárquica o que nos ajuda a acompanhar os passos de nosso trabalho. Agora sabemos que o diretório _data-shell_ está localizado no Desktop. Podemos realizar duas ações:

### cd

Inicialmente, podemos olhar para o seu conteúdo, utilizando a mesma estratégia que antes:

    $ ls -F Desktop/data-shell
 
Além disso, podemos mudar nossa localização para um diretório diferente. 

cd - change directory - não é mudado o diretório, mas a ideia do terminal de qual diretório estamos. 

    $ cd Desktop
    
    $ cd data-shell
    
    $ cd data

    $ pwd
    
    $ ls -F
 
 Porém, como retornamos para os diretórios anteriores?
 
    $ cd ..
    
 O diretório .. não aparece quando damos um ls. Para observá-lo, podemos fazer:
 
    $ ls -F -a
 
-a está relacionado a mostrar todos os arquivos, inclusive os escondidos. 

Podemos observar na saida o diretório ./, que representa o diretório atual. 

./bash_profile : possue configurações da shell. Existem arquivos que iniciam com . que caracterizam-se por configurar diferentes programas presentes no computador. 

Em linguagem de programação, **ortogonalidade** significa que um conjunto relativamente pequeno de construções primitivas podem ser combinadas em um número pequeno de maneiras para construir as estruturas de controle e de dados de uma linguagem.
Isso pode ser verificado com:

    $ ls ..
    
 Esses portanto são os comandos mais básicos para navegar no sistema de arquivos de Unix.
 
 O que acontece caso executemos:
 
    $ cd
    
    $ pwd
    
 Retornemos ao arquivo data como anteriormente:
 
     $ cd Desktop/data-shell/data
  
 Até então, utilizamos de nosso localizaço atual para navegar entre os diretórios. Porém, o comando cd permite ter como argumento de localização o diretório absoluto. Desejamos ir para a pasta data:
 
  
    $ pwd
    
    $ cd /Users/nelle/Desktop/data-shell
  

 Outro argumento interessante é o ~: atual diretório home do usuário. No caso de Nelle:
 
    $ pwd ~ 
 
Outro arumento interessante é - : diretório anterior que eu estava

    $ pwd -
    
    $ cd - 
    
* .. vs -: .. leva para diretório mãe do atual e - leva ao anterior.

##### Exercício

Starting from /Users/amanda/data/, which of the following commands could Amanda use to navigate to her home directory, which is /Users/amanda?

    cd .
    cd /
    cd /home/amanda
    cd ../..
    cd ~
    cd home
    cd ~/data/..
    cd
    cd ..






 
 


