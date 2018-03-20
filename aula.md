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

    $ ls -F .

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



