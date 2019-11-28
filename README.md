# microdadosEnem_Deficit_Atencao
Análise dos Micro Dados dos alunos que fizeram o Enem nos anos de 2014 a 2018.

<h1>Análise Microdados ENEP</h1>
<h3>Análise dos Micro Dados dos alunos que fizeram o Enem nos anos de 2014 a 2018</h3>

Arquivos para Downloads: 

_2014_:http://download.inep.gov.br/microdados/microdados_enem2014.zip 
_2015_:http://download.inep.gov.br/microdados/microdados_enem2015.zip
_2016_:http://download.inep.gov.br/microdados/microdados_enem2016.zip
_2017_:http://download.inep.gov.br/microdados/microdados_enem2017.zip
_2018_:http://download.inep.gov.br/microdados/microdados_enem2018.zip

PS: todas as análises feitas na versão. Verifique se o mesmo está configurado no PATH: Control Panel\System and Security\System

<h2>Configurações Prévias do Python 3.8</h2>
<img src="https://user-images.githubusercontent.com/56441375/69769042-dddd7700-1161-11ea-8015-1ea16e932516.PNG"height="350" widht ="350">


<h3>Instalando as bibliotecas</h3> 
Iniciar + R: Abrirá uma tela de busca. Buscar por 'cmd' que o Prompt de Comando abrirá. 

Foram utilizadas as bibliotecas: 
<ul>
  <li>Upgrade do pip: pip install --upgrade pip.</li>
  <li>Jupyter: pip install jupyter</li>
  <li>Pandas: pip install pandas </li>
  <li>Numpy: pip install numpy</li>
</ul>

PS: digite ```jupyter notebook``` no prompt de comando para abrir o jupyter e crie um novo arquivo em ipynb 

<h3>Importação das bibliotecas no Jupyter</h3>

```
import pandas as pd
import matplotlib.pyplot as plt
import numpy as np

low_memory = False
``` 

Permite que não haja problemas referente a falta de memória do computador

<h3>Importação das Listas com as colunas de interesse</h3>

Lendo os arquivos csv
```
microdadosEnem2014 = pd.read_csv('MICRODADOS_ENEM_2014.csv', sep=',', encoding='ISO-8859-1', usecols = ['UF_RESIDENCIA', 'UF_PROVA', 'IN_DEFICIT_ATENCAO', 'NU_NOTA_REDACAO'])
microdadosEnem2015 = pd.read_csv('MICRODADOS_ENEM_2015.csv', sep=',', encoding='ISO-8859-1', usecols = ['SG_UF_RESIDENCIA', 'SG_UF_PROVA', 'IN_DEFICIT_ATENCAO', 'NU_NOTA_REDACAO'])
microdadosEnem2016 = pd.read_csv('MICRODADOS_ENEM_2016.csv', sep=';', encoding='ISO-8859-1', usecols = ['SG_UF_RESIDENCIA', 'SG_UF_PROVA', 'IN_DEFICIT_ATENCAO', 'NU_NOTA_REDACAO'])
microdadosEnem2017 = pd.read_csv('MICRODADOS_ENEM_2017.csv', sep=';', encoding='ISO-8859-1', usecols = ['SG_UF_RESIDENCIA', 'SG_UF_PROVA', 'IN_DEFICIT_ATENCAO', 'NU_NOTA_REDACAO'])
microdadosEnem2018 = pd.read_csv('MICRODADOS_ENEM_2018.csv', sep=';', encoding='ISO-8859-1', usecols = ['SG_UF_RESIDENCIA', 'SG_UF_PROVA', 'IN_DEFICIT_ATENCAO', 'NU_NOTA_REDACAO'])
```

Essa mesma leitura foi feita para os microdados do enem dos anos de 2015, 2016, 2017 e 2018. 

<h3>Variáveis para o Gráfico</h3>

```
anos = ['2014', '2015', '2016', '2017', '2018']
dados_por_ano = []
```

<h3>Consulta da informação necessária: Alunos com Défict de Atenção</h3> 

