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

PS: digite ```jupyter notebook``` no prompt de comando para abrir o jupyter e crie um novo arquivo em ipynb 

<h3>Importação das bibliotecas no Jupyter</h3>

```import pandas as pd```

```import matplotlib.pyplot as plt```

```import numpy as np```

```low_memory = False``` Permite que não haja problemas referente a falta de memória do computador

<h3>Importação das Listas com as colunas de interesse</h3>

Lendo os arquivos csv
```microdadosEnem2014 = pd.read_csv('MICRODADOS_ENEM_2014.csv', sep=',', encoding='ISO-8859-1', usecols = ['UF_RESIDENCIA', 'UF_PROVA', 'IN_DEFICIT_ATENCAO', 'NU_NOTA_REDACAO'])```

Essa mesma leitura foi feita para os microdados do enem dos anos de 2015, 2016, 2017 e 2018. 

<h3>Variáveis para o Gráfico</h3>

```anos = ['2014', '2015', '2016', '2017', '2018'] ```

```dados_por_ano = []```

<h3>Consulta da informação necessária: Alunos com Défict de Atenção</h3> 

```deficit2014 = microdadosEnem2014.query('(IN_DEFICIT_ATENCAO == 1)')['IN_DEFICIT_ATENCAO'].count()```

Essa mesma leitura foi feita para todos os anos de estudo: 2014, 2015, 2016, 2017 e 2018
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

<img src= "https://user-images.githubusercontent.com/56441375/69770555-3c0d5880-1168-11ea-8ea6-9327801965d3.PNG" height="650" widht ="650">

Criamos uma lista vazia chamada **dados_por_ano**. 
Adicionamos os valores coletados 

