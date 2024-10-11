# IAprevisao_jornadapy
IA de previsão modelos arvore de decisões e vizinhos conhecidos


bibliotecas: pandas | sklearn (scikit-learn)

ler tabela e atribuir a variavel >> tabela = pd.read_csv("")
print (tabela)   exibir tabela em arqui ipynb >> display()

display(tabela.info()) >> informações sobre a planilha entre elas index Dtype and columns non-null values e memoria usada.

Após importar bibliotecas, abrir o banco de dados, e se necessario fazer o tratamento dos dados. Iremos codigicar as colunas transformando os dtype object em número para que possa ser interpretado pela IA. >> LabelEncoder

utilizaremos sklearn

from sklearn.preprocessing import labelencoder

o codificador irá aplicar o label encoder

codificador = LabelEncoder()


tabela ["profissao"] = codificador.fit_transform(tabela["profissao"])

a coluna profissao recebe o valor codificado obtido  através de codificador.fit_transform na coluna ["profissão"]
#

#
Por convenção a base de dados é dividida em x - para os dados a serem utilizados e y - para os dados a serem previstos 
Nesse caso, 

y = ["score_credito"]

x = tabela.drop(columns ["id_cliente"] , ["score_credito"])

x recebe toda a tabela removendo através do metodo drop as colunas ["id_cliente"] para remover dado inútil, e ["score_credito"] para não repetir a coluna que será prevista
#

Agora vamor separar a base de dados em  dados para treino e dados para teste. Nesse sentido, os eixos ficarão divididos em x_treino, x_teste, y_treino, y_teste.

Para isso podemos usar o metodo train_test_split que receberá x e y e irá dividir os dados de treino e de teste criando x_treino,x_teste,y_treino,y_teste.

A divisão recomendada é de 60 ~ 80% para treino e 20~40% para teste. Podendo ser informado no metodo train_test_split (x,y,testsize=0.3)

criando a IA em tres passoas #1 importar #2 criar #3 treinar
#
importar a classe RandomForestClassifier do módulo sklearn.ensemble   >> arvore de decisões (Classifier previsão de texo // Regressor previsão de números)
e a classe KneighborsClassifer do módulo sklearn.neighbors            >> vizinhos próximos 


from sklearn.ensemble import RandomForestClassifier
from sklear.neighbors import KRandomForestClassifier

#
modelo_arvore = RandomForestClassifier()
modelo_vizinhos= KRandomForetClassifier()

# 
x_treino e y_treino para treinar a IA

modelo_arvore.fit(x_treino, y_treino)
modelo_vizinho.fit(x_treino,y_treino)

Para testar >>

x_teste para fazer as previsões (variaveis recebem as previsões)


previsao_arvore = modelo_arvore.predict(x_teste)
previsao_vizinhos = modelo_vizinhos.predict(x_teste)


y_teste para comparar as respostas e quantificar o valor de acurácia (sera comparado y_teste com a variavel de previsão)

Analisando a acurácia

from sklearn.metrics import accuracy_score

display (accuracy_score(y_teste, previsao_arvore))

display(accuracy_score(previsao_vizinhos))