```
deficit2014 = microdadosEnem2014.query('(IN_DEFICIT_ATENCAO == 1)')['IN_DEFICIT_ATENCAO'].count()
deficit2015 = microdadosEnem2015.query('(IN_DEFICIT_ATENCAO == 1)')['IN_DEFICIT_ATENCAO'].count()
deficit2016 = microdadosEnem2016.query('(IN_DEFICIT_ATENCAO == 1)')['IN_DEFICIT_ATENCAO'].count()
deficit2017 = microdadosEnem2017.query('(IN_DEFICIT_ATENCAO == 1)')['IN_DEFICIT_ATENCAO'].count()
deficit2018 = microdadosEnem2018.query('(IN_DEFICIT_ATENCAO == 1)')['IN_DEFICIT_ATENCAO'].count()
```

Essa mesma leitura foi feita para todos os anos de estudo: 2014, 2015, 2016, 2017 e 2018.

As variáveis criadas foram:
<ul>
  <li>deficit2014</li>
  <li>deficit2015</li>
  <li>deficit2016</li>
  <li>deficit2017</li>
  <li>deficit2018</li>
</ul>

A função query consulta a informação desejada. 

**IN_DEFICIT_ATENCAO == 1**: alunos com Défict de Atenção

**IN_DEFICIT_ATENCAO == 0**: alunos sem Défict de Atenção


<h4> Resultado da Consulta:</h4>
<ul>
  <li>2014: 4792 alunos com Défict de Atenção fizeram o Enem</li>
  <li>2015: 3848 alunos com Défict de Atenção fizeram o Enem</li>
  <li>2016: 5300 alunos com Défict de Atenção fizeram o Enem</li>
  <li>2017: 7789 alunos com Défict de Atenção fizeram o Enem</li>
  <li>2018: 7199 alunos com Défict de Atenção fizeram o Enem</li>
</ul>

<h3> Criando o gráfico</h3>

<img src= "https://user-images.githubusercontent.com/56441375/69772546-fc963a80-116e-11ea-8d99-e05d902dbe7f.PNG" height="400" widht ="400">

Criamos uma lista vazia chamada **dados_por_ano**. 
Adicionamos os valores consultados acima, em uma só lista: 

```
dados_por_ano.append(deficit2014)
dados_por_ano.append(deficit2015)
dados_por_ano.append(deficit2016)
dados_por_ano.append(deficit2017)
dados_por_ano.append(deficit2018)
```

Para criar o Gráfico: 

```
plt.bar(anos, dados_por_ano, color='#6495ED')
plt.ylabel('Candidatos com deficit de atenção')
plt.xlabel('Anos')
plt.title('Candidatos do ENEM com deficit de atenção')
```

<h2>Analisando as notas da Redação</h2>

Foram criadas 2 listas vazias, uma dos alunos com Défict de Atenção e outra sem. 

```
redacao_por_ano = [] #alunos c/ Défict de Atenção
redacao_por_ano_sem_df = [] #alunos s/ Défict de Atenção
```

<h3>Consulta da média das notas das redações: Alunos com Défict de Atenção</h3>

```
redacao2014 = microdadosEnem2014.query('(IN_DEFICIT_ATENCAO == 1 and NU_NOTA_REDACAO)')['NU_NOTA_REDACAO'].mean()
redacao2015 = microdadosEnem2015.query('(IN_DEFICIT_ATENCAO == 1 and NU_NOTA_REDACAO)')['NU_NOTA_REDACAO'].mean()
redacao2016 = microdadosEnem2016.query('(IN_DEFICIT_ATENCAO == 1 and NU_NOTA_REDACAO)')['NU_NOTA_REDACAO'].mean()
redacao2017 = microdadosEnem2017.query('(IN_DEFICIT_ATENCAO == 1 and NU_NOTA_REDACAO)')['NU_NOTA_REDACAO'].mean()
redacao2018 = microdadosEnem2018.query('(IN_DEFICIT_ATENCAO == 1 and NU_NOTA_REDACAO)')['NU_NOTA_REDACAO'].mean()
```

