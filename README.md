# FAQs do mini projeto de FSO



## 1. Não sei o que é para fazer, podes ajudar-me?
Relê o enunciado e discute primeiro com o teu colega de grupo. <br>
Podes também perguntar no grupo do curso.<br>
Os professores têm também hórarios de dúvidas e podes contactá-los por email.<br>
Horários de dúvidas do professor Paulo Lopes ([Link Zoom]https://videoconf-colibri.zoom.us/j/86853779631?pwd=dzIyelREWmtGZ3o2WWlvVzNCVjFrZz09):<br>
- 2ª-feira, 27/12 às 15h<br>
- 3ª-feira, 28/12 às 17h<br>
- 4ª-feira, 29/12 às 17h (e não às 15h)<br>
- 5ª-feira, 30/12 às 15h (horário habitual)<br>
Se mesmo assim não conseguires, então diz-me, que, dentro dos possiveis, tentarei ajudar.

## 2. Falta um dia para a entrega, dá para fazer tudo?
Não devias de ter deixado para a última.<br>
É possível, mas vai ser bastante dificil.

## 3. O meu programa devia de estar a funcionar, mas dá erro não sei porquê.
Se estás numa versão 32 bits do linux, troca para uma de 64. Parece que não é possivel compilar em 32 bits.<br>
Se usas WSL, muda as linhas da função `makeargv` de `argv[ntokens] = strtok(s, " \t\n");` para `argv[ntokens] = strtok(s, " \r\t\n");`<br>
Experimenta de novo.<br>
Se ainda não funcionar, é porque tens algum bug no teu código.

## 4. Como é que me registo no Mooshak?
O professor não disse nada, mas deve ser tal como em AED. n1_n2, sendo n1 < n2.

## 5. Para que serve a função `inode_location` no `ffs_inode.c`?
Esta função recebe o numero do inode e vai calcular em que bloco do disco se encontra.<br>
Se tens 2 blocos para inodes, terás 96 inodes no total. 32 grandes e 64 pequenos.<br>
Se mandas o inode 0, significa que está no bloco 2 (inodes grandes vão do 0 ao 31 e ficam no bloco 2) e o offset é 0.<br>
Se mandas o 32, significa que já está no bloco 3 (inodes pequenos vão do 32 ao 95 e ficam no bloco 3), com offset 0.<br>
Exemplo:
Se recebes o inode 15, sabes que é grande. <br>
Para calcular o bloco divides 15/ninodes_grandes_por_bloco que vai dar 0,qqlcoisa, truncado dá 0. <br>
Para calcular o offset dentro do bloco, calculas o resto da divisão de 15%ninodes_grandes_por_bloco.<br>
De forma parecida fazes para os pequenos, com alguma lógica adicional que deixo para tu pensares.<br>
Os blocos variam consoante o numero de blocos que estão destinados para inodes.

## 6. Para que serve a função `bytemap_getfree` no `ffs_bytemap.c`?
Nesse metodo tens que criar um algoritmo que vai ver se um disco tem `howMany` entradas contiguas livres e devolves o indice da primeira posição.<br>
Uma entrada está vazia se o bitmap estiver a 0.<br>
Se não forem encontradas `howMany` entradas contiguas livres, é retornado `-ENOSPC`, que é um código de erro que está definido `bfs_errno.h`.

## 7. Qual a ordem que recomendas para fazer o trabalho?
A ordem que o professor recomenda.

## 8. O que é suposto meter na linha `static struct dir ` do `bfs_dir.c`?
Podes ter um array de `dir` com duas posições, uma para guardares a root e outra para guardar uma diretoria que não a root.<br>
Depois cria também uma variável que aponta (ex: `*cwd`) para a `dir` que estás a usar. Ou a root ou a other.

## 9. Estão a aparecer valores estranhos quando faço print dos bmaps.
Muito provavelemente estás a ler e/ou escrever no bloco errado do disco.

## 10. É necessário usar o cwd e como o inicializo, no dir.c?
Sim, é necessário tendo em conta o código já feito pelos professores. Inicializas como um pointer do tipo dir, ou seja, static struct dir *cwd.
