	O que é memória virtual?:
Memória virtual consiste na utilização de armazenamento externo como
extensão da memória RAM. Por exemplo, a memória principal (RAM), não
possui espaços disponíveis para armazenar determinada solicitação de um processo. A partir de algum algoritmo (por exemplo, o de retirar os dados mais
antigos armazenados) é selecionado um grupo de dados que serão salvos fora
da memória RAM (por exemplo, no disco rígido), liberando assim o espaço
necessário para armazenar a quantidade solicitada pelo processo. Esta técnica, denominada swapping (troca de processo), e implementada de forma eficiente e transparente para os processos e para os usuários. Vale a pena ressaltar que os atuais sistemas operacionais irão utilizar memória virtual paginada, retirando páginas da memória principal para um armazenamento externo, permitindo mais quadros disponíveis na memória RAM. Combinação entre a memória principal e a memória secundária (disco) para dar ao usuário a ilusão de existir uma memória principal bem maior que na realidade.

	Espaço de Endereçamento Virtual:
Um programa no ambiente de memória virtual não faz referência a endereços físicos de memória (endereços reais), mas apenas a endereços virtuais (imaginários). Durante a execução, o endereço virtual é mapeado para o endereço físico real da memória principal, ou seja, "mapeamento". O conjunto de endereços virtuais que os processos podem endereçar é chamado de "espaço de endereçamento virtual", e o conjunto de endereços reais é chamado "espaço de endereçamento real".

	Mapeamento: 
O processador, ele apenas executa instruções e referência dados residentes no espaço de endereçamento real; portanto, deve existir um mecanismo que transforme os endereços virtuais em reais. Esse mecanismo é chamado mapeamento. Nos sistemas atuais, o mapeamento é realizado por hardware juntamente com o Sistema Operacional. O dispositivo de hardware responsável por esta tradução é conhecido como Unidade de Gerenciamento de Memória (Memory Management Unit – MMU), sendo acionado sempre que se faz referência um endereço virtual. Depois de traduzido, o endereço real pode ser utilizado pelo processador para acesso à memória principal. 

	Endereçamento: 
O processador tenta sempre executar um endereço virtual. Este endereço virtual contém duas partes: um número da página e um deslocamento dentro da página. O número da página serve para o processador consultar a tabela de páginas para saber qual a página real (endereço do frame) que a instrução desejada está. Então o endereço real definitivo é obtido concatenando o número da página real (endereço do frame) com o deslocamento. O conceito de memória virtual se aproxima muito da ideia de um vetor existente nas linguagens de alto nível. Quando um programa faz referência a um elemento do vetor, não há preocupação em saber a posição de memória daquele dado. 

 
	Paginação por Demanda:
Um programa não precisa estar completamente na memória para ser executado. Muitas partes de um programa nem sempre são necessárias a todo momento. Por exemplo, editores de texto oferecem aos usuários funções que são raramente utilizadas. Se cada programa ocupar, a cada momento, somente a memória física que realmente necessita, haverá uma substancial economia de espaço na memória principal. A técnica conhecida como memória virtual permite a execução de programas que não são completamente carregados para a memória física. Tanto
paginação como segmentação podem ser estendidas no sentido de prover memória virtual. A paginação por demanda está baseada no mecanismo de paginação simples. Cada processo possui uma memória lógica, contígua. Essa memória lógica é dividida em páginas lógicas de mesmo tamanho. A memória física é dividida em páginas físicas, do mesmo tamanho das páginas lógicas. Cada página lógica é carregada em uma página física e uma tabela de páginas é construída. Na paginação por demanda, apenas as páginas efetivamente acessadas pelo processo serão carregadas para a memória física. Um bit válido/inválido na tabela de páginas é usado para indicar quais páginas lógicas foram carregadas. Dessa forma, na paginação por demanda, uma página marcada como inválida na tabela de páginas pode significar que ela realmente está fora do espaço lógico do processo ou pode significar apenas que essa página ainda não foi carregada para a memória física. A situação exata pode ser determinada através de uma consulta ao descritor do processo em questão. Quando a página lógica acessada pelo processo está marcada como válida na tabela de páginas, o endereço lógico é transformado em endereço físico, e o acesso transcorre normalmente. Quando a página lógica acessada pelo processo está marcada como inválida, a unidade de gerência de memória (MMU - Memory Management Unit) gera uma interrupção de proteção e aciona o sistema operacional. Cabe ao sistema operacional consultar o descritor do processo em questão. Caso a página acessada esteja fora do espaço de endereçamento do processo, o processo é abortado. Caso a página faça parte da memória lógica, mas esteja marcada como inválida apenas porque ainda não foi carregada para a memória, é dito que ocorreu uma interrupção por falta de página (page fault).

	Segmentação:
É a técnica de gerência de memória onde o espaço de endereçamento virtual
é dividido em blocos de tamanhos diferentes chamados segmentos. Nesta técnica um programa é dividido logicamente em sub-rotinas e estruturas de dados, que são alocados em segmentos na memória principal. Enquanto na técnica de paginação o programa é dividido em páginas de tamanho fixo, sem qualquer ligação com sua estrutura, na segmentação existe uma relação entre a lógica do programa e sua alocação na memória principal. Normalmente, a definição dos segmentos é realizada pelo compilador, a partir do código fonte do programa, e cada segmento pode representar um procedimento, uma função, vetor ou pilha. Na segmentação, os endereços especificam o número do segmento e o deslocamento dentro dele. Assim, para mapear um endereço virtual composto pelo par <segmento, deslocamento> o hardware de segmentação considera a existência de uma tabela de segmentos.
Cada entrada da tabela de segmentos possui a base e o limite de cada segmento. A base contém o endereço físico de início do segmento e o limite especifica o seu tamanho. Os segmentos podem se tornar muito grandes e, às vezes, pode ser impossível manter todos na memória ao mesmo tempo.


	Quais os benefícios oferecidos pela técnica de memória virtual?:
Como este conceito permite que um programa e seus dados ultrapassem os limites da memória principal?
Os principais benefícios da técnica de memória virtual são possibilitar que programas e dados sejam armazenados independentemente do tamanho da memória principal, permitir um número maior de processos compartilhando a memória principal e minimizar o problema da fragmentação. O que possibilita que um programa e seus dados ultrapassem os limites da memória principal é a técnica de gerência de memória virtual que combina as memórias principal e
secundária, estendendo o espaço de endereçamento dos processos.







na paginação a gente quebra o tamanho do processo em páginas, cada página contém espaço de endereçamento do processo,
então o processo é dividido em partes iguais
na páginação temos as páginas(que ficam no disco) e frames(que seriam a memória principal)
existe o page fault, que seria um evento que ocorre quando uma página existe na parte virtual, mas não é carregada na memória principal, mesmo sendo referenciada
evento que ocorre um acesso de página que não está na memória RAM foi acessada/lida/escrita
com isso, acontece a necessidade de fazer um mapeamento entre uma página virtual e uma página física e quem vai ser responsável por isso, seria a tabela de páginas
quebro páginas de tamanho iguais na mem secundária assim como na mem prim e façoi um mapeamento utilizando a tabela de páginas
