###### **Dashboard com os valores dos preços dos combustíveis nos últimos anos no Brasil.**



A ideia desse projeto é praticar o conhecimento adquirido nas aulas de Power BI do Bootcamp da Randstad pela DIO.



###### 

###### **Base baixada do site do Governo em 06/08/2025 às 11:13**



https://dados.gov.br/dados/conjuntos-dados/serie-historica-de-precos-de-combustiveis-e-de-glp



###### 

###### **Perguntas de negócios a serem respondidas:**



📌 1. Como evoluiu o preço médio da gasolina nos últimos 6 anos no Brasil?

&nbsp;

📌 2. Qual é a diferença média de preço entre cada região do Brasil?



📌 3. Quantos postos foram avaliados e qual o preço de cada regional deles?





###### **----------------------------**

###### **📦 BASE DE DADOS UTILIZADA**

###### **----------------------------**



2o Sem 2024 - Combustíveis Automotivos.csv

1o Sem 2024 - Combustíveis Automotivos.csv

2o Sem 2023 - Combustíveis Automotivos.csv

1o Sem 2023 - Combustíveis Automotivos.csv

2o Sem 2022 - Combustíveis Automotivos.csv

1o Sem 2022 - Combustíveis Automotivos.csv

2o Sem 2021 - Combustíveis Automotivos.csv

1o Sem 2021 - Combustíveis Automotivos.csv

2o Sem 2020 - Combustíveis Automotivos.csv

1o Sem 2020 - Combustíveis Automotivos.csv

2o Sem 2019 - Combustíveis Automotivos.csv

1o Sem 2019 - Combustíveis Automotivos.csv

2o Sem 2018 - Combustíveis Automotivos.csv

1o.Sem 2018 - Combustíveis Automotivos.csv



###### **----------------------------**

###### **📦 PACOTE DE MEDIDAS EM DAX**

###### **----------------------------**



**📌 1. Lucro**


&nbsp;	Lucro = \[PreçoMedioVenda] - \[PreçoMedioCompra]



**📌 2. Preço Médio de Compra**



&nbsp;	PreçoMedioCompra = AVERAGE(Base\[Valor de Compra])



**📌 3. Preço Médio de Venda**



&nbsp;	PreçoMedioVenda = AVERAGE(Base\[Valor de Venda])



**📌 4. Preço Médio de Venda**



&nbsp;	QtdPosto = DISTINCTCOUNT(Base\[CNPJ da Revenda])



**📌 5. Variação % Semestre Anterior**



&nbsp;	Variação % Semestre Anterior = 

&nbsp;	VAR MediaAtual = \[PreçoMedioVenda]

&nbsp;	VAR MediaAnterior = 

&nbsp;	    CALCULATE(

&nbsp;       	\[PreçoMedioVenda],

&nbsp;	        DATEADD('Base'\[Data da Coleta], -6, MONTH)

&nbsp;	    )

&nbsp;	RETURN

&nbsp;	IF(

&nbsp;	    NOT ISBLANK(MediaAnterior),

&nbsp;	    DIVIDE(MediaAtual - MediaAnterior, MediaAnterior),

&nbsp;	    BLANK()

&nbsp;	)



