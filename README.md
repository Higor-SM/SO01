# SO01
Dedicado ao meu estudo de SO


O processador tenta sempre executar um endereço virtual. 
Este endereço virtual contém duas partes:
um número da página e um deslocamento dentro da página. 
O número da página serve para o processador consultar a tabela de páginas para saber qual a página real (endereço do frame) que a instrução desejada está.
Então o endereço real definitivo é obtido concatenando o número da página real (endereço do frame) com o deslocamento


 Memória lógica de 16 bytes
 (16 bytes = 128 bits = 2^7 bits)
  p p d d d d d
 Páginas de 4 bytes
 (4 bytes = 32 bits = 2^5 bits)
 Memória física de 32 bytes
 (32 bytes = 256 bits = 2^8 bits)
  f f f d d d d d
 Entrada da tabela de páginas
 possui 3 bits e pode referenciar
 até 2^3 frames
 Em geral, uma entrada da
tabela de páginas possui
4 bytes
 Com 4 bytes (32 bits) pode-se
referenciar até 2^32 quadros
 Se o tamanho de um quadro é
4 Kbytes (4096 bits = 2^12 bits),
então é possível endereçar:
2^12 x 2^32 = 2^44 bits = 4Tbytes

na paginação a gente quebra o tamanho do processo em páginas, cada página contém espaço de endereçamento do processo,
então o processo é dividido em partes iguais
na páginação temos as páginas(que ficam no disco) e frames(que seriam a memória principal)
existe o page fault, que seria um evento que ocorre quando uma página existe na parte virtual, mas não é carregada na memória principal, mesmo sendo referenciada
evento que ocorre um acesso de página que não está na memória RAM foi acessada/lida/escrita
com isso, acontece a necessidade de fazer um mapeamento entre uma página virtual e uma página física e quem vai ser responsável por isso, seria a tabela de páginas
quebro páginas de tamanho iguais na mem secundária assim como na mem prim e façoi um mapeamento utilizando a tabela de páginas
