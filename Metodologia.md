## Metodologia 

### Dados e Linguagem de Programação


Os dados serão obtidos por meio de sensores da plataforma de prototipagem em Arduino e serão analisados com rigor estatístico. Esses dados serão utilizados para simulações e inferências estatísticas conforme a necessidade da pesquisa.

Na escolha da(s) linguagem(s), será utilizada principalmente a linguagem C/C++, padrão da plataforma Arduino, devido à sua proximidade com o hardware, o que permite o controle de pinos de entrada e saída, temporizadores, interrupções e outros recursos do compilador (MITCHELL, 2012). Essa linguagem também permite um uso eficiente da memória, o que é importante uma vez que o microcontrolador do Arduino possui uma quantidade limitada de memória disponível. Além disso, por permitir programação orientada a objetos, facilita a codificação de estruturas complexas e a reutilização de código (STROUSTRUP, 2013).

Para a análise dos dados, serão utilizadas as linguagens R ou Python, devido à facilidade de codificação e às bibliotecas disponíveis para análise de dados, plotagem e estatística em geral, conforme discutido por Wickham (2016) e VanderPlas (2016).

### Conceitos Básicos de Probabilidade Utilizados na Robótica Probabilística

Nesta seção, serão abordados os conceitos básicos de probabilidade utilizados em robótica probabilística. Nesse sentido, serão utilizados conceitos abordados por Ross (2014a). Em robótica probabilística, quantidades como medidas de sensores, controles, estados do robô e o ambiente são modeladas por variáveis aleatórias. Uma variável aleatória pode assumir múltiplos valores que estão de acordo com leis de probabilidade específicas. Nesse sentido, a inferência probabilística é o processo de calcular essas leis que derivam de outras variáveis aleatórias e dos dados observados. Assim definimos:

$$P(X = x)$$

Sendo \(X\) uma variável aleatória, a probabilidade de \(X\) assumir um valor \(x\) é \(P(X = x)\). No caso de variáveis discretas, o somatório das probabilidades de todos os possíveis valores de \(X\) é igual a 1, ou seja:

$$\sum_x P(X = x) = 1$$

No caso contínuo, a integral da função de densidade de probabilidade é igual a 1, ou seja:

$$\int p(x) \, dx = 1$$

No estudo probabilístico, há o conceito de probabilidade conjunta que descreve a probabilidade das variáveis aleatórias \(X\) e \(Y\) assumirem os valores \(x\) e \(y\) respectivamente. Esse conceito é dado por:

$$p(x,y) = P(X = x \text{ e } Y = y)$$

No caso de variáveis independentes:

$$p(x,y) = p(x)p(y)$$

Frequentemente, as variáveis aleatórias têm informações sobre outras variáveis. Por exemplo, os sensores podem fornecer informações importantes sobre o estado do robô para a modelagem probabilística. Nesse sentido, é necessário utilizar a probabilidade condicional para relacionar as variáveis:

$$p(x | y) = P(X = x | Y = y)$$

No caso de \(p(y) > 0\), a probabilidade condicional é definida por:

$$p(x | y) = \frac{p(x,y)}{p(y)} = \frac{p(x)p(y)}{p(y)} = p(x)$$

Os axiomas de probabilidade e a probabilidade condicional permitem determinar os resultados da probabilidade total dados por:

$$p(x) = \sum_y p(x | y) p(y) \quad \text{(caso discreto)}$$

$$p(y) = \int p(x | y)p(y) dy \quad \text{(caso contínuo)}$$

Os resultados da probabilidade total permitem a formulação de importantes equações para a robótica probabilística, conhecidas como regras de Bayes, apresentadas da seguinte forma: para \(p(y) > 0\) tem-se:

$$
p(x | y) = \frac{p(y | x) p(x)}{p(y)} = \frac{p(y | x) p(x)}{\sum_{x'}p(y | x')p(x')} \quad \text{(discreto)}
$$

$$
p(x | y) = \frac{p(y | x) p(x)}{p(y)} = \frac{p(y | x) p(x)}{\int p(y | x') p(x') dx'} \quad \text{(contínuo)}
$$



Uma vez que \(x\) é a quantidade a ser inferida a partir de \(y\), a probabilidade \(p(x)\) será denominada de distribuição de probabilidade anterior e \(y\) será a variável de dados do estudo, por exemplo, a medida de um sensor do robô em estudo. A distribuição \(p(x)\) resume a informação sobre a variável \(X\) antes de incorporarmos os dados de \(y\). A probabilidade \(p(x | y)\) é chamada de distribuição de probabilidade posterior de \(X\). 

A regra de Bayes permite inferir a quantidade \(x\) a partir dos dados do sensor \(y\) utilizando a probabilidade inversa, isto é, calcular a probabilidade dos dados \(y\) assumindo que \(x\) é o caso a ser analisado (THRUN; BURGARD; DURRANT-WHYTE 2005). A probabilidade \(p(x | y)\) em robótica probabilística é chamada de modelo generativo, pois descreve em algum nível de abstração como o estado da variável \(X\) influencia a medida do sensor \(Y\).

Na regra de Bayes, observa-se primeiramente que \( p(y) \) não depende de \( x \). Por essa razão, utiliza-se   $\frac{1}{p(y)}$   para normalizar a regra de Bayes. Assim, ao usar   $\eta = \frac{1}{p(y)}$    , obtemos a seguinte formulação:

$$
p(x | y) = \eta p(y | x)p(x)
$$

Essa formulação tem como objetivo deixar evidente que, ao final do processo de aplicação da regra de Bayes, deve-se realizar a normalização para 1.

 [Voltar ao índice](index.md)
