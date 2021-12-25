# FAQs do mini projeto de FSO
#

## Para que serve a função `inode_location` no `ffs_inode.c`
Esta função recebe o numero do inode e vai calcular em que bloco do disco se encontra. 
Se tens 2 blocos para inodes, terás 96 inodes no total. 32 grandes e 64 pequenos. 
Se mandas o inode 0, significa que está no bloco 2 (inodes grandes vão do 0 ao 31 e ficam no bloco 2) e o offset é 0. 
Se mandas o 32, significa que já está no bloco 3 (inodes pequenos vão do 32 ao 95 e ficam no bloco 3), com offset 0.
Os blocos variam consoante o numero de blocos que estão destinados para inodes

## 2
fsdfsfsdfs
