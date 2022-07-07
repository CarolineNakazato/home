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
> Disfunção executiva, com problemas de atenção, memória e aprendizado;
> * Transtornos de humor como depressão, TOC, paranoia e Transtorno de Déficit de Atenção e Hiperatividade
> * Dores de cabeça persistentes, enxaqueca que não respondem a analgésicos
> * Formas menos comuns de Lúpus no sistema nervoso são neuropatia craniana, convulsões e até meningites que requerem diagnóstico rápido e tratamento imediato.
> 
> Os mecanismos relacionados ao envolvimento neurológico no lúpus ainda não estão completamente esclarecidos. Entretanto, algumas evidências apontam lesões dos pequenos vasos cerebrais ou presença de anticorpos atingindo diretamente as conexões neuronais.
>
> O lúpus cerebral se manifestando com AVC pode sinalizar descontrole da doença. Note que nem todos os pacientes com LES apresentarão AVC; os pacientes com doença controlada e que cuidam da sua saúde conseguem minimizar essa chance.
> 
> O risco aumentado para AVC no lúpus está associado a:
> 
> * Inflamações em pequenos vasos cerebrais (vasculites)
> * Uso de corticoides em altas doses
> * Perfil lipídico alterado (colesterol e triglicerídeos elevados)
> * Hipertensão arterial e aterosclerose.
> 
> Esse conjunto de fatores pode contribuir com mecanismos variados para lesão isquêmica do sistema nervoso central. Os pacientes também podem apresentar risco aumentado de trombose de vasos cerebrais (trombose venosa cerebral).
>
> O termo síndrome desmielinizante descreve uma doença que afeta diretamente a bainha de mielina, com relativa preservação dos axônios. Clinicamente, a síndrome desmielinizante apresenta-se com sintomas variados, incluindo alteração sensorial, perda de visão e disartria (fala embolada).
> 
> Em pacientes com lúpus, o principal desafio consiste no diagnóstico diferencial com outras doenças desmielinizantes do sistema nervoso central incluindo a Esclerose Múltipla.
> 
> As características imunológicas de ambas as doenças, o padrão remitente-recorrente, as manifestações neurológicas e a presença de lesões da mielina podem dificultar sua distinção.
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
> Para classificar imagens, estamos usando SVM. Scikit-learn é uma biblioteca de aprendizado de máquina de software livre para a linguagem de programação Python e a Support vector machine(SVM) está incluída no Scikit-learn.
> 
> Alguns dos principais parâmetros no SVM são:
> 
> * Gamma : define até que ponto a influência de exemplos de treinamento individuais atinge valores que levam a resultados tendenciosos.
>
> * C : Controla o custo de erros de cálculo.
> 
> C pequeno — torna BAIXO o custo da classificação incorreta.
> 
> Grande C — torna o custo da classificação errada ALTO.
>
> * Kernel : Os algoritmos SVM usam um conjunto de funções matemáticas que são definidas como o kernel.
> 
> Os tipos de Kernels são: Linear, RBF (Função de Base Radial), Kernel Polinomial
>
> GridSearchCV
> 
> É uma função de biblioteca que é membro do pacote model_selection do sklearn. Ele ajuda a percorrer hiperparâmetros predefinidos e ajustar seu estimador (modelo) em seu conjunto de treinamento. Assim, no final, você pode selecionar os melhores parâmetros dos hiperparâmetros listados.
> 
> Processo
> 
> É uma das formas de aprendizado de máquina onde o modelo é treinado por dados de entrada e dados de saída esperados.
Para criar tal modelo, é necessário passar pelas seguintes fases:
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
> Tomando entrada: 2 categorias diferentes de imagens (AVC e EM) são lidas e rotuladas como 0,1 respectivamente.
> 
> Como o SVM recebe entradas do mesmo tamanho, todas as imagens precisam ser redimensionadas para um tamanho fixo antes de serem inseridas no SVM. df é o quadro de dados criado usando pandas e xey são dados de entrada e saída, respectivamente
> 
> Construção do modelo: Neste caso de projeto, o modelo é uma máquina de vetores de suporte.
> 
> O algoritmo para construção do modelo é assim:
> 
> 1. Crie um support vector classifier:
> 
> → svc=svm.SVC()
>
>
> 2. Com a ajuda de GridSearchCV e grade de parâmetros, crie um modelo: 
> 
> → model=GridSearchCV(svc,parameters_grid)
> 
> Treinamento do modelo: Os dados são divididos em duas categorias: dados de treinamento e dados de teste. Os dados de treinamento são usados para treinar o modelo, enquanto os dados de teste são usados para testar o modelo treinado.
> 
> Para dividir os dados em treinamento e teste, é usado train_test_split() da biblioteca sklearn.
> O modelo é treinado usando dados de treinamento dessa maneira
> 
> → model.fit(dados_treinamento,saída_esperada)
>
> Resultados do treinamento do classificador
>
> Usei o GridSearchCV para descobrir os melhores parâmetros para o SVM classificar as imagens e medir a precisão do modelo.
> 
> O melhores paramêtros encontrados pelo GrindSearchCV foram: {'C': 10, 'gamma': 0.0001, 'kernel': 'rbf'}
>
![alt text](https://github.com/CarolineNakazato/home/blob/master/resources/templates/2022/p4/p4.2.png)
>
> Tabela 1: Métricas de avaliação do gridsearch. 
> 
> A coluna "rank_test_score classifica todas as combinações de parâmetros pelos valores de "mean_test_score"
>
![alt text](https://github.com/CarolineNakazato/home/blob/master/resources/templates/2022/p4/p4.png)
>
> Tabela 2: Comparação de amostra dos dados previstos com os dados reais.
> 
> A Tabela faz a comparação dos dados previstos com os dados reais e as células em vermelho marcam 2 lesões que foram previstas de forma incorreta. Foi previsto como AVC, mas era EM.
> 
![alt text](https://github.com/CarolineNakazato/home/blob/master/resources/templates/2022/p4/matriz%20de%20confusao.png)
>
> Tabela 3: Matriz de confusão
>
> A tabela 3 que mostra as frequências de classificação para cada classe do modelo.
> 
> Verdadeiro pode ocorrer de duas formas: Verdadeiro positivo (true positive — TP) ocorre quando no conjunto real, a lesão que estamos buscando foi prevista corretamente e Falso verdadeiro (true negative — TN) ocorre quando no conjunto real, a lesão que não estamos buscando prever foi prevista corretamente.
>
> Já o falso positivo (false positive — FP): ocorre quando no conjunto real, o tipo da lesão que estamos buscando prever foi prevista incorretamente e o falso negativo (false negative — FN) ocorre quando no conjunto real, a lesão que não estamos buscando prever foi prevista incorretamente. 
>
> Assim, o modelo:
>
> Previu AVC 29 vezes corretamente;
> 
> Previu EM 28 vezes corretamente;
> 
> Previu EM 2 vez incorretamente, quando na realidade era AVC;
>  
>  
> A seguir, analisaremos algumas informações úteis que podemos tirar da matriz de condusão.
>
![alt text](https://github.com/CarolineNakazato/home/blob/master/resources/templates/2022/p4/p4.3.png)
>
> Tabela 5: Tabela de métricas do modelo.
>
> * Acurácia: revela quanto o meu modelo acertou das previsões possíveis. No contexto acima, nosso modelo teve uma acurácia de 96.61016949152543%. É a razão entre o somatório das previsões corretas (verdadeiros positivos com verdadeiros negativos) sobre o somatório das previsões.
>
> * Recall: mostra quão bom meu modelo é para prever positivos, sendo positivo entendido como a classe que se quer prever. É definido como a razão entre verdadeiros positivos sobre a soma de verdadeiros positivos com negativos falsos.
>
> * Precisão: é a proporção de identificações positivas foi realmente correta. Em outras palavras, o qual bem meu modelo trabalhou.
>
> * F-score: Já o f-score nos mostra o balanço entre a precisão e o recall de nosso modelo. 
>
> * Macro Average:  é calculada usando a média aritmética (também conhecida como média não ponderada) de todas as pontuações F1 por classe. Esse método trata todas as classes igualmente, independentemente de seus valores de suporte.
> 
> * Weighted Average: é calculada tomando a média de todas as pontuações da F1 por classe, considerando o suporte de cada classe.
> O suporte refere-se ao número de ocorrências reais da classe no conjunto de dados. Por exemplo, o valor de suporte de 1 em Boat significa que há apenas uma observação com um rótulo real de Boat.
> O ‘peso’ refere-se essencialmente à proporção do suporte de cada classe em relação à soma de todos os valores de suporte.
> Com a média ponderada, a média de saída teria levado em conta a contribuição de cada classe ponderada pelo número de exemplos dessa determinada classe.
> 
> Micro Average:  calcula uma pontuação F1 média global contando as somas dos verdadeiros positivos (TP), falsos negativos (FN) e falsos positivos (FP).
> Primeiro somamos os respectivos valores de TP, FP e FN em todas as classes e, em seguida, os conectamos à equação F1 para obter nossa pontuação micro F1.
> 
![alt text](https://github.com/CarolineNakazato/home/blob/master/resources/templates/2022/p4/p4.6.png)
>
> Imagem 1: Predição de uma lesão de EM feita corretamente.
>
![alt text](https://github.com/CarolineNakazato/home/blob/master/resources/templates/2022/p4/p4.7.png)
>
> Imagem 2: Predição de uma lesão de AVC feita incorretamente.
>
> Quando o modelo erra ele aprende com seu erro e os corrige e não repete o mesmo erro novamente.
>
# Resultados Obtidos e Discussão
>
![alt text](https://github.com/CarolineNakazato/home/blob/master/resources/templates/2022/p4/p4.4.png)
>
> Imagem 3: Predição de uma lesão de EM no paciente 600 com SLE.
> 
> Todos as imagens de pessoas com SLE tiverem apontaram para lesões EM.
> 
> A maioria com a seguinte porcentagem de probabilidade de cada tipo de lesão:
> * AVC = 21.43356181692244%
> * EM = 78.56643818307757%
> 
# Conclusão
>
![alt text](https://github.com/CarolineNakazato/home/blob/master/resources/templates/2022/p4/p4.5.png)
>
> Imagem 4: Gráfico AUC ROC.
>
> Um gráfico AUC ROC (Area Under the Curve Receiver Operating Characteristics) é usado para visualizar o desempenho de um modelo entre sensibilidade e especificidade. A sensibilidade refere-se à capacidade de identificar corretamente as entradas que se enquadram no tipo correto da lesão. A especificidade refere-se à capacidade de identificar corretamente as entradas que se enquadram em um verdadeiro negativo (TN) . Dito de outra forma, um gráfico AUC ROC identifica quão bem o modelo é capaz de distinguir entre as classes.
> 
> Uma pontuação AUC de 1 significa que o modelo pode distinguir com precisão entre as lesões 100% das vezes. Uma pontuação de 0,5 significa que o modelo não pode determinar entre os tipo de lesão, o que não ocorreu neste modelo. A curva ROC é o gráfico da taxa de verdadeiros positivos do modelo em relação à taxa de falsos positivos.
> 
> Portanto podemos concluir que o modelo consegue distinguir de forma razoável (AUC = 0.98) os tipos de lesões AVC e EM, porem ainda possui dificuldade não é exato.
>
> Um dos principais desafios foi interpretar os dados encontrados e entender o objetivo do projeto.
>
> Principais lições aprendidas.
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
