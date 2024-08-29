# Robótica Probabilistica 

Esse repositório é focado em automação estocástica.

# Robótica Probabilística: Automação Estocástica com Arduino

## Introdução

A robótica é uma ciência que observa e manipula o ambiente físico por meio de aparelhos de controle e computadores. Conforme Thrun, Burgard e Durrant-Whyte (2005), as possibilidades de aplicação da robótica vão desde a indústria, com braços robóticos, até a medicina, com manipuladores que auxiliam cirurgiões, e também na análise de ambientes hostis, por meio de robôs tipo drone e/ou andarilhos. Nesse contexto, deve-se destacar que a atuação dos robôs é condicionada pelo hardware, como motores que podem apresentar incerteza e erro devido a ruído de controle, desgaste ou falha mecânica.

O software também deve ser considerado, uma vez que todos os programas que gerenciam o hardware e o funcionamento do robô são modelos que representam o mundo de maneira aproximada. De acordo com Ross (2014a), modelos são aproximações do mundo real que representam alguma situação ou processo físico. Dessa forma, o modelo pode estar suscetível a problemas como a falta de parâmetros necessários para o funcionamento do robô em determinado ambiente e a incerteza dos dados medidos quando o robô enfrenta situações com variações estocásticas, dificultando sua adaptação. Além disso, o próprio funcionamento do algoritmo pode ser afetado por problemas de implementação computacional, como excesso de processamento e limitações de memória.

O nível de incerteza no funcionamento do robô depende da aplicação. Nesse sentido, conforme Thrun, Burgard e Durrant-Whyte (2005), a robótica probabilística é a área que tem como objetivo analisar dados dos sensores do robô e construir algoritmos robustos baseados em Estatística e Probabilidade, que contemplem as incertezas relacionadas aos dados, ao software, ao hardware ou ao ambiente. O intuito é possibilitar a construção e utilização de robôs confiáveis para as mais variadas tarefas que a sociedade possa necessitar, como o uso de robôs em ambientes de risco para seres humanos.

Na construção e nos testes com robôs, é importante ter uma plataforma de prototipagem, ou seja, uma plataforma de hardware e software para a implementação de modelos e algoritmos em protótipos de robôs. A plataforma Arduino se destaca por fornecer uma plataforma livre. A construção de hardware e software no Arduino, bem como sua documentação, são abertas, permitindo que os desenvolvedores analisem o funcionamento dos protótipos sem restrições de licença (Mitchell, 2012). Além disso, seus componentes são de fácil acesso, o que torna a plataforma favorável para a análise de dados e a implementação de modelos, garantindo a fidelidade dos dados.

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

Na escolha da(s) linguagem(s), será utilizada, principalmente, a linguagem C/C++ padrão da plataforma Arduino, devido à sua proximidade com o hardware, o que permite o controle de pinos de entrada e saída, temporizadores, interrupções e outros recursos do compilador (Mitchell, 2012). Essa linguagem também permite um uso eficiente da memória, o que é importante, uma vez que o microcontrolador do Arduino possui uma quantidade limitada de memória disponível. Além disso, por permitir programação orientada a objetos, facilita a codificação de estruturas complexas e a reutilização de código (Stroustrup, 2013).

Para a análise dos dados, serão utilizadas as linguagens R ou Python, devido à facilidade de codificação e às bibliotecas disponíveis para análise de dados, plotagem e estatística em geral, conforme discutido por Wickham (2016) e VanderPlas (2016).

### Conceitos básicos de probabilidade utilizados na robótica probabilística

Nesta seção, serão abordados os conceitos básicos de probabilidade utilizados em robótica probabilística. Nesse sentido, serão utilizados conceitos abordados por Ross (2014a). Em robótica probabilística, quantidades como medidas de sensores, controles, estados do robô e o ambiente são modeladas por variáveis aleatórias. Uma variável aleatória pode assumir múltiplos valores que estão de acordo com leis de probabilidade específicas. Nesse sentido, a inferência probabilística é o processo de calcular essas leis, que derivam de outras variáveis aleatórias e dos dados observados. Assim, definimos:

$$ p(X=x) $$

Sendo \(X\) uma variável aleatória, a probabilidade de \(X\) assumir um valor \(x\) é \(P(X = x)\). No caso de variáveis discretas, o somatório das probabilidades de todos os possíveis valores de \(X\) é igual a 1, ou seja,

$$
\sum_x P(X=x)=1
$$

No caso contínuo, a integral da função de densidade de probabilidade é igual a 1, ou seja,

