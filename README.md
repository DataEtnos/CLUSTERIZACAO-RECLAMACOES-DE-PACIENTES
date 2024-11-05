# Clusterização K-Means  - Cluster de reclamações 


O Objetivo deste projeto é clusterizar os operadores de saude de acordo com a quantidade de reclamações sobre o plano . 
isso pode incluir problemas com o atendimento , tratamento dos medicos no geral  e ate o que cobre o plano , 
aqui a clusterização vai nos  ajudar a identificar qual grupo tem mais problemas com reclamações
podendo ser criado um plano de ações das operações para a correções ou minimizar atritos  , e as operadoras com baixa reclamações podendo criar planos de fidelização dos clientes .

Neste projeto vou utilizar o dataframe de IGR da Agência Nacional de Saúde Suplementar (ANS).
O IGR é uma metrica calculada pela ANS que avalia o atendimento das operadoras de Saúde  aos beneficiários , é uma metrica isolada para cada Operador , 
que neste  projeto não vou considerar o igr, devido a  cada operador ter um banco de beneficiarios cadastrados muito variante e sendo isso parte da conta que faz o IGR (QTD_RECLAMAÇÕES / QTD_BENEFICIARIOS).
Este mesmo Dataframe se encontra no site dados.gov/br .


Apos verificar toda parte de limpeza de dados ( verificação de dados duplicados, nulos , quantidade de linhas do data frame ).
fiz algumas estruturação de dados ja pensando no modelo K-Means ( retirei o IGR apenas do modelo de Kmeans , mas manterei ele no dataframe fina, por isso fiz a troca da virgula pelo ponto na metrica IGR) ,
Foquei as analises do  K-means apenas nas operadoras de porte maior, por isso fiz 2 copias do df . 
a primeira copia vai conter todas as transformações e limpeza ,  a segunda vai conter apenas o o grupo de porte grande das operadoras , também fiz a retirada das operaadoras que não contem valores de reclamações .


apos a retirada das colunas que não usarei no k-means focando apenas na quantidade de reclamações e base de clientes.
verifiquei como estão  os percentil dos dados para ter uma ideia de como esta a distribuição dos dados , media , max contagem do dados com df.describe()

imagem -  describe

![describe](https://github.com/user-attachments/assets/73fa64b7-5d97-4b51-bd2a-d89a13d5687f)



imagem - boxplot - sem normalizar os dados
![bloxplot -  sem normalizar](https://github.com/user-attachments/assets/10bb4e07-f531-4913-b7b5-ff5ba4b86eca)


Observando os dados noto que preciso fazer uma normalização do mesmo com min-max-scaller,isso faz com que os dados fiquem na escala de 0 - 1 ,  verifico como ficou a distribuição dos dados com um grafico de boxplot. 

imagem -  boxplot
![bloxplot normalizado](https://github.com/user-attachments/assets/e943b229-d545-415e-aa95-dce71fb353f8)




Com o grafico de  cotovelo verifico em quantos cluster vou dividir os dados do df, eu fico com a sugestão do modelo de 4 grupos , porem pode ser quebrado em mais grupos , mais isso traria um pouco mais de complexidade na hora de subjulgar os operadores .
![cotovelo](https://github.com/user-attachments/assets/2264d14c-1123-4039-bc42-3ba6c417528f)


Em seguida, utilizo um gráfico de barras para visualizar os centróides de cada cluster, o que me permite ter uma ideia de como a clusterização está organizada. Com essa visualização, posso identificar os grupos que apresentam uma quantidade menor de reclamações (QTD_RECLAMACOES) e, para esses clusters, aplicar uma estratégia de fidelização, focando em manter a satisfação dos clientes. Por outro lado, nos clusters com alto volume de reclamações, priorizo o ajuste de problemas operacionais. Essa abordagem permite que eu verifique os valores dos centróides para cada variável, facilitando a análise detalhada sobre as causas das reclamações e ajudando a definir ações mais específicas para cada grupo


imagem - grafico de barra de cada cluster.

![grafico de barra](https://github.com/user-attachments/assets/158a6ded-5ba7-442b-b54f-f225ea121858)




É interessante ver como esta cada comparados ao outro grupos, plotei um grafico scatterplot que nos ajuda a verificar a posição do centroíde no grafico a estrela negra é onde esta o centroide de cada cluster

![cluster de reclamações](https://github.com/user-attachments/assets/a490defa-ddc4-44c1-802e-14492cccfe60)


feito fiz apenas o ajuste dos cluster no dataframe para sabermos quais as operadoras e em quais cluster cada operadora ficou .

é uma tabela bem grande de verificação, esse mesma tecnica pode ser aplicada analises de produtos , segmentação de clientes, pode ser usada como uma forma alternativa de definir a curva ABC nas cadeias logisticas e em uma outra infinidades de questões. 


para verificar de forma um pouco mais rapida e batendo agora com o IGR  consigo verificar que o IGR  acima de 100 ficaram os cluster mais alto no caso o cluster 1 , o que valida a clusterização ja que quanto maior for o IGR mais reclamações aquelas unidades agrupadas receberam .

imagem - grafico de barra.





Etnos De Jesus Santos 
Analista De Dados.
