<h1 align = 'center'> CLUSTERING💠</h1>

![Badge em Desenvolvimento](https://img.shields.io/static/v1?label=STATUS&message=CONSTRUINDO&color=<COLOR>)

<h2 align = 'left'>Informações Básicas</h2>

* **O que é:**

  Clustering (tradução livre: agrupamento) é uma técnica de aprendizado não supervisionado. Sua função é separar os dados em diferentes grupos por similaridade,
e com isso gerar os rótulos (labels) que os dados não tem. 

* **Quando usar:**

  Utiliza quando os dados que temos não possuem a variável alvo (target) que separa os dados em grupos específicos, os quais queremos estudar.
Neste sentido, aplica-se técnicas matemáticas e de probabilidade para separar os dados em grupos, e assim busca-se compreender cada grupo.

* **Exemplos de Uso:**
1. Recomendador: Com dados de opiniões, notas, tipos e afins, separa-se em grupos clientes que tenham opiniões semelhantes para recomendar algo (como músicas) 
que o grupo gosta. 
2. Em bancos: Usando dados dos clientes pode-se separar eles em grupos afim de estudar diferentes comportamentos dos grupos e tomar diferentes ações para cada um.


<h2 align = 'left'> Biblioteca Utilizada</h2>

A biblioteca mais utiliza é a [Scikit-Learn](https://scikit-learn.org/stable/modules/clustering.html#clustering). Dentro desta utiliza-se vários módulos e funções.
Abaixo deixarei o link para cada momento. 

<h2 align = 'left'>Como Realizar um Clustering</h2>

Um dos módulos utilizado para realizar a separação dos grupos é o [Kmeans](https://scikit-learn.org/stable/modules/clustering.html#k-means)
(leia a documentação para mais informações). Nele você deve colocar o número de grupos desejados. Porém, antes de realizar o clustering deverão ser feitos 
alguns passos:

<h3 align = 'left'>Análise dos Dados</h3>

Para realizar um bom aprendizado é preciso ter bastantes dados, quanto mais melhor. O dataset não pode conter variáveis Null ou NaN, caso tenha pode utilizar o comando
fillna() do Pandas pela média ou mediana. Estude os dados para tomar a decisão. 

<h3 align = 'left'>Normalização dos Dados</h3>

**1-Por que normalizar os dados?** 

Todos os dados se distribuem de valores máximos a valores mínimos, que podem ter qualquer valor. E diferentes categorias tem diferentes valores máximos e mínimos. 
*O objetivo de normalizar os dados é trazer todas as categorias para a mesma faixa de máximos e mínimo (0 a 1), criando um padrão*. 
**É importante pois as bibliotecas funcionam neste padrão, e garante confiabilidade e precisão.**

**2-Como desnormalizar?** 

Não é preciso desnormalizar. Bastar criar um array com os dados normalizados e usar este array para treinar o modelo. Com o modelo treinado você terá as 
labels dos clusters criados, e poderá adicionar as labels no dataset com os valores originais. 

O Scikit-learn possui módulo para normalizar, [NORMALIZER](https://scikit-learn.org/stable/modules/generated/sklearn.preprocessing.Normalizer.html). Este é um passo
do preprocessamento, e novamente existem mais módulos sobre em 
[sklean.preprocessing](https://scikit-learn.org/stable/modules/classes.html#module-sklearn.preprocessing).

**Com esses passo feitos pode seguir para a realização do clustering (fit_predict)**

<h2 align = 'left'>Como Validar um Clustering: Métrica</h2>

Existem coeficientes que calculam a similaridade e a diferença entre os grupos criados. Esses coeficientes são encontrados em
[metrics](https://scikit-learn.org/stable/modules/classes.html#module-sklearn.metrics), e alguns usados são detalhados abaixo.

<h3 align = 'left'>Coeficientes</h3>

<font color='blue' > 1- Coeficiente de Silhouette </font>: É um coeficiente usado na validação dos cluster usando a distância entre amostras 
do mesmo grupo e amostras entre grupos para o cálculo. Em geral, **queremos um valor positivo e próximos de 1, o 
qual indica que os grupos estão mais distantes um do outro e agrupados entre seus membros**

<font color='blue' > 2- Coeficiente de Davis Bouldin </font>: Calcula a similaridade entre clusters distintos. 
Pra isso é usado a distância entre os clusters e o tamanho médio deles. **O esperado é um valor próximo a zero (indicando zero similaridade).**

<font color='blue' > 3- Coeficiente de Calinsk - Harabasz </font>: Calcula a similaridade de um ponto nos dados com o próprio cluster a qual ele pertence. 
Assim **Esperamos que seja o maior valor possível (indicará alta similaridade)**.

<h3 align = 'left'>Formas de Validação</h3>

**Objetivo da Validação:** Verificar se seus clusters são válidos e se são os melhores a se utilizar. 

1. Validação Relativa: Altera-se a quantidade de clusters e analisa como altera os valores dos coeficientes.
2. Validação Por Comparação: Coloca-se valores aleatorios e observa os valores dos coeficientes. Este é um jeito "Dummy" e os valores do nosso clusters devem ser 
melhores que o Dummy.
3. Validação por Estabilidade: Realiza-se splits randômicos no dataset, usamos esses para verificar os coeficientes. Esperamos aqui que os coeficientes não se 
alterem tanto para indicar estabilidade.
4. Validação por Estatística: Usamos os valores estatísticos dos clustes para cada variável afim de verificar como cada cluster se comporta. Esperamos resultados 
diferentes para cada cluster.
5. Validação por Visualização: Realizamos um gráfico que mostre a variável escolhida e que separe por cor cada cluster. Este é um jeito que pode ser enganoso, já que
como tem muitas variáveis e mais de 1 clusters os olhos podem enganar.

<h2 align = 'left'>Compreender os Clusters</h2>

<h3 align = 'left'>Algumas Técnicas</h3>

Compreender os clusters significa entender quais as diferenças entre eles. Exemplo: qual grupo gasta mais, qual tem mais crédito. 

1. Retirar variáveis: O Kmeans calcula os centróides de cada clusters. Podemos utilizar a variação dos centróides para cada variável afim de verificar se aquela 
variável é significativa, ou seja, se há variação ou não. Dado nossa opção de escolha podemo retirar algumas variáveis no momento de validar nossos clusters. 
Foi feito no projeto de CLUSTER_interpretacao e usou como critério possuir variação acima das 2 casa decimal. 



