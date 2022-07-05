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

> Descreva o pipeline de pré-processamento dos dados:
* normalização (se houver)
* outros processamentos
* uso das máscaras (se houver)
* extração de atributos (se houver)
* seleção de atributos (se houver)


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

Usei o GridSearchCV para descobrir os melhores parâmetros para o SVM classificar as imagens e medir a precisão do modelo.

Resultados do treinamento do classificador
![alt text](https://github.com/CarolineNakazato/home/blob/master/resources/templates/2022/p4/p4.png)
>
> Justificar as escolhas.
> Esta parte do relatório pode ser copiada da Atividade 11, caso o grupo opte por usar o SVM já treinado.

# Resultados Obtidos e Discussão
> Esta seção deve apresentar o resultado de predição das lesões de LES usando o classificador treinado. Também deve tentar explicar quais os atributos relevantes usados na classificação obtida
> * apresente os resultados de forma quantitativa e qualitativa
> * tenha em mente que quem irá ler o relatório é uma equipe multidisciplinar. Descreva questões técnicas, mas também a intuição por trás delas.

# Conclusão
> Destacar as principais conclusões obtidas no desenvolvimento do projeto.
>
> Destacar os principais desafios enfrentados.
>
> Principais lições aprendidas.
>
> Trabalhos Futuros:
> * o que poderia ser melhorado se houvesse mais tempo?

# Referências Bibliográficas
> https://scikit-learn.org/stable/modules/svm.html
> https://scikit-learn.org/stable/modules/generated/sklearn.model_selection.GridSearchCV.html
> https://scikit-learn.org/stable/modules/grid_search.html
