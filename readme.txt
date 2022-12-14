# House Rocket - Análise de preços e recomendações de Portifolio

![icon](https://user-images.githubusercontent.com/42360197/207433028-735a3b18-1aa9-432f-9d16-6d2f027a0d64.png)

House Rocket é uma empresa fictícia que visa analisar dados de propriedades e realizar operações de compra e venda, maximizado o lucro e levando em conta:
* As condições do imóvel
* E a época do ano

O projeto em questão visa criar uma solução completa para análise do ponto de vista do CEO da empresa sobre quais são os melhores negócios disponíveis no mercado, incluindo visualizações, análise estatística descritiva, insights de negócio e recomendações de compra e venda.
(Empresa e Logo são fictícias)

# 1. Descrição - Questões de Negócio
Encontrar as melhores oportunidades de negócio: compra de casas em boas condições e com preços baixos, e venda desses imóveis adquiridos por um preço superior e justo. Os atributos dos imóveis, tais como localização, número de cômodos, áreas e datas de construção e reforma influenciam diretamente na sua atratividade e preço.
**1. Quais imóveis a empresa deve adquirir e por qual preço? **
**2. Para os imóveis adquiridos, quando é o melhor momento para vendê-los e por qual preço? **

# 2. Dataset e atributos
Originalmente baixado em <url>https://www.kaggle.com/harlfoxem/housesalesprediction/discussion/207885</url>. Definições dos atributos relevantes:

|    Atributo     |                         Descrição                            |
| :-------------: | :----------------------------------------------------------: |
|       id        |              Identificação única para cada imóvel            |
|      date       |               Data do anúncio de venda do imóvel             |
|      price      |                 Preço de venda atual do imóvel               |
|    bedrooms     |                      Número de quartos                       |
|    bathrooms    |                     Número de banheiros                      |
|   sqft_living   |    Medida em pés quadrados da área total interior do imóvel  |
|    sqft_lot     |        Medida em pés quadrados da área total do terreno      |
|     floors      |                 Número de andares do imóvel                  |
|   waterfront    |     Possui ou não frente para a água (0 = não e 1 = sim)     |
|      view       |   Indica a qualidade da vista da propriedade (0 = baixa e 4 = alta) |
|    condition    | Indica a qualidade das condições gerais da propriedade (0 = baixa e 5 = alta) |
|      grade      | Indica a qualidade da construção e o design do imóvel (1-3 = baixa, 4-10 = médio e 11-13 = alta) |
|  sqft_basement  |      Medida em pés quadrados da área total do porão/subsolo  |
|    yr_built     |                  Ano de construção do imóvel                 |
|  yr_renovated   |                Ano de reforma do imóvel                      |
|     zipcode     |                  CEP da localização do imóvel                |
|       lat       |                           Latitude                           |
|      long       |                          Longitude                           |
| sqft_livining15 | Medida em pés quadrados da área total interior de habitação para os 15 vizinhos mais próximo |
|   sqft_lot15    | Medida em pés quadrados da área total do terreno dos 15 vizinhos mais próximo |


# 3. Premissas do Negócio
As seguintes premissas foram adotadas para o dataset e o projeto como um todo:
- Imóveis com mais de 11 quartos foram considerados outliers e dessa forma. ignorados
- Na maioria das análises (exceto de evolução de preço ao longo do tempo), foi considerado somente o registro mais recente para cada propriedade, no caso dela ter múltiplas ocorrências em períodos distintos.
- Valores iguais a 0 (zero) significam que aquele atributo não está presente ou não é aplicável (ex.: não faz fronteira com a água, não sofreu reforma, não possui porão, etc.)

# 4. Planejamento da solução
Foram adotadas as seguintes etapas, que guiaram a evolução deste projeto:
1. Entendimento do Negócio
2. Importação dos dados (via Kaggle)
3. Limpeza e tratamento dos dados
4. EDA (Análise Exploratória de Dados) - criação de visualizações e tabelas
5. Elaboração de Insights de Negócio - hipóteses com possível valor para o negócio, a serem analisadas
6. Respostas dos Problemas de Negócio
7. Resultados e recomendações de compra e venda

# 5. Os principais Insights de Negócio
**Insights de negócio** são hipóteses que levam em conta uma afirmação, análise e comparação entre 2 ou mais variáveis, geração de conclusão através de gráficos e tabelas. Caso seja acionável (possível tomar decisões para beneficiar o negócio a partir dos encontrados), a hipótese se torna um *insight*.

| Hipótese                                                     | Resultado  | Sugestão de ação para o negócio                                        |
| ------------------------------------------------------------ | ---------- | ------------------------------------------------------------ |
| **H1** - Imóveis com vista para a água são em média 25% mais caros | Verdadeiro | Priorizar a compra de imóveis com vista para água caso estejam com preço favorável    |
| **H2** - Imóveis com frente para a água são cerca de 10% mais baratos quando vendidos no inverno ou outono | Verdadeiro      | Observar preços destes imóveis nessas estações do ano, pois podem ser mais em conta |
| **H3** - Imóveis com porão são cerca de 50% mais caros do que aqueles sem | Falso | O fato de ter porão é um atrativo considerável mas não tanto quanto se imaginava (somente 25%)    |
| **H4** - O maior crescimento do preço dos imóveis mês após mês no período observado é maior que 5% | Verdadeiro | Priorizar adquirir os imóveis nos meses em que há baixa de preços  |
| **H5** - Propriedades que foram construídas antes de 1955 e que sofreram reforma possuem preço acima de 20% acima daquelas que não foram reformadas ou que foram construídas em outro período | Verdadeiro      | Comprar imóveis antigos e que foram reformados, pois o preço de venda é cerca de 32% acima do que a média dos outros   |