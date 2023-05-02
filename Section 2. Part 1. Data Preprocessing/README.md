# Etapas de Pré-processamento

A primeira etapa (ou pré-etapa) na construção de um modelo de machine learning consiste na preparação
dos dados que o modelo pretende usar. Essa etapa é essencial porque, dado que não há
problemas na modelagem, é ela que garante que o modelo terá um resultado de qualidade. É o velho ditado:
_"garbage in, garbage out"_. Logo, para não termos **_garbage out_**, vamos listar e explicar cada
uma das seguintes etapas de pré-processamento:

1. Importação das bibliotecas;
2. Importação do _dataset_;
3. Lidando com valores ausentes;
4. Lidando com valores categóricos;
5. Separação em treinamento e teste;
6. _Feature scaling_.

Ao longo do processo, iremos usar um dataset de um e-commerce fictício de 10 linhas para aplicarmos cada uma das etapas. 

## 1. Importação das bibliotecas

No primeiro momento vamos trabalhar com as bibliotecas `numpy`, `matplotilib`
e `pandas`. `numpy` é uma biblioteca de criação e manipulação de arrays, `matplotlib`, plotagem de gráficos e `pandas`,
de criação e manipulação de dataframes.

Mais tarde, também será introduzida no pré-processamento uma biblioteca de machine learning: o `sckitlearn`. 

## 2. Importação do _Dataset_

Etapa de importação do _dataset_ (conjunto de dados) a ser analisado. Nesta etapa
iremos usar o método `read_csv()` do pandas para ler os dados que estão no formato csv. 

No exemplo em questão, o dataset é formado por um conjunto de informações de compradores de um e-commerce fictício.
Cada linha do csv possui a informação de _**Country**_ (País), _**Age**_ (Idade) e _**Salary**_ (Salário) de um consumidor.
A última coluna (_**Purchase**_) indica se o consumidor comprou ou não na loja virtual. No total, o dataset é 
formado por 10 consumidores (ou seja, 10 linhas).

Após a importação, separamos o dataset em variável dependente (**y**) e variável independente (**X**).
De forma simplificada, a variável dependente se trata da variável que queremos encontrar. No nosso exemplo é a coluna
_**Purchase**_, que mostra se o consumidor comprou ou não. Já a variável independente é composta por informações do meu dataset
que permitem determinar o meu resultado, ou seja, que permitem determinar se houve a compra ou não.
No nosso exemplo, a variável independente é composta pelas informações de _**Country**_, _**Age**_ e _**Salary**_.

Portanto, o **X** é formado pelas colunas **_Country_**, **_Age_** e **_Salary_**, e o y é formado
pela coluna **_Purchase_**.

## 3. Lidando com valores ausentes

No campo de Machine Learning, é muito comum que o dataset tenha valores ausentes. O motivo são vários:
nem sempre é possível fazer uma medição, o equipamento se danificou ou a informação simplesmente
se perdeu. Como esse problema é frequente, é muito importante criar estratégias para resolução dessa questão.
Existem duas formas principais de lidar com isso:

1. **Remoção**: essa técnica consiste em remover as linhas com dados ausentes. Ela pode
ser boa para casos em que o dataset seja grande e tenham poucos valores ausentes.
2. **Substituição**: essa técnica consiste em substituir o valor ausente por outro. Pode
ser substituir pela média, mediana, último valor válido etc. É uma boa ideia
quando remover os dados ausentes geram perda de informaçãoes importante.

No nosso exemplo, com auxílio do `scikitlearn`, substituímos os valores
vazios pela média da respectiva coluna.

## 4. Lidando com valores categóricos

Os modelos de machine learning se alimentam tanto de dados numéricos quanto de dados categóricos. Como os modelos
processam apenas números, é imprescindível que transformemos os dados categóricos em dados numéricos.

No nosso exemplo usamos o `OneHotEncoder` para transformar a coluna **Country**
de **X** e `LabelEncoder` para a única coluna da variável **y**.

## 5. Separação em treinamento e teste

Umas das principais etapas do Machine Learning consiste na separação
do dataset em dataset de treinamento e dataset de teste. O primeiro tem o propósito de treinar o modelo de machine learning, enquanto o
segundo tem a função de validar (testar) o modelo.

Com o uso da função `train_test_split` do `sckitlearn`, dividimos o dataset
e o resultado foram 4 conjunto de dados: `X_train`, `X_test`, `y_train` e `y_test`.


## 6. _Feature scaling_

_Feature Scaling_, ou escalonamento de recursos em português, consiste no processo de 
ajustar as variáveis do dataset de forma a colocá-las em uma mesma escala.
Existem duas técnicas de _feature scaling_:

1. **Padronização**: tem o objetivo de colocar os dados em uma mesma escala, sendo que esta escala
tem média 0 e desvio-padrão igual a 1;
2. **Normalização:** também tem o objetivo de colocar os dados em uma mesma escala, no entanto, 
nesse caso os valores variam de 0 a 1 ou dde -1 a 1, no caso de ter valores negativos nos dados.

Enquanto a **Padronização** funciona sempre, a **Normalização** é mais apropriada
para variáveis que já possuem o comportamento de uma distribuição normal.

No nosso exemplo, usamos a técnica de **Padronização** para as colunas _**Age**_ e _**Salary**_.
A coluna _**Country**_, que agora são três colunas com valores binários, não foram aplicadas a Padronização devido
ao fato dessas colunas já estarem dentro da escala das outras colunas.