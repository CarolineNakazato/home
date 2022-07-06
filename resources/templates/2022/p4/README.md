# Projeto 4 – Classificação de lesões de substância branca no Lúpus

O objetivo geral do projeto é, a partir de uma classificador treinado em imagens de ressonância do cérebro para diferenciar lesões isquêmicas e desmielinizantes, identificar qual a etiologia mais provável das lesões presentes em pacientes de Lúpus Eritematoso Sistêmico (LES).

# Modelo Relatório Final de Projeto P4

# Projeto Classificação de lesões de substância branca no Lúpus
# Project Classification of white matter lesions in lupus

# Apresentação

O presente projeto foi originado no contexto das atividades da disciplina de pós-graduação [*Ciência e Visualização de Dados em Saúde*](https://ds4h.org), oferecida no primeiro semestre de 2022, na Unicamp.


> | CAROLINE NAKAZATO  | 168913  | Computação|

# Introdução
> Apresentação de forma resumida do problema (contexto) e a pergunta que se quer responder.

## Ferramentas
> Listagem das ferramentas utilizadas (na forma de itens).
* Google Colab
* ython syntax
* Pandas library for data frame
* Support vector Machine(svm) from sklearn (a.k.a scikit-learn) library
* GridSearchCV
* skimage library for reading the image
* matplotlib for visualization purpose

## Preparo e uso dos dados
Todas as imagens foram  redimensionadas para um tamanho fixo.

# Metodologia
Para classificar imagens, estamos usando SVM. Scikit-learn é uma biblioteca de aprendizado de máquina de software livre para a linguagem de programação Python e a Support vector machine(SVM) está incluída no Scikit-learn.
Alguns dos principais parâmetros no SVM são:
→ Gamma : define até que ponto a influência de exemplos de treinamento individuais atinge valores que levam a resultados tendenciosos.

→ C : Controla o custo de erros de cálculo
C pequeno — torna BAIXO o custo da classificação incorreta
Grande C — torna o custo da classificação errada ALTO

→ Kernel : Os algoritmos SVM usam um conjunto de funções matemáticas que são definidas como o kernel.
Os tipos de Kernels são: Linear, RBF (Função de Base Radial), Kernel Polinomial

GridSearchCV
É uma função de biblioteca que é membro do pacote model_selection do sklearn. Ele ajuda a percorrer hiperparâmetros predefinidos e ajustar seu estimador (modelo) em seu conjunto de treinamento. Assim, no final, você pode selecionar os melhores parâmetros dos hiperparâmetros listados.

Processo
É uma das formas de aprendizado de máquina onde o modelo é treinado por dados de entrada e dados de saída esperados.
Para criar tal modelo, é necessário passar pelas seguintes fases:

1. Recebendo informações
2. Construção do modelo
3. Treinamento do modelo
4. Teste de modelo
5. Avaliação do modelo

Tomando entrada: 3 categorias diferentes de imagens (AVC, EM e SLE) são lidas e rotuladas como 0,1,2.

Como o SVM recebe entradas do mesmo tamanho, todas as imagens precisam ser redimensionadas para um tamanho fixo antes de serem inseridas no SVM. df é o quadro de dados criado usando pandas e xey são dados de entrada e saída, respectivamente

Construção do modelo: Neste caso de projeto, o modelo é uma máquina de vetores de suporte.
O algoritmo para construção do modelo é assim:

1. Crie um support vector classifier:
→ svc=svm.SVC()

2. Com a ajuda de GridSearchCV e grade de parâmetros, crie um modelo: 
→model=GridSearchCV(svc,parameters_grid)

Treinamento do modelo: Os dados são divididos em duas categorias: dados de treinamento e dados de teste. Os dados de treinamento são usados para treinar o modelo, enquanto os dados de teste são usados para testar o modelo treinado.
Para dividir os dados em treinamento e teste, é usado train_test_split() da biblioteca sklearn.
O modelo é treinado usando dados de treinamento dessa maneira
→ model.fit(dados_treinamento,saída_esperada)

>Resultados do treinamento do classificador
>
>Usei o GridSearchCV para descobrir os melhores parâmetros para o SVM classificar as imagens e medir a precisão do modelo.
>O melhores paramêtros encontrados pelo GrindSearchCV foram: {'C': 10, 'gamma': 0.0001, 'kernel': 'rbf'}
>
![alt text](https://github.com/CarolineNakazato/home/blob/master/resources/templates/2022/p4/p4.2.png)
>
> Tabela 1: Métricas de avaliação do gridsearch. A coluna "rank_test_score classifica todas as combinações de parâmetros pelos valores de "mean_test_score"
>
![alt text](https://github.com/CarolineNakazato/home/blob/master/resources/templates/2022/p4/p4.png)
>
> Tabela 2: Comparação de amostra dos dados presvistos com os dados reais
>
![alt text](https://github.com/CarolineNakazato/home/blob/master/resources/templates/2022/p4/matriz%20de%20confusao.png)
>
> Tabela 3: Matriz de confusão
>
> A tabela 3 que mostra as frequências de classificação para cada classe do modelo.
> Verdadeiro pode ocorrer de duas formas: Verdadeiro positivo (true positive — TP) ocorre quando no conjunto real, a lesão que estamos buscando foi prevista corretamente e Falso verdadeiro (true negative — TN) ocorre quando no conjunto real, a lesão que não estamos buscando prever foi prevista corretamente.
> Já o falso positivo (false positive — FP): ocorre quando no conjunto real, o tipo da lesão que estamos buscando prever foi prevista incorretamente e o falso negativo (false negative — FN) ocorre quando no conjunto real, a lesão que não estamos buscando prever foi prevista incorretamente. 
>
> Assim, o modelo:
>
> Previu AVC 28 vezes corretamente;
> Previu EM 28 vezes corretamente;
> Previu SLE 24 vezes corretamente;
> Previu EM 2 vez incorretamente, quando na realidade era AVC;
>
> A seguir, analisaremos algumas informações úteis que podemos tirar da matriz de condusão.
>
![alt text](https://github.com/CarolineNakazato/home/blob/master/resources/templates/2022/p4/p4.3.png)
>
> Tabela 5: Tabela de métricas do modelo.
>
> * Acurácia: revela quanto o meu modelo acertou das previsões possíveis. No contexto acima, nosso modelo teve uma acurácia de 97.5609756097561%. É a razão entre o somatório das previsões corretas (verdadeiros positivos com verdadeiros negativos) sobre o somatório das previsões.
>
> * Recall: mostra quão bom meu modelo é para prever positivos, sendo positivo entendido como a classe que se quer prever. É definido como a razão entre verdadeiros positivos sobre a soma de verdadeiros positivos com negativos falsos.
>
> * Precisão: é a proporção de identificações positivas foi realmente correta. Em outras palavras, o qual bem meu modelo trabalhou.
>
>* F-score: Já o f-score nos mostra o balanço entre a precisão e o recall de nosso modelo. 
>
# Resultados Obtidos e Discussão
>
![alt text](https://github.com/CarolineNakazato/home/blob/master/resources/templates/2022/p4/p4.4.png)
>
> Imagem 1: Predição de uma lesão de SLE feita corretamente.
>
![alt text](https://github.com/CarolineNakazato/home/blob/master/resources/templates/2022/p4/p4.7.png)
>
> Imagem 2: Predição de uma lesão de AVC feita incorretamente.
>
> Quando o modelo erra ele aprende com seu erro e os corrige e não repete o mesmo erro novamente.
>
# Conclusão
>
![alt text](https://github.com/CarolineNakazato/home/blob/master/resources/templates/2022/p4/p4.5.png)
>
> Imagem 3: Gráfico AUC ROC.
>
> Um gráfico AUC ROC (Area Under the Curve Receiver Operating Characteristics) é usado para visualizar o desempenho de um modelo entre sensibilidade e especificidade. A sensibilidade refere-se à capacidade de identificar corretamente as entradas que se enquadram no tipo correto da lesão. A especificidade refere-se à capacidade de identificar corretamente as entradas que se enquadram em um verdadeiro negativo (TN) . Dito de outra forma, um gráfico AUC ROC identifica quão bem o modelo é capaz de distinguir entre as classes.
> Uma pontuação AUC de 1 significa que o modelo pode distinguir com precisão entre as lesões 100% das vezes. Uma pontuação de 0,5 significa que o modelo não pode determinar entre os tipo de lesão, o que não ocorreu neste modelo. A curva ROC é o gráfico da taxa de verdadeiros positivos do modelo em relação à taxa de falsos positivos.
> Portanto podemos concluir que o modelo consegue distinguir muito bem SLE dos outros 2 tipos de lesões (AVC e EM), porem ainda possui dificuldade em distinguir entre as lesões AVC e EM.
>
> Um dos principais desafios foi interpretar os dados encontrados e gerar gráficospara 3 classes.
>
> Principais lições aprendidas.
>
> Trabalhos Futuros:
> Poderia ser feito normalização, uso das máscaras e outros pré-processamentos, uma melhor divisão dos dados de treino e dos dados de teste e também seria interessante utilizar de outros métodos de classifição para observar seus desempenho em relação a acurácia e ao tempo de processamento.


# Referências Bibliográficas
> https://scikit-learn.org/stable/modules/svm.html
> https://scikit-learn.org/stable/modules/generated/sklearn.model_selection.GridSearchCV.html
> https://scikit-learn.org/stable/modules/grid_search.html
