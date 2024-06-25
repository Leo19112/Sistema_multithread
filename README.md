# Projeto prático da disciplina de Sistemas Operacionais

## Descrição do Projeto
O projeto prático da disciplina TT304_A - Sistemas Operacionais, ministrado pelo Prof. Dr André Leon Sampaio Gradvohl, tem como objetivo principal consolidar conhecimentos sobre programação com múltiplos *threads*. O projeto propõe o desenvolvimento de um programa que realiza uma sequência de operações matemáticas com matrizes de números inteiros, lidos a partir de arquivos de entrada, e posteriormente, a gravação dos resultados em arquivos de saída.

Especificamente, o programa deve ser desenvolvido na linguagem C e no ambiente Linux.

O programa deverá realizar as seguintes operações:

   1. Receber as matrizes de entrada:
        - O usuário deve fornecer três matrizes de entrada Anxn, Bnxn e Cnxn.     
   2. Receber a leitura da matriz Anxn e Bnxn:
        - O programa deve realizar a leitura das matrizes Anxn e Bnxn, cada um em seus respectivos arquivos.
   3. Calcular a matriz Dnxn:
      - O programa deve calcular a matriz Dnxn, tal que Dnxn = (Anxn + Bnxn). O resultado deve ser gravado em um arquivo, cujo nome será definido pelo usuário via linha de comando ao instanciar o programa.
   4. Realizar a leitura da matriz Cnxn:
        - O programa deve realizar a leitura da matriz Cnxn em seu respectivo arquivo.  
   5. Calcular a matriz Enxn:
        - O programa deve calcular a matriz Enxn, tal que Enxn= (Cnxn * Dnxn). O resultado deve ser gravado em um arquivo, cujo nome será definido pelo usuário via linha de comando ao instanciar o programa. 
   6. Reduzir a matriz Enxn:
        - O programa deve reduzir a matriz Enxn por soma, ou seja, todos os seus componentes devem ser somados, resultando em um único valor final.

Para manter a clareza e a organização do projeto, foram adotadas boas práticas de programação, como dividir o código-fonte em arquivos de implementação e cabeçalho. Dessa maneira, a manutenção e a compreensão do projeto são facilitadas. Todas as matrizes foram alocadas dinamicamente em uma única etapa, utilizando o comando **‘malloc’**. Além disso, foi criado um Makefile para a compilação do projeto, evitando possíveis erros durante o processo. 

O programa foi projetado para executar essas operações simultaneamente utilizado múltiplos *threads* (de leitura, processamento e escrita) para otimizar o processamento. As entradas são fornecidas via linha de comando e os resultados das operações, juntamente com os tempos de processamento, devem ser exibidas ao final da execução do programa.

Inicialmente, utilizei a primitiva **‘clock’** para medir os tempos de execução, mas observei que os tempos aumentavam conforme o incremento da quantidade de *threads*. Para resolver isso, utilizei a primitiva **‘clock_gettime’**, o que permitiu visualizar a redução dos tempos de execução conforme o aumento do número de *threads*.

## Instruções para compilar o programa
1. **Utilizar o comando ‘make clean’:**
   - Antes de compilar, utilize o comando **‘make clean’** para remover todos os arquivos de compilação anteriores. Isso garante que a nova compilação será feita do zero, evitando possíveis conflitos.
2. **Utilizar o comando 'make':**
   - Utilizar o comando **‘make’** para gerenciar a compilação de todos os arquivos de implementação e cabeçalho. Esse comando automatiza o processo, compilando apenas os arquivos que foram modificados, economizando tempo e evitando erros.
3. **Abrir a pasta 'bin':**
   - Após a compilação, utilize o comando **‘cd bin’** para mudar para o diretório **‘bin’**, onde os arquivos compilados são armazenados.
4. **Executar o programa:**
   - Estando no diretório **‘bin’**, use o comando **‘./programa T N arqA.dat arqB.dat arqC.dat arqD.dat arqE.dat’** para executar o programa, substituindo **‘T’** pelo número de *threads* desejado e **‘N’** pelo tamanho da matriz, 100x100 ou 1000x1000.

