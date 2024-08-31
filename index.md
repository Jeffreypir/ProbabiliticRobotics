# Robótica Probabilística: Automação Estocástica com Arduino

## Introdução

A robótica é uma ciência que observa e manipula o ambiente físico por meio de aparelhos de controle e computadores. Conforme Thrun, Burgard, e Durrant-Whyte (2005), as possibilidades de aplicação da robótica vão desde a indústria, com braços robóticos, até a medicina, com manipuladores que auxiliam cirurgiões, e também na análise de ambientes hostis por meio de robôs tipo drone e/ou andarilhos. Nesse contexto, deve-se destacar que a atuação dos robôs é condicionada pelo hardware, como motores que podem apresentar incerteza e erro devido a ruído de controle, desgaste ou falha mecânica.

O software também deve ser considerado, uma vez que todos os programas que gerenciam o hardware e o funcionamento do robô são modelos que representam o mundo de maneira aproximada. De acordo com Ross (2014a), modelos são aproximações do mundo real que representam alguma situação ou processo físico. Dessa forma, o modelo pode estar suscetível a problemas como a falta de parâmetros necessários para o funcionamento do robô em determinado ambiente e a incerteza dos dados medidos quando o robô enfrenta situações com variações estocásticas, dificultando sua adaptação. Além disso, o próprio funcionamento do algoritmo pode ser afetado por problemas de implementação computacional, como excesso de processamento e limitações de memória.

O nível de incerteza no funcionamento do robô depende da aplicação. Nesse sentido, conforme Thrun, Burgard, e Durrant-Whyte (2005), a robótica probabilística é a área que tem como objetivo analisar dados dos sensores do robô e construir algoritmos robustos baseados em Estatística e Probabilidade que contemplem as incertezas relacionadas aos dados, ao software, ao hardware ou ao ambiente. O intuito é possibilitar a construção e utilização de robôs confiáveis para as mais variadas tarefas que a sociedade possa necessitar, como o uso de robôs em ambientes de risco para seres humanos.

Na construção e nos testes com robôs, é importante ter uma plataforma de prototipagem, ou seja, uma plataforma de hardware e software para a implementação de modelos e algoritmos em protótipos de robôs. A plataforma Arduino se destaca por fornecer uma plataforma livre. A construção de hardware e software no Arduino, bem como sua documentação, são abertas, permitindo que os desenvolvedores analisem o funcionamento dos protótipos sem restrições de licença (MITCHELL, 2012). Além disso, seus componentes são de fácil acesso, o que torna a plataforma favorável para a análise de dados e a implementação de modelos, garantindo a fidelidade dos dados.

Nesse sentido, o presente trabalho propõe um estudo sobre robótica probabilística e suas aplicações utilizando a plataforma Arduino, por essa área ter um amplo campo de desenvolvimento em diferentes ambientes. Assim, são necessários algoritmos probabilístico-estatísticos robustos para a aplicabilidade de robôs em diferentes tarefas e ambientes.

## Objetivos

### Geral
Implementar e analisar algoritmos probabilísticos/estatísticos por meio da robótica probabilística para melhor adaptabilidade de robôs em diferentes contextos.

### Específicos
- Programar algoritmos da robótica probabilística em diferentes contextos.
- Analisar dados para aplicação na adaptação de robôs e automação.
- Averiguar a utilização da plataforma Arduino como plataforma de prototipagem e estudo de robôs.

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

$$p(y) = \int p(x | y)p(y) \, dy \quad \text{(caso contínuo)}$$

Os resultados da probabilidade total permitem a formulação de importantes equações para a robótica probabilística, conhecidas como regras de Bayes, apresentadas da seguinte forma: para \(p(y) > 0\) tem-se:

