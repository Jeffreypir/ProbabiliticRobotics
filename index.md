# Robótica Probabilística: Automação Estocástica com Arduino

## Introdução

A robótica é uma ciência que observa e manipula o ambiente físico por meio de aparelhos de controle e computadores. Conforme Thrun, Burgard e Durrant-Whyte (2005), as possibilidades de aplicação da robótica vão desde a indústria, com braços robóticos, até a medicina, com manipuladores que auxiliam cirurgiões, e também na análise de ambientes hostis, por meio de robôs tipo drone e/ou andarilhos. Nesse contexto, deve-se destacar que a atuação dos robôs é condicionada pelo hardware, como motores que podem apresentar incerteza e erro devido a ruído de controle, desgaste ou falha mecânica.

O software também deve ser considerado, uma vez que todos os programas que gerenciam o hardware e o funcionamento do robô são modelos que representam o mundo de maneira aproximada. De acordo com Ross (2014a), modelos são aproximações do mundo real que representam alguma situação ou processo físico. Dessa forma, o modelo pode estar suscetível a problemas como a falta de parâmetros necessários para o funcionamento do robô em determinado ambiente e a incerteza dos dados medidos quando o robô enfrenta situações com variações estocásticas, dificultando sua adaptação. Além disso, o próprio funcionamento do algoritmo pode ser afetado por problemas de implementação computacional, como excesso de processamento e limitações de memória.

O nível de incerteza no funcionamento do robô depende da aplicação. Nesse sentido, conforme Thrun, Burgard e Durrant-Whyte (2005), a robótica probabilística é a área que tem como objetivo analisar dados dos sensores do robô e construir algoritmos robustos baseados em Estatística e Probabilidade, que contemplem as incertezas relacionadas aos dados, ao software, ao hardware ou ao ambiente. O intuito é possibilitar a construção e utilização de robôs confiáveis para as mais variadas tarefas que a sociedade possa necessitar, como o uso de robôs em ambientes de risco para seres humanos.

Na construção e nos testes com robôs, é importante ter uma plataforma de prototipagem, ou seja, uma plataforma de hardware e software para a implementação de modelos e algoritmos em protótipos de robôs. A plataforma Arduino se destaca por fornecer uma plataforma livre. A construção de hardware e software no Arduino, bem como sua documentação, são abertas, permitindo que os desenvolvedores analisem o funcionamento dos protótipos sem restrições de licença (MITCHELL, 2012). Além disso, seus componentes são de fácil acesso, o que torna a plataforma favorável para a análise de dados e a implementação de modelos, garantindo a fidelidade dos dados.

Nesse sentido, o presente trabalho propõe um estudo sobre robótica probabilística e suas aplicações, utilizando a plataforma Arduino, por essa área ter um amplo campo de desenvolvimento em diferentes ambientes. Assim, são necessários algoritmos probabilístico-estatísticos robustos para a aplicabilidade de robôs em diferentes tarefas e ambientes.

## Objetivos

### Geral

Implementar e analisar algoritmos probabilísticos/estatísticos por meio da robótica probabilística para melhor adaptabilidade de robôs em diferentes contextos.

### Específicos

- Programar algoritmos da robótica probabilística em diferentes contextos.
- Analisar dados para aplicação na adaptação de robôs e automação.
- Averiguar a utilização da plataforma Arduino como plataforma de prototipagem e estudo de robôs.

## Metodologia

### Dados e linguagem de programação

Os dados serão obtidos por meio de sensores da plataforma de prototipagem em Arduino e serão analisados com rigor estatístico. Esses dados serão utilizados para simulações e inferências estatísticas conforme a necessidade da pesquisa.

Na escolha da(s) linguagem(s), será utilizada, principalmente, a linguagem C/C++ padrão da plataforma Arduino, devido à sua proximidade com o hardware, o que permite o controle de pinos de entrada e saída, temporizadores, interrupções e outros recursos do compilador (MITCHELL, 2012). Essa linguagem também permite um uso eficiente da memória, o que é importante, uma vez que o microcontrolador do Arduino possui uma quantidade limitada de memória disponível. Além disso, por permitir programação orientada a objetos, facilita a codificação de estruturas complexas e a reutilização de código (STROUSTRUP, 2013).

Para a análise dos dados, serão utilizadas as linguagens R ou Python, devido à facilidade de codificação e às bibliotecas disponíveis para análise de dados, plotagem e estatística em geral, conforme discutido por Wickham (2016) e VanderPlas (2016).

### Conceitos básicos de probabilidade utilizados na robótica probabilística

Nesta seção, serão abordados os conceitos básicos de probabilidade utilizados em robótica probabilística. Nesse sentido, será utilizada conceitos abordados por Ross (2014a). Em robótica probabilística, quantidades como medidas de sensores, controles, estados do robô e o ambiente são modeladas por variáveis aleatórias. Uma variável aleatória pode assumir múltiplos valores que estão de acordo com leis de probabilidade específicas. Nesse sentido, a inferência probabilística é o processo de calcular essas leis, que derivam de outras variáveis aleatórias e dos dados observados. Assim, definimos:

P(X=x).

Sendo X uma variável aleatória, a probabilidade de X assumir um valor x é P(X = x). No caso de variáveis discretas, o somatório das probabilidades de todos os possíveis valores de X é igual a 1, ou seja,

∑_x▒〖p(X=x)=1〗.

No caso contínuo, a integral da função de densidade de probabilidade é igual a 1, ou seja,	
∫▒〖p(x)=1.〗

No estudo probabilístico, há o conceito de probabilidade conjunta, que descreve a probabilidade das variáveis aleatórias X e Y assumirem os valores x e y, respectivamente. Esse conceito é dado por:

p(x,y)=p(X=x e Y=y).

No caso de variáveis independentes:

p(x,y)=p(x)p(y).

Frequentemente, as variáveis aleatórias têm informações sobre outras variáveis. Por exemplo, os sensores podem fornecer informações importantes sobre o estado do robô para a modelagem probabilística. Nesse sentido, é necessário utilizar a probabilidade condicional para relacionar as variáveis,

p(x │ y )=p(X=x ┤| Y=y).

No caso p(y)>0, a probabilidade condicional é definida por:

p(x ┤| y)=(p(x)p(y))/(p(y))=p(x).

Os axiomas de probabilidade e a probabilidade condicional permitem determinar os resultados da probabilidade total dados por:

p(x)= ∑_y▒〖p(x ┤| y)〗 p(y)      (caso discreto)

p(y)= ∫▒〖p(x │ y)p(y)dy     (caso contínuo)〗.

Os resultados da probabilidade total permitem a formulação de importantes equações para a robótica probabilística, conhecidas como regras de Bayes, apresentadas da seguinte forma: para p(y) >0, tem-se:

p(x ┤| y)=(p(y ┤| x) p(x))/p(y) =(p(y ┤| x) p(x))/(∑_(x^')▒〖p(y ┤| x')〗 p(x^' )  )      (discreto)

p(x ┤| y)=(p(y ┤| x) p(x))/(p(y))=(p(y ┤| x) p(x))/(∫▒〖p(y ┤| x') p(x') dx'〗)      (contínuo).

Uma vez que x é a quantidade a ser inferida a partir de y, a probabilidade p(x) será denominada de distribuição de probabilidade anterior, e y será a variável de dados do estudo, por exemplo, a medida de um sensor do robô em estudo. A distribuição p(x) resume a informação sobre a variável X antes de incorporarmos os dados de y. A probabilidade p(x∣y) é chamada de distribuição de probabilidade posterior de X. A regra de Bayes permite inferir a quantidade x a partir dos dados do sensor y utilizando a probabilidade inversa, isto é, calcular a probabilidade dos dados y assumindo que x é o caso a ser analisado (THRUN; BURGARD; DURRANT-WHYTE, 2005). A probabilidade p(x | y), em robótica probabilística, é chamada de modelo generativo, pois descreve, em algum nível de abstração, como o estado da variável X influencia a medida do sensor Y.

Na regra de Bayes, observa-se primeiramente que p(y) não depende de x. Por essa razão, utiliza-se 1/(p(y) ) para normalizar a regra de Bayes. Assim, ao usar η = 1/(p(y) ), obtemos a seguinte formulação:

p(x ┤| y)= η p(y ┤| x)p(x).

Essa formulação tem como objetivo deixar evidente que, ao final do processo de aplicação da regra de Bayes, deve-se realizar a normalização para 1.

### O ambiente ou mundo do robô

O ambiente do robô é um sistema dinâmico que possui um estado interno. O robô adquire informações do ambiente por meio de sensores, que podem apresentar ruídos que afetam a qualidade das informações obtidas. Além disso, muitas informações são difíceis de serem obtidas, pois muitas variáveis não podem ser medidas de forma adequada pela interação do robô com o ambiente. Para Ross (2014a), não existe um ambiente perfeitamente modelável na robótica, devido a essas incertezas e limitações dos sensores. Assim, as variáveis medidas pelo robô devem ser modeladas como variáveis aleatórias, permitindo inferências probabilísticas sobre o estado do ambiente com base nas informações obtidas.

### Algoritmo Probabilístico e Estocástico

Um algoritmo probabilístico pode ser utilizado para inferir o estado do ambiente com base em medidas obtidas pelos sensores do robô. Um exemplo é a utilização de um filtro de partículas, que é uma técnica baseada em Monte Carlo para representar a distribuição de probabilidade de um estado desconhecido de um sistema dinâmico, como o ambiente do robô (THRUN; BURGARD; DURRANT-WHYTE, 2005). Um filtro de partículas utiliza um conjunto de amostras (partículas) para representar a distribuição de probabilidade posterior do estado do sistema. A cada nova medida obtida pelo sensor, as partículas são atualizadas com base na regra de Bayes, permitindo uma estimativa do estado do ambiente com base nas informações disponíveis.

## Resultados Esperados

Espera-se que a implementação de algoritmos probabilísticos e estocásticos na plataforma Arduino permita uma melhor adaptação dos robôs a diferentes ambientes. A análise dos dados obtidos pelos sensores do robô, juntamente com a aplicação de modelos probabilísticos, deve resultar em uma maior confiabilidade e precisão no funcionamento dos robôs. Além disso, espera-se que a utilização da plataforma Arduino como ferramenta de prototipagem e estudo possibilite o desenvolvimento de novas aplicações em robótica probabilística, contribuindo para o avanço da área.

## Referências

- MITCHELL, S. Arduino: Aprendendo a Programar. 3. ed. São Paulo: Novatec, 2012.
- ROSS, S. M. Introdução à Probabilidade e Estatística para Engenheiros e Cientistas. 4. ed. São Paulo: Elsevier, 2014.
- STROUSTRUP, B. The C++ Programming Language. 4. ed. Boston: Addison-Wesley, 2013.
- THRUN, S.; BURGARD, W.; DURRANT-WHYTE, H. Robótica Probabilística. 1. ed. São Paulo: Elsevier, 2005.
- VANDERPLAS, J. Python Data Science Handbook: Essential Tools for Working with Data. 1. ed. Sebastopol: O'Reilly Media, 2016.
- WICKHAM, H. ggplot2: Elegant Graphics for Data Analysis. 2. ed. Springer, 2016.