## Gráficos contendo o tempo de execução dos experimentos
### Utilizando clock()
#### a) Matriz 100x100
![Tempo Soma](https://github.com/Leo19112/Projeto_S.O/blob/main/Soma100x100.PNG).
![Tempo Multiplicação](https://github.com/Leo19112/Projeto_S.O/blob/main/Multi100x100.PNG).
![Tempo Redução](https://github.com/Leo19112/Projeto_S.O/blob/main/Reducao100x100.PNG).
![Tempo Total](https://github.com/Leo19112/Projeto_S.O/blob/main/total100x100.PNG).

#### b) Matriz 1000x1000
![Tempo Soma](https://github.com/Leo19112/Projeto_S.O/blob/main/Soma1000x1000.PNG).
![Tempo Multiplicação](https://github.com/Leo19112/Projeto_S.O/blob/main/Multi1000x1000.PNG).
![Tempo Redução](https://github.com/Leo19112/Projeto_S.O/blob/main/Reducao1000x1000.PNG).
![Tempo Total](https://github.com/Leo19112/Projeto_S.O/blob/main/Total1000x1000.PNG).

### Uilizando clock_gettime
#### a) Matriz 100x100
![Tempo Soma](https://github.com/Leo19112/Projeto_S.O/blob/main/Soma(1)100x100.PNG).
![Tempo Multiplicação](https://github.com/Leo19112/Projeto_S.O/blob/main/Multi(1)100x100.PNG).
![Tempo Redução](https://github.com/Leo19112/Projeto_S.O/blob/main/Reducao(1)100x100.PNG).
![Tempo Total](https://github.com/Leo19112/Projeto_S.O/blob/main/Total(1)100x100.PNG).

#### b) Matriz 1000x1000
![Tempo Soma](https://github.com/Leo19112/Projeto_S.O/blob/main/Soma(1)1000x1000.PNG).
![Tempo Multiplicação](https://github.com/Leo19112/Projeto_S.O/blob/main/Multi(1)1000x1000.PNG).
![Tempo Redução](https://github.com/Leo19112/Projeto_S.O/blob/main/Reduao(1)1000x1000.PNG).
![Tempo Total](https://github.com/Leo19112/Projeto_S.O/blob/main/Total(1)1000x1000.PNG).

## Conclusões sobre os resultados obtidos
### a) Primitiva **'clock'** em uma matriz 100x100

Inicialmente, foi realizado um teste no projeto utilizando a primitiva **‘clock’**. Foram feitas dez execuções do programa, coletando os dados dos tempos de soma, multiplicação, redução e tempo total do programa em segundos. Esses dados foram lançados em uma planilha, e a média das dez amostras foi calculada. Dessa maneira, foi possível tirar conclusões mais assertivas sobre os resultados obtidos de uma matriz qualquer 100x100 contendo números de 1 a 9.

Analisando os resultados, observamos que o tempo de soma aumenta conforme o número de *threads* instanciado pelo usuário. No caso do tempo de multiplicação, ocorre uma diminuição do tempo conforme aumenta o número de *threads*. Utilizando duas *threads* o usuário obtém o menor tempo de todos, enquanto ao usar uma *thread*, obtém o maior tempo. O tempo de redução, o cenário é similar ao do tempo de soma. Finalmente, ao analisar o tempo total de execução do programa, constatamos que o usuário obtém um tempo consideravelmente maior utilizando apenas uma *thread* em comparação com duas ou quatro *threads*. No melhor cenário, o usuário deverá utilizar duas *threads* para realizar as operações com as matrizes.

Foram buscadas soluções para verificar se era possível reduzir ainda mais o tempo de execução com quatro *threads*. Entretanto, não foi possível obter um resultado melhor do que o já obtido. Pode ser que alguma lógica de programação utilizada esteja contribuindo para essa pequena diferença em comparação com duas *threads*.

### b) Primitiva **'clock'** em uma matriz 1000x1000

Inicialmente, foi realizado um teste no projeto utilizando a primitiva **‘clock’**. Foram feitas dez execuções do programa, coletando os dados dos tempos de soma, multiplicação, redução e tempo total do programa em segundos. Esses dados foram lançados em uma planilha, e a média das dez amostras foi calculada. Dessa maneira, foi possível tirar conclusões mais assertivas sobre os resultados obtidos de uma matriz 1000x1000 contendo números de 1 a 9.

Analisando os resultados, observamos que o tempo de soma diminui conforme o número de *threads* instanciado pelo usuário. No caso do tempo de multiplicação, ocorre um aumento considerável do tempo com duas ou quatro *threads* em relação a uma *thread* só. O tempo de redução apresenta um cenário similar ao do tempo de soma. Finalmente, ao analisar o tempo total de execução do programa, constatamos que o usuário obtém um tempo consideravelmente menor utilizando apenas uma *thread*. 

No entanto, durante os testes, foi constatado que, ao usar duas ou quatro *threads*, o tempo do programa retornava maior do que o tempo real. Após algumas pesquisas, descobrimos que esse erro ocorre porque a primitiva ’clock’ soma o tempo de cada *thread*. Buscando contornar esse problema, foi encontrado que o uso da primitiva ‘clock_gettime’ poderia solucioná-lo. Para isso, foi implementada uma versão do projeto que utiliza esta primitiva.

### c) Primitiva **'clock_gettime'** em uma matriz 100x100

Inicialmente, foi realizado um teste no projeto utilizando a primitiva **‘clock_gettime’** . Foram feitas dez execuções do programa, coletando os dados dos tempos de soma, multiplicação, redução e tempo total do programa em segundos. Esses dados foram lançados em uma planilha, e a média das dez amostras foi calculada. Dessa maneira, foi possível tirar conclusões mais assertivas sobre os resultados obtidos de uma matriz 100x100 contendo números de 1 a 9.

Analisando os resultados, observamos que o tempo de soma aumenta conforme o número de *threads* instanciado pelo usuário, o que não é muito comum. No caso do tempo de multiplicação, ocorre uma diminuição do tempo conforme aumenta o número de *threads*. Utilizando quatro *threads*, obtém-se o menor tempo, indicando que a  otimização/performance do código está correta. O tempo de redução apresenta um cenário similar ao do tempo de soma, apresentando apenas uma única diferença, com uma diferença considerável nos valores conforme aumenta o número de *threads*.

Por fim, ao analisar o tempo total de execução do programa, constatamos que o usuário obteve um tempo consideravelmente maior utilizando apenas uma *thread*, o que era de se esperar, em comparação com duas ou quatro *threads*. No melhor cenário, o usuário deve utilizar quatro *threads* para realizar as operações com matrizes.

### d) Primitiva **'clock_gettime'** em uma matriz 1000x1000

Inicialmente, foi realizado um teste no projeto utilizando a primitiva **‘clock_gettime’** . Foram feitas dez execuções do programa, coletando os dados dos tempos de soma, multiplicação, redução e tempo total do programa em segundos. Esses dados foram lançados em uma planilha, e a média das dez amostras foi calculada. Dessa maneira, foi possível tirar conclusões mais assertivas sobre os resultados obtidos de uma matriz 100x100 contendo números de 1 a 9.

Analisando os resultados, observamos que o tempo de soma aumenta conforme o número de *threads* instanciado pelo usuário, o que é incomum. No caso do tempo de multiplicação, a utilização de quatro *threads* no programa obteve o melhor resultado, enquanto a utilização de duas *threads* obteve o pior resultado. O tempo de redução, por algum motivo, apresenta o mesmo tempo para uma ou quatro *threads*, ambos com o pior desempenho. A utilização de apenas duas *threads* apresenta o dobro do desempenho. 

Por fim, ao analisar o tempo total de execução do programa, constatamos que o usuário obteve um tempo menor utilizando quatro *threads*, o que era de se esperar, demonstrando que a otimização/performance do código está correta. No entanto, o pior resultado foi obtido utilizando duas *threads*, o que não é muito comum. As *threads* foram separadas conforme o tamanho da matriz em ambos os casos (100x100 e 1000x1000). Foi estabelecido também um índice de início e fim para as *threads*, e utilizado o join para que as *threads* que já finalizaram a execução esperassem as que ainda estão em execução.