$$
\int p(x) \, dx = 1
$$

No estudo probabilístico, há o conceito de probabilidade conjunta, que descreve a probabilidade das variáveis aleatórias \(X\) e \(Y\) assumirem os valores \(x\) e \(y\), respectivamente. Esse conceito é dado por:

$$
p(x,y)=p(X=x \text{ e } Y=y)
$$

No caso de variáveis independentes:

$$
p(x,y)=p(x)p(y)
$$

Frequentemente, as variáveis aleatórias têm informações sobre outras variáveis. Por exemplo, os sensores podem fornecer informações importantes sobre o estado do robô para a modelagem probabilística. Nesse sentido, é necessário utilizar a probabilidade condicional para relacionar as variáveis,

$$
p(x \mid y)=\frac{p(X=x \text{ e } Y=y)}{p(Y=y)}=p(x)
$$

Os axiomas de probabilidade e a probabilidade condicional permitem determinar os resultados da probabilidade total dados por:

$$
p(x)=\sum_y p(x \mid y) \, p(y) \quad \text{(caso discreto)}
$$

$$
p(x)=\int p(x \mid y) \, p(y) \, dy \quad \text{(caso contínuo)}
$$

Os resultados da probabilidade total permitem a formulação de importantes equações para a robótica probabilística, conhecidas como regras de Bayes, apresentadas da seguinte forma: para \( p(y) >0 \), tem-se:

$$
p(x \mid y)= \frac{p(y \mid x) \, p(x)}{p(y)} = \frac{p(y \mid x) \, p(x)}{\sum_{x'} p(y \mid x') \, p(x')}
$$

$$
p(x \mid y)= \frac{p(y \mid x) \, p(x)}{p(y)} = \frac{p(y \mid x) \, p(x)}{\int p(y \mid x') \, p(x') \, dx'}
$$

### Cadeias de Markov

A robótica probabilística é fortemente baseada no conceito de cadeias de Markov. Para modelar a mudança de estado do ambiente, utilizam-se modelos baseados em cadeias de Markov. A cadeia de Markov pode ser definida como um processo estocástico, em que a probabilidade de transição para o próximo estado não depende dos estados anteriores. Os modelos de Markov são definidos por:

$$
P(x_t \mid x_{t-1}, x_{t-2}, \dots, x_0)=P(x_t \mid x_{t-1})
$$

Os estados são discretos, e a sequência de estados é uma sequência de variáveis aleatórias. Dessa forma, a distribuição de probabilidade de cada estado futuro depende apenas do estado atual. A observação dos estados, por meio das transições e suas probabilidades, define o comportamento do sistema ao longo do tempo.

Um exemplo de modelagem de cadeia de Markov é o modelo oculto de Markov, utilizado para modelar situações em que o sistema pode estar em um dos vários estados ocultos que não podem ser diretamente observados. Nesse modelo, os estados ocultos são modelados por variáveis estocásticas, e o sistema observa saídas com base nessas variáveis.

A Robótica Probabilística utiliza o conceito de cadeias de Markov para modelar e analisar o comportamento dos robôs em ambientes dinâmicos, onde o modelo estocástico é utilizado para descrever as mudanças de estado e as incertezas associadas às medições dos sensores.

## Resultados Esperados

- Implementação de algoritmos probabilísticos que demonstrem a adaptação do robô a diferentes contextos e variáveis do ambiente.
- Análise de dados obtidos da plataforma Arduino para validação dos modelos probabilísticos propostos.
- Avaliação da eficiência da plataforma Arduino na prototipagem e estudo de robôs.
- Identificação de desafios e soluções na implementação de robôs probabilísticos em diferentes cenários e aplicações.

## Referências

- ROSS, Sheldon M. **Introduction to Probability Models**. 11. ed. San Diego: Academic Press, 2014a.
- MITCHELL, John C. **Programming Arduino: Getting Started with Sketches**. 2. ed. O'Reilly Media, 2012.
- STROUSTRUP, Bjarne. **The C++ Programming Language**. 4. ed. Addison-Wesley, 2013.
- WICKHAM, Hadley. **R for Data Science**. O'Reilly Media, 2016.
- VANDERPLAS, Jake. **Python Data Science Handbook: Essential Tools for Working with Data**. O'Reilly Media, 2016.
- THRUN, Sebastian; BURGARD, Wolfram; DURRANT-WHYTE, Hugh. **Probabilistic Robotics**. Cambridge: MIT Press, 2005.