$$p(x | y) = \frac{p(y | x) p(x)}{p(y)} = \frac{p(y | x) p(x)}{\sum_{x'}p(y | x')p(x')} \quad \text{(discreto)}$$

$$p(x | y) = \frac{p(y | x) p(x)}{p(y)} = \frac{p(y | x) p(x)}{\int p(y | x') p(x') \, dx'} \quad \text{(contínuo)}$$

Uma vez que \(x\) é a quantidade a ser inferida a partir de \(y\), a probabilidade \(p(x)\) será denominada de distribuição de probabilidade anterior e \(y\) será a variável de dados do estudo, por exemplo, a medida de um sensor do robô em estudo. A distribuição \(p(x)\) resume a informação sobre a variável \(X\) antes de incorporarmos os dados de \(y\). A probabilidade \(p(x | y)\) é chamada de distribuição de probabilidade posterior de \(X\). A regra de Bayes permite inferir a quantidade \(x\) a partir dos dados do sensor \(y\) utilizando a probabilidade inversa, isto é, calcular a probabilidade dos dados \(y\) assumindo que \(x\) é o caso a ser analisado (THRUN; BURGARD; DURRANT-WHYTE 2005). A probabilidade \(p(x | y)\) em robótica probabilística é chamada de modelo generativo, pois descreve em algum nível de abstração como o estado da variável \(X\) influencia a medida do sensor \(Y\).

Na regra de Bayes, observa-se primeiramente que \(p(y)\) não depende de \(x\). Por essa razão, utiliza-se \( \frac{1}{p(y)}\) para normalizar a regra de Bayes. Assim, ao usar \(\eta = \frac{1}{p(y)}\), obtemos a seguinte:

Na regra de Bayes, observa-se primeiramente que \( p(y) \) não depende de \( x \). Por essa razão, utiliza-se    $\frac{1}{p(y)}$    para normalizar a regra de Bayes. Assim, ao usar \( \eta = \frac{1}{p(y)} \), obtemos a seguinte formulação:

$$
p(x | y) = \eta p(y | x)p(x)
$$

Essa formulação tem como objetivo deixar evidente que, ao final do processo de aplicação da regra de Bayes, deve-se realizar a normalização para 1.


#### Estado

Os ambientes caracterizam o que será chamado de estado. Para o presente estudo, o estado será considerado um conjunto formado pelos aspectos do robô e seu ambiente que podem impactar o futuro (THRUN; BURGARD; DURRANT-WHYTE 2005). O estado pode variar ou não com o tempo. Por exemplo, o estado das paredes de um prédio ou edifício são exemplos de estados não mutáveis, enquanto a movimentação de animais ou pessoas são exemplos de estados mutáveis. Quando o estado é mutável, denomina-se estado dinâmico para diferenciá-lo do estado não mutável, que é chamado de estado estático.

No conceito de estado podem existir variáveis do robô como posição, velocidade ou sensores de medição. O estado é denotado por \(x\). Caso seja necessário considerar o estado no instante de tempo \(t\), denota-se por \(x_t\). Quando as informações do estado \(x_t\) podem predizer o futuro, tem-se um estado completo. Na prática, o estado completo é teoricamente relevante, mas de difícil aplicação, pois na criação do modelo seria necessário ter todas as informações do estado do robô e do ambiente, além de armazenar essas informações. Por isso, utiliza-se o estado incompleto para a criação de modelos na robótica probabilística, desde que se tome cuidado na escolha das variáveis do modelo probabilístico. Uma análise das interações do robô com o ambiente é necessária.

#### As Interações com o Ambiente

Existem dois tipos fundamentais de interação do robô com o ambiente: o robô pode ser influenciado pelos estados dos seus atuadores e pela obtenção de informações dos estados dos seus sensores (THRUN; BURGARD; DURRANT-WHYTE 2005). Dessa forma, devem ser analisados os seguintes processos: medições dos sensores do ambiente, controles de ação, ambiente de medição dos dados e controle de dados.

Na medição dos sensores, temos a percepção que é a forma como o robô usa seus sensores para obter informações sobre os estados e o ambiente. Por exemplo, o robô pode obter informações a partir da imagem de uma câmera ou de um scanner. As ações de controle do estado com o mundo são ativadas para forçar uma mudança na relação entre o robô e o ambiente, como por exemplo, a manipulação de objetos pelo robô.

A medida dos dados do ambiente provém do estado do ambiente no qual o robô está situado, por exemplo, medidas de dados de uma câmera. No presente trabalho, as medidas de dados em um instante de tempo \(t\) serão denotadas por \(z_t\). Essa notação facilita a formulação do modelo, pois a representação de todas as medidas de dados feitas no intervalo de tempo \(t_1 < t_2\) pode ser escrita de forma simplificada como:

$$z_{t_1:t_2} = \{z_{t_1}, z_{t_1+1}, z_{t_1+2}, \dots, z_{t_2}\}$$

O controle de dados fornece informações sobre a escolha do estado em um ambiente, como por exemplo, o controle de velocidade de um robô. A notação para controle de dados será \(u_t\). A variável \(u_t\) representa a escolha do estado no intervalo de tempo \((t-1, t]\). De forma semelhante às medidas de estado para um intervalo de tempo \(t_1 < t_2\), todas as sequências de controle são representadas na notação:

$$u_{t_1:t_2} = \{u_{t_1}, u_{t_1+1}, u_{t_1+2}, \dots, u_{t_2}\}$$

Esta seção será finalizada apresentando as interações entre o robô e o ambiente, bem como as notações utilizadas no estudo. Na próxima seção, serão abordadas as relações entre probabilidades e variáveis como estados, medidas de dados e controle de dados.

### As Leis de Probabilidade Aplicadas às Variáveis do Robô

#### A Modelagem Estocástica

Na robótica probabilística, a evolução do estado e das medições é governada por leis de probabilidade que permitem a construção do modelo estocástico do robô. Dessa forma, é necessário especificar a distribuição de probabilidade \(x_t\) que gera o modelo (ROSS 2014a). Sendo um modelo de estados, faz sentido assumir que o estado \(x_t\) é gerado de forma estocástica a partir do estado \(x_{t-1}\). Na modelagem, deve-se ter um modelo que condicione o estado \(x_t\) ao estado anterior, medições e controles, ou seja, é necessário um modelo de probabilidade condicional conforme se segue:

$$p(x_t | x_{0:t-1}, z_{1:t-1}, u_{1:t})$$

No modelo de probabilidade condicional, assume-se que o robô executa uma ação de controle \(u_1\) e em seguida realiza uma medição de dados \(z_1\). Uma informação importante fornecida pelo modelo é que se o estado \(x\) é completo, então ele serve como um resumo suficiente de todas as etapas anteriores. Ou seja, \(x_{t-1}\) é uma estatística suficiente no tempo, levando em consideração os controles e medições \(u_{1:t-1}\) e \(z_{1:t-1}\) respectivamente. Dentre todas as variáveis do modelo acima, se apenas \(u_t\) for relevante e sendo conhecido o estado \(x_{t-1}\), pode-se escrever a seguinte expressão em termos probabilísticos:

$$p(x_t | x_{0:t-1}, z_{1:t-1}, u_{1:t}) = p(x_t | x_{t-1}, u_t)$$

A propriedade utilizada acima é um exemplo de independência condicional. Essa propriedade afirma que as variáveis são independentes umas das outras se for conhecido um terceiro grupo de variáveis, as variáveis condicionantes (THRUN; BURGARD; DURRANT-WHYTE 2005). A independência condicional é importante para a robótica, pois permite que os algoritmos probabilísticos sejam tratáveis de maneira computacional. Caso o interesse do modelo seja nas medições geradas \(z_t\) dado que \(x_t\) é completo, tem-se uma importante independência condicional:

$$p(z_t | x_{0:t}, z_{1:t-1}, u_{1:t}) = p(z_t | x_t)$$

O estado quando completo contém informações suficientes para a predição das medidas \(z_t\). Nesse sentido, quando se tem o estado completo, as informações sobre as medidas passadas, controles e eventos anteriores tornam-se irrelevantes (THRUN; BURGARD; DURRANT-WHYTE 2005). No presente trabalho, \(p(x_t | x_{t-1}, u_t)\) representa a probabilidade de transição de estado, especificando como o ambiente de estados evolui com o tempo modelado como uma função de \(u_t\). Nota-se que a probabilidade de transição de estados é uma distribuição de probabilidade e não uma função determinística. No caso em que a distribuição de transição de estados não depende do índice de tempo \(t\), utiliza-se a expressão \(p(x' | u, x)\), em que \(x'\) é o sucessor e \(x\) é o estado predecessor.

A probabilidade \(p(z_t | x_t)\) é chamada de probabilidade de medição, especificando as leis de probabilidade a partir das quais as medições \(z_t\) são geradas para o ambiente de estado \(x_t\). Pode-se pensar nas medições como projeções ruidosas do estado (THRUN; BURGARD; DURRANT-WHYTE 2005). Quando a probabilidade de medição não depende do índice \(t\), ela será escrita simplesmente como \(p(z | x)\). A probabilidade de transição de estado e a probabilidade conjunta descrevem um sistema dinâmico estocástico para o ambiente do robô. O estado no tempo \(t\) é estocasticamente dependente do estado no tempo \(t-1\) e do controle \(u_t\). A medição \(z_t\) depende estocasticamente do estado no tempo \(t\).

Uma vez discutida a modelagem probabilística para a robótica, deve-se exemplificar a construção e o funcionamento do modelo, bem como a estrutura de funcionamento do algoritmo, o que será feito a seguir.

### Aplicação de Robótica Probabilística

Um conceito importante em robótica probabilística é o de *belief*. Uma *belief* tem a função de refletir o conhecimento interno do robô sobre o estado do ambiente (THRUN; BURGARD; DURRANT-WHYTE 2005). Essa informação, na maior parte das vezes, não pode ser obtida de forma direta. Por exemplo, a posição do robô dada por \(x_t = (14, 12, 12, 745°)\) em termos de coordenadas globais, não é conhecida a menos que se tenha um GPS. Portanto, o robô deve inferir essa posição com base nos dados. Na literatura, sinônimos de *belief* incluem "estado de conhecimento" e "informação de estado". A representação da *belief* é dada por uma distribuição de probabilidade condicional. As distribuições de *belief* são probabilidades posteriores sobre as variáveis de estado condicionadas pelos dados disponíveis (BARBER, 2012). A notação utilizada no presente trabalho para a representação de uma *belief* sobre a variável de estado \(x_t\) é dada por:

$$bel(x_t) = p(x_t | z_{1:t}, u_{1:t})$$

Essa é uma representação da distribuição de probabilidade posterior ou *belief* posterior sobre o estado \(x_t\) no tempo \(t\) condicionada por todas as medidas passadas \(z_{1:t}\) e todos os controles \(u_{1:t}\). Em nosso estudo, o cálculo de uma *belief* posterior antes de incorporar \(z_t\) somente após a execução de um controle \(u_t\) será representado por:

$$bel(x_t) = p(x_t | z_{1:t-1}, u_{1:t})$$

A representação \(bel(x_t)\) ​é definida como a predição no contexto da filtragem probabilística. A \(bel(x_t)\) indica a predição do estado no tempo \(t\) com base no estado posterior após a incorporação da medição no tempo \(t\). Nesse sentido, o cálculo de \(bel(x_t)\) a partir de \(bel(x_t)\) será chamado de correção ou atualização de medição.

Na implementação do algoritmo baseado no cálculo de \(bel(x_t)\) e \(bel(x_t)\) utiliza-se abordagem descrita na literatura como Filtro de Bayes (THRUN; BURGARD; DURRANT-WHYTE 2005) como se segue:

```markdown
Algoritmo Filtro de Bayes (bel(x_{t-1}), u_t, z_t):
    for all x_t faça
        bel(x_t) = ∫ p(x_t | u_t, x_{t-1}) bel(x_{t-1}) dx_{t-1}
    bel(x_t) = η p(z_t | x_t) bel(x_t)
    fimfor
    return bel(x_t)

