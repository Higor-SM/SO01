# Gerenciamento de Memória

Como a memória principal é gerenciada pelo sistema operacional

Existem várias formas de gerenciar, existem formas mono-programadas aonde existe um único programa e existem formas para gerenciar memória quando ela é mais complexa, quando existe vários processos que são executados de forma concorrente.

Então existem várias formas de gerenciar memória, existem várias formas de quebrar memória e dar um pedaço de memória para cada processo.

Hierarquia de Memória

O sistema de computação possui diversos tipos de memórias.

Memórias como os registradores, que essencialmente se encontram dentro do processador e consequentemente a distância percorrida para acessar uma informação é pequena, é menor doque acessar uma informação da memória principal, em função disso o acesso aos dados que se encontram no registrador ele é mais rápido.

Resumindo: O registrador é uma memória que se encontra dentro da CPU, e ele tem um acesso mais rápido que das outras memórias como a própria memória principal.

Na hierarquia existe uma coisa importante a ser falado...

Quanto maior o tamanho do armazenamento da memória, mais lento o tempo de acesso será

e quanto menor o tamanho do armazenamento da memória, mais rápido o tempo de acesso será.

Memória cache:

É uma memória intermediária que fica entre a memória principal e a própria CPU.

E a memória cache tem vários níveis.

Temos cache de nível 1, cache de nível 2 e cache de nível 3.

E o que são esses níveis? 

Esses níveis são essencialmente onde as  cache se localizam?

Hoje temos arquiteturas que se chamam de multi-core, e essas arquiteturas multi-core elas possuem vários núcleos de processador.

Existem caches que podem ser utilizadas, e não são compartilhadas por nenhum desses núcleos, elas são particulares a um determinado núcleo.

Porém existem caches que são compartilhadas entre vários núcleos distintos.

Então são caches que são comuns a todos os núcleos.

Então existem esses níveis

E o nível 1 é mais rápido por ele estar mais próximo ao processador.

Existe também a memória ram, que são memórias consideradas memórias principais.

Memória Ram por exemplo.

Que são dispositivos que vão prover uma área de trabalho maior e melhor para a aplicação do usuário.

E existem os armazenamentos que são chamados de persistentes e não voláteis.

Ou seja, você desligou o computador as informações contidas nessa memória, elas continuam armazenadas e não são excluídas.

Exemplos HDs, SSDs.

E também temos no final da hierarquia, temos os equipamentos de backups que ainda são utilizadas.

Um exemplo são os tape storage que são unidades de fitas que normalmente são utilizadas para a parte de backup, cópias de seguranças.

E como vamos gerenciar, principalmente a memória principal?

Para isso temos as Tarefas do Gerenciador de Memória (para cada tipo de memória)

A primeira tarefa que nós temos é:

Gerenciar a hierarquia de memória que seria

Gerenciar os espaços livres e ocupados

Alocar e localizar os processos e dados na memória.

E também Controlar as partes  da memória que estão em uso, e as partes que não se encontram em uso.

Ou seja, preciso fazer um mapeamento e preciso atualizar, quais são as partes da memória principal que estão em uso e as que não estão em uso.

Sendo assim , eu preciso cuidar de alocar memória aos processos, quando precisarem e liberar memória quando um processo terminar.

Então todo esse trabalho é feito por um módulo do sistema operacional que se chama gerenciador de recursos, e esse recurso do gerenciador de recursos, na realidade seria a memória.

Então, gerenciador de recursos é como se fosse um módulo de computador, um módulo do sistema operacional que cuida da administração da memória do computador

Outra tarefa que nós temos é controlar as partes que estão em uso, e as que não para

tratar do problema do swapping que é tirar o conteúdo da memória principal e colocar no disco e assim como o inverso.

Existem várias gerencias de memórias, várias estruturas e layouts de memória, que nós chamamos de monoprogramação 

Monoprogramação seria um único processo que está sendo executado num sistema de computação 

Existem 3 tipos diferentes, uma que foi usado antigamente em mainframes, computadores de grande porte.

Onde o sistema operacional é na memória principal.

outra que foi usado em sistema operacionais e dispositivos handhelds, um smartphone por exemplo que tem um sistema operacional armazenado numa memória apenas de leitura.

