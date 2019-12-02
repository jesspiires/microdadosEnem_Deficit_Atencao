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


Essa mesma leitura foi feita para os microdados do enem dos anos de 2015, 2016, 2017 e 2018. 


<h2>Análise dos Alunos que fizeram Enem nos anos de 2014 a 2018:</h2> 

<h3> Quantidade de Alunos com Défict de Atenção que fizeram o Enem em seus respectivos anos:</h3>
<ul>
  <li>2014: 4792 alunos </li>
  <li>2015: 3848 alunos </li>
  <li>2016: 5300 alunos </li>
  <li>2017: 7789 alunos </li>
  <li>2018: 7199 alunos </li>
</ul>

<h3> Quantidade de Alunos sem Défict de Atenção que fizeram o Enem em seus respectivos anos:</h3>

<ul>
  <li>2014: 8.717.456 alunos </li>
  <li>2015: 7.742.579 alunos </li>
  <li>2016: 8.622.067 alunos </li>
  <li>2017: 6.723.552 alunos </li>
  <li>2018: 5.506.548 alunos </li>
</ul>

<h3> Média das notas da REDAÇÃO do Enem de Alunos **com** Défict de Atenção em seus respectivos anos:</h3>
<ul>
  <li>2014: 597.4</li>
  <li>2015: 668.9846590909091</li>
  <li>2016: 673.310692669805</li>
  <li>2017: 662.877170622909</li>
  <li>2018: 671.902343109946</li>
</ul>

<h3> Média das notas da REDAÇÃO do Enem de Alunos **sem** Défict de Atenção em seus respectivos anos:</h3>

<ul>
  <li>2014: 581.3305709023941 </li>
  <li>2015: 541.9724381337455 </li>
  <li>2016: 542.1498524635513</li>
  <li>2017: 558.403625354807</li>
  <li>2018: 522.5685460989124</li>
</ul>

<h2> Análise visual </h3>

<img src= "https://user-images.githubusercontent.com/56441375/69772546-fc963a80-116e-11ea-8d99-e05d902dbe7f.PNG" height="400" widht ="400">


<h2>Resultados das médias das notas de Redação: Alunos com Défict de Atenção</h2> 


<h2>Resultado da média das Notas de Redação dos Alunos sem Défict de Atenção: </h2>




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
