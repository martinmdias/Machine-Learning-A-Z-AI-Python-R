# Data Preprocessing Tools

## 1. Importing the Libraries

No primeiro momento vamos trabalhar com as bibliotecas `numpy`, `matplotilib`
e `pandas`. Numpy é uma biblioteca de criação e manipulação de arrays, matplotlib
é uma biblioteca de plotagem de gráficos e pandas é uma biblioteca de
criação e manipulação de dataframes.

Mais tarde, o `sckitlearn`, uma biblioteca de machine learning será introduzida

## 2. Importing the Dataset

Etapa de importação do conjunto de dados (dataset) a ser analisado. Nesta etapa
fazemos uso do método `read_csv()` do pandas para ler os dados que têm como 
extensão o .csv.

No exemplo em questão, o dataset é formado por um conjunto de informações
de compradores de um ecommerce fictício. Cada linha do csv possui a informação
de País (Country), Idade (Age) e Salário (Salary) de um único consumidor.
A última coluna (Purchase) indica se o consumidor comprou ou não na loja.

Em seguida, separamos o dataset em variável independente (**X**) e variável
dependente (**y**).Em termos simples, a variável indenpendente são informações do meu dataset
que permitem determinar o meu resultado (ou **y**).
No nosso exemplo, queremos, a partir de informações de país, idade e salário, saber se
um consumidor comprou ou não no nosso e-commerce.

Portanto, o **X** é formado pelas colunas **Country**, Age e **Salary**, e o y é formado
pela coluna Purchase.

## 3. Taking care of missing data

É muito comum que o dataset tenha valores ausentes em uma ou mais linhas e saber
lidar com esses dados é de suma importância. Existem duas formas de lidar com isso:

1. Remoção: essa técnica consiste em remover as linhas com dados ausentes. Ela pode ser
ser boa para casos em que o dataset seja grande e tenham poucos valores ausentes.
2. Substituição: essa técnica consiste em substituir o valor ausente por outro. Pode
ser substituir pela média, medida, último valor válido etc. É uma boa ideia
quando remover os dados ausentes geram perda de informaçãoes importante

No nosso exemplo, com auxílio do `scikitlearn`, substituímos os valores
vazios pela média de toda a coluna

## 4. Encoding Categorical Values

Modelos de Machine Learning utilizam valores numéricos para executar
tarefas de classificação e predição. Por isso que é importante transformar
os valores categóricos, ou seja, colunas que podem assumir um conjunto
finito de valores, em números.

Nesta etapa, portanto, usamos o OneHotEncoder para transformar a coluna Country
de X e LabelEncoder para a única coluna da variável y.

## 5. Splitting the dataset into the Training set and Test set

Umas das principais etapas do Machine Learning consiste na separação
do dataset em dataset de Treinamento e dataset de Teste. O primeiro servirá
com o propósito de treinar o modelo de machine learning, enquanto que o
segundo tem a função de validar (testar) o modelo.


Com o uso da função `train_test_split` do `sckitlearn`, dividimos o dataset
e o resultado foram 4 conjunto de dados: X_train, X_test, y_train e y_test.


## 6. _Feature Scaling_

_Feature Scaling_, ou escalonamento de recursos em português, consiste na em
ajustar a escala das variáveis do dataset.
Existem duas técnicas de feature scaling:
1. Padronização (Estandardização): garante que a variável tenha média 0
e desvio-padrão igual a 1
2. Normalização: faz com que a variável tenha distruição normal

Enquanto a padronização funciona sempre, a normalização é mais apropriada
para variáveis que já possuem o comportamento de uma distribuição normal.
No nosso exemplo, fizemos uso da padronização apenas para variáveis
que não são binárias, ou seja, apenas para as colunas Age e Salary.