Ou seja, fez o boot, ligou, essa memória de leitura é acessada para que possa carregar o sistema operacional.

e também temos os primeiros computadores pessoais onde nós temos o sistema operacional na memória principal começando com o endereço 0 e os drivers de dispositivos que sãoo softwares que controlam os dispositivos que são armazenados em memórias apenas de leitura

Agora vou falar sobre a Multiprogramação

Como seria o cenário com multiprogramação?

Seria um cenário com vários computadores que vão compartilhar uma única CPU e uma única memória.

E como que nós fazemos esse gerenciamento, a divisão dessa memória entre processos diferentes?

A primeira forma é a forma particionada, nessa forma eu quebro a memória principal em várias partições diferentes, onde cada uma delas fica alocada para uma determinada fila.

Então uma partição pode ter uma fila com uma quantidade de trabalhos esperando por essa partição.

Além da divisão em si, nós temos que cuidar de fazer a parte da proteção para que o processo não venha invadir partes de outro processo

Para isso existem 2 registradores

Um para armazenar a base e o outro para armazenar o limite.

e para que serve isso?

serve para que se vc tem um programa de 40 k por exemplo e esse programa foi armazenado no endereço 20 da memória principal, eu tenho que somar esse 40 + 20 = 60 e esse 60 seria o endereço que o processo vai utilizar.

Uma vez que o processo só utiliza endereços que vão de 0 até o número máximo correspondente ao tamanho do processo.

Então esse 20 seria o BASE e o 60 seria o limite.

Justamente para que nenhum endereço possa ultrapassar o limite e nenhum endereço possa ir para o outro lado do endereço 20 que seria a base de onde ele foi carregado.

Um sistema multiprogramado são memórias divididas em várias partições diferentes e existe o cenário onde os endereços utilizados são endereços lógicos, e por utilizar endereços lógicos eu preciso fazer uma conversão para um endreço físico.

Obs: um endreço lógico é um endereço como o processo vai trabalhar.

E o endereço físico é o endereço onde o processo foi carregado na memória principal.

E quem faz a conversão de endereço lógico para endereço físico?

quem faz essa conversão é um circuito no hardware, na cpu, que se chama MMU, Memory Management Unit, ele é o responsável por fazer a manipulação dos endereços lógicos para converter esses endereços lógicos para endereços físicos.

Existem dois tipos de memória particionada

Que são as memórias de partições fixas e memória de partições variáveis.

As fixas são as que já são fixadas no ínicio do boot do sistema enquanto que as variáveis elas ocorrem alocação dinâmica.

Ou seja, as partições são criadas durante a execução dos processos.

