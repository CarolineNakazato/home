# Projeto 4 – Classificação de lesões de substância branca no Lúpus

> O objetivo geral do projeto é, a partir de uma classificador treinado em imagens de ressonância do cérebro para diferenciar lesões isquêmicas e desmielinizantes, identificar qual a etiologia mais provável das lesões presentes em pacientes de Lúpus Eritematoso Sistêmico (LES).

# Modelo Relatório Final de Projeto P4

# Projeto Classificação de lesões de substância branca no Lúpus
# Project Classification of white matter lesions in lupus

# Apresentação

> O presente projeto foi originado no contexto das atividades da disciplina de pós-graduação [*Ciência e Visualização de Dados em Saúde*](https://ds4h.org), oferecida no primeiro semestre de 2022, na Unicamp.
>
> | CAROLINE NAKAZATO  | 168913  | Computação|

# Introdução
> O Lúpus Eritematoso Sistêmico (LES ou apenas lúpus) é uma doença inflamatória crônica de origem autoimune, cujos sintomas podem surgir em diversos órgãos de forma lenta e progressiva (em meses) ou mais rapidamente (em semanas) e variam com fases de atividade e de remissão.
> 
> Pacientes com lúpus apresentam risco aumentado para doenças cerebrovasculares do tipo AVC, principalmente com lesões isquêmicas, que ocorrem em idades mais jovens do que o habitual.
> 
> Pesquisas feitas por Johnson e Richardson já definiram as manifestações do lúpus no sistema nervoso como parte integral da doença. As manifestações neuropsiquiátricas são as manifestações que envolvem alterações do humor ou comportamento e podem estar presentes em 50% dos pacientes. São elas:
>
> * Disfunção executiva, com problemas de atenção, memória e aprendizado;
> * Transtornos de humor como depressão, TOC, paranoia e Transtorno de Déficit de Atenção e Hiperatividade
> * Dores de cabeça persistentes, enxaqueca que não respondem a analgésicos
> * Formas menos comuns de Lúpus no sistema nervoso são neuropatia craniana, convulsões e até meningites que requerem diagnóstico rápido e tratamento imediato.
> 
> Os mecanismos relacionados ao envolvimento neurológico no lúpus ainda não estão completamente esclarecidos. Entretanto, algumas evidências apontam lesões dos pequenos vasos cerebrais ou presença de anticorpos atingindo diretamente as conexões neuronais.
>
> O lúpus cerebral se manifestando com AVC pode sinalizar descontrole da doença. Nem todos os pacientes com LES apresentarão AVC, os pacientes com doença controlada e que cuidam da sua saúde conseguem minimizar essa chance.
> 
> O risco aumentado para AVC no lúpus está associado a:
> 
> * Inflamações em pequenos vasos cerebrais (vasculites);
> * Uso de corticoides em altas doses;
> * Perfil lipídico alterado (colesterol e triglicerídeos elevados);
> * Hipertensão arterial e aterosclerose;
> 
> Esse conjunto de fatores pode contribuir com mecanismos variados para lesão isquêmica do sistema nervoso central. Os pacientes também podem apresentar risco aumentado de trombose de vasos cerebrais (trombose venosa cerebral).
>
> Já a síndrome desmielinizante descreve uma doença que afeta diretamente a bainha de mielina, com relativa preservação dos axônios. Clinicamente, a síndrome desmielinizante apresenta-se com sintomas variados, incluindo alteração sensorial, perda de visão e disartria (fala embolada).
> 
> Em pacientes com lúpus, o principal desafio consiste no diagnóstico diferencial com outras doenças desmielinizantes do sistema nervoso central incluindo a Esclerose Múltipla.
> 
> As características imunológicas de ambas as doenças, o padrão remitente-recorrente, as manifestações neurológicas e a presença de lesões da mielina podem dificultar sua distinção.
> 
> Não há cura para Lúpus Eritematoso Sistêmico, mas é possível controlar e conviver com ela com o acompanhamento médico regular.
>
> Globalmente, o Lúpus afeta, aproximadamente, 40 pessoas a cada 100 mil habitantes.
> 
> No Brasil, estima-se uma prevalência de 98 casos para cada 100.000 brasileiros, sendo, aproximadamente, 200 mil casos de Lúpus no país.
>
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
> Todas as imagens foram  redimensionadas para um tamanho fixo.

# Metodologia
> Scikit-learn é uma biblioteca de aprendizado de máquina de software livre para a linguagem de programação Python e a Support vector machine(SVM) está incluída no Scikit-learn. Para classificar as imagens, estamos usando SVM.
> 
> Alguns dos principais parâmetros no SVM são:
> 
> * Gamma : define até que ponto a influência dos exemplos de treinamento individuais atingem valores que levam a resultados tendenciosos.
>
> * C : Controla o custo de erros de cálculo.
> 
>   C baixo —> torna BAIXO o custo da classificação incorreta.
> 
>   C alto —> torna o custo da classificação errada ALTO.
>
> * Kernel : Os algoritmos SVM usam um conjunto de funções matemáticas que são definidas como o kernel.
> 
> Os tipos de Kernels são: Linear, RBF (Função de Base Radial), Kernel Polinomial.
>
> GridSearchCV é uma função de biblioteca que é faz parte do pacote model_selection do sklearn. A biblioteca ajuda a percorrer hiperparâmetros predefinidos e ajustar seu estimador (modelo) em seu conjunto de treinamento. Assim, no final, podemos selecionar os melhores parâmetros dos hiperparâmetros listados.
> 
> Processo:
> 
> É uma das formas de aprendizado de máquina onde o modelo é treinado por dados de entrada e dados de saída esperados.
> 
> Para criar tal modelo, é necessário passar pelas seguintes fases:
>
> 1. Recebendo informações;
> 
> 2. Construção do modelo;
> 
> 3. Treinamento do modelo;
> 
> 4. Teste de modelo;
> 
> 5. Avaliação do modelo;
> 
> Recebendo informações: 2 categorias diferentes de imagens de ressonância do cerébro, lesões isquêmicas (AVC - Acidente Vascular Cerebral) e desmielinizantes (EM - Esclerose Múltipla) são lidas e rotuladas como 0 e 1 respectivamente.
> 
> Como o SVM recebe apenas entradas do mesmo tamanho, todas as imagens precisam ser redimensionadas para um tamanho fixo antes de serem inseridas no SVM. 'df' é o quadro de dados criado usando pandas e x e y são dados de entrada e saída, respectivamente
> 
> Construção do modelo:
> 
> O algoritmo principal para construção do modelo é:
> 
> 1. Criar um support vector classifier:
> 
> → svc=svm.SVC()
>
>
> 2. Com a ajuda de GridSearchCV e grade de parâmetros foi criado um modelo: 
> 
> → model=GridSearchCV(svc,parameters_grid)
> 
> Treinamento do modelo: Os dados são divididos em duas categorias, dados de treinamento e dados de teste. Os dados de treinamento são usados para treinar o modelo, enquanto os dados de teste são usados para testar o modelo treinado.
> 
> Para dividir os dados em treinamento e teste, é usado train_test_split() da biblioteca sklearn.
> 
> O modelo é treinado usando dados de treinamento dessa maneira
> 
> → model.fit(dados_treinamento,saída_esperada)
>
> Foi usado o GridSearchCV para descobrir os melhores parâmetros para o SVM classificar as imagens e medir a precisão do modelo.
> 
> O melhores paramêtros encontrados pelo GrindSearchCV foram: {'C': 10, 'gamma': 0.0001, 'kernel': 'rbf'}
>
![alt text](https://github.com/CarolineNakazato/home/blob/master/resources/templates/2022/p4/p4.2.png)
>
> Tabela 1: Métricas de avaliação do gridsearch. 
> 
> A coluna 'params' da tabela 1 traz os possíveis valores principais paramêtros do SVM. A coluna 'rank_test_score' classifica todas as combinações de parâmetros pelos valores de 'mean_test_score'.
> A coluna principal é 'mean_test_score'. Esta é a média correta de precisão da classificação.
>
![alt text](https://github.com/CarolineNakazato/home/blob/master/resources/templates/2022/p4/p4.png)
>
> Tabela 2: Comparação de amostra dos dados previstos com os dados reais.
> 
> A Tabela 2 faz a comparação dos dados previstos com os dados reais e as células em vermelho marcam 2 lesões que foram previstas de forma incorreta. Foi previsto como lesões isquêmicas (AVC), mas era lesões desmielinizantes (EM).
> 
![alt text](https://github.com/CarolineNakazato/home/blob/master/resources/templates/2022/p4/matriz%20de%20confusao.png)
>
> Tabela 3: Matriz de confusão
>
> A tabela 3 que mostra as frequências de classificação para cada classe do modelo.
> 
> Verdadeiro positivo (VP ou TP) ocorre quando a lesão que estamos buscando foi prevista corretamente e Falso verdadeiro (VN ou TN) ocorre quando  a lesão que não estamos buscando prever foi prevista corretamente.
>
> Já o falso positivo (false positive — FP) ocorre quando  o tipo da lesão que estamos buscando prever foi prevista incorretamente e o falso negativo (false negative — FN) ocorre quando a lesão que não estamos buscando prever foi prevista incorretamente. 
>
> Assim, o modelo:
>
> Previu lesões de AVC 29 vezes corretamente;
> 
> Previu lesões de EM 28 vezes corretamente;
> 
> Previu leões de EM 2 vez incorretamente, quando na realidade eram lesões de AVC;
>  
>  
> A seguir, analisaremos algumas informações úteis que podemos tirar da matriz de confusão.
>
![alt text](https://github.com/CarolineNakazato/home/blob/master/resources/templates/2022/p4/p4.3.png)
>
> Tabela 5: Tabela de métricas do modelo.
>
> * Acurácia: revela quanto o modelo acertou das previsões. No contexto acima, o modelo teve uma acurácia de 96.61016949152543%. A acurácia é a razão entre o somatório das previsões corretas (verdadeiros positivos com verdadeiros negativos) sobre o somatório das previsões.
>
> * Recall: mostra quão bom o modelo é para prever positivos, sendo positivo entendido como a classe que se quer prever. É definido como a razão entre verdadeiros positivos sobre a soma de verdadeiros positivos com falsos negativos.
>
> * Precisão: é a proporção de identificações positivas foi realmente correta. Em outras palavras, o qual bem o modelo trabalhou.
>
> * F1-score: Já o f-score nos mostra o balanço entre a precisão e o recall do modelo. 
>
> * Macro Average:  é calculada usando a média aritmética de todas os f1-score por classe. Esse método trata todas as classes igualmente, independentemente de seus valores de suport.
> 
> * Weighted Average: é calculada tomando a média de todas os f1-score por classe, considerando o suporte de cada classe.
> 
> * Support: refere-se ao número de ocorrências reais da classe no conjunto de dados.
> 
> * Micro Average:  calcula uma média global do f1-score contando as somas dos verdadeiros positivos, falsos negativos e falsos positivos.
>
# Resultados Obtidos e Discussão
>
![alt text](https://github.com/CarolineNakazato/home/blob/master/resources/templates/2022/p4/p4.6.png)
>
> Imagem 1: Predição de uma lesão de EM feita corretamente.
> 
> A imagem 1 mostra a predição correta de uma lesão desmielinizantes (EM).
> 
![alt text](https://github.com/CarolineNakazato/home/blob/master/resources/templates/2022/p4/p4.7.png)
>
> Imagem 2: Predição de uma lesão de AVC feita incorretamente.
>
> Já a imagem 2 mostra um predição incorretta, o modelo previu que era uma lesão desmielinizantes (EM), porém era uma lesão isquêmicas (AVC). Quando o modelo erra ele aprende com seu erro, os corrige e não repete o mesmo erro novamente.
>
![alt text](https://github.com/CarolineNakazato/home/blob/master/resources/templates/2022/p4/p4.5.png)
>
> Imagem 3: Gráfico AUC ROC.
>
> Na imagem 3 temos um gráfico AUC ROC (Area Under the Curve Receiver Operating Characteristics) é usado para visualizar o desempenho de um modelo entre sensibilidade e especificidade. A sensibilidade refere-se à capacidade de identificar corretamente as entradas que se enquadram no tipo correto da lesão. A especificidade refere-se à capacidade de identificar corretamente as entradas que se enquadram em um verdadeiro negativo. Dito de outra forma, um gráfico AUC ROC identifica quão bem o modelo é capaz de distinguir entre as classes.
> 
> Uma pontuação AUC de 1 significa que o modelo pode distinguir com precisão entre as lesões 100% das vezes. Uma pontuação de 0,5 significa que o modelo não pode determinar entre os tipo de lesão, o que não ocorreu neste modelo. A curva ROC é o gráfico da taxa de verdadeiros positivos do modelo em relação à taxa de falsos positivos.
> 
> Portanto podemos concluir que o modelo consegue distinguir de forma razoável (AUC = 0.94) os tipos de lesões de AVC e EM, porém ainda possui dificuldades e não é 100% preciso em sua previsão.
> 
![alt text](https://github.com/CarolineNakazato/home/blob/master/resources/templates/2022/p4/p4.4.png)
>
> Imagem 4: Predição de uma lesão de EM no paciente 600 com SLE.
> 
> Na imagem 4 podemos observar a predição do paciente 600 que possui Lúpus Eritematoso Sistêmico, o modelo concluiu que a lesão era do tipo desmielinizantes (EM).
> 
> Após analisarmos as imagens de ressonância do cérebro de 77 pacientes com Lúpus Eritematoso Sistêmico temos o seguinte histograma.
> 
![alt text](https://github.com/CarolineNakazato/home/blob/master/resources/templates/2022/p4/p4.8.png)
>
> Imagem 5: Histograma.
> 
> Como podemos analisar atravez do histograma todas as imagens de ressonância do cérebro de pacientes com SLE tiverem apontaram para lesões do tipo desmielinizantes (EM).
> 
> A maioria com a seguinte porcentagem de probabilidade de cada tipo de lesão:
> * AVC = 21.43356181692244%;
> * EM = 78.56643818307757%;
>
# Conclusão
>
> Podemos concluir atravez dos dados fornecidos desta amostra que a etiologia mais provável, possuindo Lúpus Eritematoso Sistêmico, são lesões desmielinizantes comparado a ter lesões isquêmicas.
> 
> Desafios encontrados: Um dos principais desafios foi interpretar os dados encontrados e entender o objetivo do projeto, além da parte técnica, falta de memória em disco, o que impossibilitou do modelo avaliar 100% as imagens do treinamento.
>
> Trabalhos Futuros: poderia ser feito normalização, uso das máscaras e outros pré-processamentos, uma melhor divisão dos dados de treino e dos dados de teste e também seria interessante utilizar de outros métodos de classifição para observar seus desempenho em relação a acurácia e ao tempo de processamento.


# Referências Bibliográficas
> https://scikit-learn.org/stable/modules/svm.html
> 
> https://scikit-learn.org/stable/modules/generated/sklearn.model_selection.GridSearchCV.html
> 
> JOHNSON, RICHARD T. M.D.1; RICHARDSON, EDWARD P. M.D.2; THE NEUROLOGICAL MANIFESTATIONS OF SYSTEMIC LUPUS ERYTHEMATOSUS, https://journals.lww.com/md-journal/Citation/1968/07000/The_Neurological_Manifestations_of_Systemic_Lupus.2.aspx
> 
> https://scikit-learn.org/stable/modules/grid_search.html
