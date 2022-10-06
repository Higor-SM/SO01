# Processo

# O que é?
O processo ele é caracterizado por um programa em execução.

# Resumindo: um programa que é colocado para execução.

# E qual é a diferença entre processo e programa?
Um processo é uma instância de um programa e possui dados de entrada, dados de saída e um estado; os dados são temporários, dados processados.

# E o processo ele possuí 3 estados:
Estado Pronto para Ser executado, necessitando do processador.
Estado de execução, onde está manuseando o processador.
E estado de bloqueado/espera que é quando existe uma interrupção que vai interromper o processo e colocar ele no estado de bloqueado.

# Programa X Processo
Um programa pode ter várias instâncias em execução( em diferentes processos); é um algoritmo codificado e é uma forma como o programador vê a tarefa a ser executada.

Por outro lado o processo é único; é um código acompanhado de dados e estado e é a forma pela qual o SO vê um programa e possibilita sua execução.

# Existem dois tipos de processo:
Processo em Primeiro Plano e Processo em Segundo Plano

# Processo em Primeiro Plano:
O processo em primeiro plano tem interação direta com o usuário
Exemplo: quando vc abrir um browser, vc vai usar ele digitar endereços e etc.
Nesse cenário vc ta tendo um processo de primeiro plano.

# Processo em Segundo Plano:
Muita gente costuma chamar de background
Esse processo de segndo plano, ele nao tem interação direta com o usuário
Nós chamamos esse processo de processo genérico
Enquanto o processo de primeiro plano é específico, o processo de segundo plano é um processo genérico, que vai servir a uma quantidade grande de usuários.
#Exemplo: recepção e envio de emails
Um servidor de email não vai servir apenas para apenas um único processo, ele vai servir para N processos que pertencem a N usuários distintos.
A mesma coisa em um serviço de impressão é um serviço que vai realizar a impressão de diversos relatórios arquivos e etc.
Ele nao vai servir para um único usuário, e sim para diversos usuários distintos.

# O que cada processo possui?
1)Conjunto de instruções
2) Espaço de endereçamento (é um espaço para ele trabalhar, para que o processo possa ler e escrever - que pode ir de número 0 até número máximo)
3) Contexto de Hardware( que seria os valores que o hardware vai conter referente ao processo, exemplo: o processo tem um conjunto de instruções, ele vai dizer em que N de instruções ele se encontra, então ele precisa armazenar isso(essas informações) dentro de um registrador)
4)Contexto de software( atributos em geral, como lista de arquivos abertos, variáveis e etc.)
exemplo: int X; é um contexto que precisa ser armazenado durante a execução do programa que se encontra na memória principal.

# Espaço de endereçamento:
Ele é dividido em 3 segmentos, o primeiro segmento é o de texto que  são os códigos executáveis que estão dentro da memória principalo
segundo segmento é os dados que são as variáveis, elas são armazenadas por esse processo 
e o terceiro é a pilha de execução, que uma vez que um processo chama rotinas diferentes, ela vai chamando uma por uma, e depois ela tem que voltar para a rotina que foi chamada. Então quem vai armazenar esses ponteiros e endereços que ele vai percorrer? A pilha de execução

# Tabela de Processos 
Chamada também de BCP bloco controle de processo.
Ela contém oque?
Todas as informações de contextos, arquivos abertos, espaço de endereçamento. Assim como as informações necessárias para trazer o processo de volta para a CPU.

# Porque o processo pode ser tirado e colocado devolta na cpu?
porque eu so tenho uma cpu e diversos processos.
e eu também preciso de uma tabela que fala onde o processo parou, em que estado ele se encontra.
Então todas essas informações precisam ser armazenadas.

# Tabela de BCP

nós temos uma única tabela e dentro dessa tabela temos várias entradas, uma vez que eu nao posso colocar todas as informações dentro dessa tabela se não ela fica muito estensa
E essas entradas vão possuir as entradas dos endereços de cada tabela pertecente aos processos.

# Característica de Processo:

Um processo ele pode ser
CPU-bound e pode ser I/O-bound 
o CPU-bound é um processo que utiliza mais CPU que um dispositivo de entrada e saída
exemplo: O reconhecimento de imagem, que é o método usado pela Inteligência Artificial (IA) para “ver” conteúdos
por outro lado
o processo I/O-bound são processos que utilizam mais operações de entrada e saída doque a propria CPU. 
exemplo: copiar e mover arquivos, tipo transferencia de arquivos de um pendrive 
Um processo é considerado I/O-Bound quando passa a maior parte do tempo no estado de espera, pois realiza um elevado número de operações de E/S
O ideal seria existir um balanceamento entre processos CPU bound e IO bound


# Criação de Processos e quais são as formas de criar um processo?

a primeira forma é através da inicialização do sistema
através da execução de uma chamada de sistema para a criação de processo, realizada por algum processo em execução
requisição de usuário para criar um novo processo(duplo clique do mouse etc.)

Inicialização de um processo em batch.
Processo criando outros processos
No UNIX é utilizando a função fork()
e no Windows é utilizando o comando CreateProcess
Isso ai é um trap
um syscall
uma chamada

# Finalizando Processos 

Tem várias formas de se matar um processo
Ele pode morrer por um término normal(voluntário)
ou um término por erro
um exemplo é a divisão por zero.
ele também pode morrer com um erro fatál(involuntário)
ou também um término (involuntário) causado por algum outro processo
via chamada a esses dois comandos:

kill(UNIX)
TerminateProcess(Windows)

# Estados de Processos

Executando: realmente usando a CPU naquele momento
Bloqueado: executando alguma operação de entrada e saída por exemplo
Pronto: ele possuí tudo menos a CPU

# O processo em execução pode ir para o estado de bloqueado se ele fizer alguma chamada de sistema ou alguma requisição de entrada e saída.

# De execução para pronto também caso o processo em execução utilizou todo o tempo designado  para ele, e tiver outro processo para ser executado, ele é colocado para o estado de pronto.