![.](https://github.com/Higor-SM/SO01/blob/main/gerenciamento_de_memória/exemplo%20de%20partições%20variáveis.png)

Nesse exemplo nós temos um exemplo de partições variáveis.

Nós temos uma memória totalmente vazia que consiste apenas do sistema operacional, chegou o processo A ele é carregado na base da memória, chegou o processo B, o C e ele vai carregando.

E quando o processo A termina sua execução e aquela partição que ele estava ela fica liberada, e como ela fica liberada entra o processo D , ela verifica que o processo D cabe naquela partição então ela coloca o processo D e continua sua execução, o processo B finaliza sua execução e aquela parte fica liberada, e quando o processo A quiser voltar ele pode ser carregado nessa área que foi liberada pelo processo B.

Então esse é um tipo de particionamento que nós chamamos de partições variáveis.

Bom agora vou falar de Swapping, o que seria Swapping?

o Swap seria a transferência de dados ou páginas ou de partições, entre a memória principal 

e uma memória secundária, porque como nem tudo vai caber dentro da memória principal, é deixado umas partes que não estão sendo manuseadas numa área que nós chamamos de área de sawp, e essa área é utilizada para fazer essa permutação.

Ai temos o swap-in seria tirar do disco e colocar na memória principal 

e swap-out que seria tirar da memória principal e colocar em disco enquanto um outro processo possa ocupar essa área da memória.

E como que é feito o gerenciamento de espaço na memória?

Tem duas formas, a primeira forma é pelo mapa de bits.

E a segunda forma é através de lista encadeada 

Mapa de bits

Como vc pode ver na segunda imagem que eu mandei

![.](https://github.com/Higor-SM/SO01/blob/main/gerenciamento_de_memória/mapa%20de%20bits.png)

Então temos por exemplo 4KB, e esses 4KB são colocados como 1 caso ela esteja ocupada, nesse cenário da imagem o processo A ocupou 5 blocos e esses 3 blocos que se encontram livres é deixado como 0 uma vez que ele não se encontra ocupado, e assim por diante.

Ele vai seguir com esse gerenciamento desse mapa de bits de acordo com o uso da memória principal.

Lista encadeada

Nós temos uma lista contendo o processo + o endereço de início + a parte final, então na imagem temos do 0 a 5 que o 5 seria a parte final, o último endereço que se encontra ocupado.

O H denota Hole, buraco, ou seja , uma área de memória que não se encontra ocupada.

E o 3 seria os 3 slots que se encontram nesse NÓ, então se encontra esse Hole, esse buraco a partir do endereço 5 por 3 posições.

E assim por diante até ele chegar no final da memória principal.

Algoritmos de Alocação

//abre a 3 imagem//

Existem 3 formas de alocar uma área livre para um processo

A melhor escolha seria escolher a área que mais se encaixa para o processo, ela busca a lista inteira e toma a menor partição.

A pior escolha é o inverso 

![.](https://github.com/Higor-SM/SO01/blob/main/gerenciamento_de_memória/conjunto%20de%20partições%20com%20processo%2014%20kb.png)

Nesse cenário da imagem nós temos o conjunto de partições e tem um processo de 14 kb, que quer entrar na memória principal, e o melhor lugar seria o de 16 bytes e como ele tem 14 vai sobrar um espaço de 2 bytes livres

O pior seria esse de 32 kb, ai vai sobrar 18 kb.

E a primeira escolha seria a alocação onde o processo é alocado no primeiro que couber.





Fragmentação de Memória
¤ A gestão de memória mediante partições fixas
provoca o aparecimento de áreas de memória não
utilizadas.
¤ Este efeito se denomina fragmentação da memória e
pode ser de dois tipos:
- Fragmentação interna
Porção de memória de uma determinada partição que não é utilizada devido
aos requisitos reduzidos dos processos.
- Fragmentação externa
Ocorre quando existe espaço suficiente de memória livre para satisfazer uma
requisição, porém não é continuo e portanto não pode ser utilizado. 

frag int -

ocorre quando o tamanho do processo é menor que a área alocada, uma lacuna com 6kb aloca um processo de 5kb, causando desperdicio de memória.

numa mem seg ela ocorre quando um arquivo ou fragmento de arquivo não ocupa completamente o espaço da unidade de alocação destinado a ele, causando desperdício de espaço
na mem prin, o esquema de particionamento pode ser dinâmico ou fixo, no particionamento dinâmico, cada processo submetido à execução recebe o tamanho necessário para se comportar por completo na memória. Assim, a memória principal é subdividida em segmentos de tamanho variado. No particionamento fixo, a memória é subdividida em
blocos de tamanho fixo (iguais ou não) chamados em páginas, blocos ou frames.


frag ext -

ocorre quando um processo precisa de um espaço, por exemplo 5kb, porém esse espaço só existe em duas lacunas, uma de 3kb e outra de 2kb, em lugares separados. Este tipo de fragmentação começa a acontecer quando os programas forem terminando e deixando espaços cada vez menores na memória, não permitindo o ingresso de novos programas

algoritimos de alocação: 
3 maneiras para alocar uma area livre para um processo
 tenho um processo de 14kb, que quer entrar na mem principal
  ele melhor se encaixaria no local de 16kb
  o pior seria ele encaixar no 32, sobraria 18kb
  primeira escolha o processo se alocaria no primeiro espaço que coubesse, vc procura um espaço e o processo é alocado no primeiro que couber


swapping, transferencia de dados/paginas/partições entre e mem prin, e a mem seg, como tudo não cabe na mem prin, vc deixa algumas partes não essenciais numa area de
swap, sendo uma troca, swap in para colocar na mem principal e swap out pra tirar da mem prin e colocar