A Função mean() tem como objetivo de calcular a média dentre todos os valores dos alunos com Défict de Atenção. 

<h4>Adicionando as médias a lista vazia</h4> 

```
redacao_por_ano.append(redacao2014)
redacao_por_ano.append(redacao2015)
redacao_por_ano.append(redacao2016)
redacao_por_ano.append(redacao2017)
redacao_por_ano.append(redacao2018)
```

<h4>Resultados das médias das notas de Redação: Alunos com Défict de Atenção</h4> 
<ul>
  <li>2014: 597.4</li>
  <li>2015: 668.9846590909091</li>
  <li>2016: 673.310692669805</li>
  <li>2017: 662.877170622909</li>
  <li>2018: 671.902343109946</li>
</ul>

<h3>Consulta da média das notas das redações: Alunos sem Défict de Atenção</h3>
Foi feito o mesmo processo do anterior, porém, a coluna IN_DEFICIT_ATENCAO == 0, ou seja, são alunos que não possuem Défict de Atenção

```
redacao2014sdf = microdadosEnem2014.query('(IN_DEFICIT_ATENCAO == 0 and NU_NOTA_REDACAO)')['NU_NOTA_REDACAO'].mean()
redacao2015sdf = microdadosEnem2015.query('(IN_DEFICIT_ATENCAO == 0 and NU_NOTA_REDACAO)')['NU_NOTA_REDACAO'].mean()
redacao2016sdf = microdadosEnem2016.query('(IN_DEFICIT_ATENCAO == 0 and NU_NOTA_REDACAO)')['NU_NOTA_REDACAO'].mean()
redacao2017sdf = microdadosEnem2017.query('(IN_DEFICIT_ATENCAO == 0 and NU_NOTA_REDACAO)')['NU_NOTA_REDACAO'].mean()
redacao2018sdf = microdadosEnem2018.query('(IN_DEFICIT_ATENCAO == 0 and NU_NOTA_REDACAO)')['NU_NOTA_REDACAO'].mean()
```

```
redacao_por_ano_sem_df.append(redacao2014sdf)
redacao_por_ano_sem_df.append(redacao2015sdf)
redacao_por_ano_sem_df.append(redacao2016sdf)
redacao_por_ano_sem_df.append(redacao2017sdf)
redacao_por_ano_sem_df.append(redacao2018sdf)
```


<h4>Resultado da média das Notas de Redação dos Alunos sem Défict de Atenção: </h4>

```
redacao_por_ano_sem_df
```
<ul>
  <li>2014: 581.3305709023941 </li>
  <li>2015: 541.9724381337455 </li>
  <li>2016: 542.1498524635513</li>
  <li>2017: 558.403625354807</li>
  <li>2018: 522.5685460989124</li>
</ul>

<h3> Gráfico de análise entre Média de Notas de: Alunos com Défict de Atenção x Alunos sem Défict de Atenção" </h3> 

```
# largura da barra
barWidth = 0.25

# posicao barra
b1 = np.arange(len(redacao_por_ano))
b2 = [x + barWidth for x in b1]

# criaçao de barras
plt.bar(b1, redacao_por_ano, color='#6A5ACD', width=barWidth, label='c/ Deficit')
plt.bar(b2, redacao_por_ano_sem_df, color='#6495ED', width=barWidth, label='s/ Deficit')

# legenda
plt.xlabel('Anos')
plt.xticks([b + barWidth for b in range(len(redacao_por_ano))], anos)
plt.ylabel('Notas - Médias')
plt.title('Médias das notas de redação')

plt.legend()
```

<img src= "https://user-images.githubusercontent.com/56441375/69772008-7d543700-116d-11ea-851b-5cf5c2a00933.png" height="400" widht ="400">

<h2>Considerações Finais</h2> 
A Média das Notas de Redação dos Alunos com Défict de Atenção dos anos de 2014 a 2018 são maiores do que os alunos sem. 
