# FAQs do mini projeto de FSO



## Para que serve a função `inode_location` no `ffs_inode.c`
Esta função recebe o numero do inode e vai calcular em que bloco do disco se encontra. 
Se tens 2 blocos para inodes, terás 96 inodes no total. 32 grandes e 64 pequenos. 
Se mandas o inode 0, significa que está no bloco 2 (inodes grandes vão do 0 ao 31 e ficam no bloco 2) e o offset é 0. 
Se mandas o 32, significa que já está no bloco 3 (inodes pequenos vão do 32 ao 95 e ficam no bloco 3), com offset 0.
Os blocos variam consoante o numero de blocos que estão destinados para inodes


## Para que serve a função `bytemap_getfree` no `ffs_bytemap.c`
Nesse metodo tens que criar um algoritmo que vai ver se um disco tem howMany entradas contiguas livres e devolves o indice da primeira posição
Uma entrada está vazia se o bitmap estiver a 0.

## O meu programa devia de estar a funcionar, mas dá erro não sei porquê.
Se usas WSL, muda as linhas da função `makeargv` de `argv[ntokens] = strtok(s, " \t\n");` para `argv[ntokens] = strtok(s, " \r\t\n");`
Experimenta de novo. Senão funcionar, é porque tens algum bug no teu código.

## Qual a ordem que recomendas para fazer o trabalho?
A ordem que o professor recomenda
