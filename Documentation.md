Foi utilizada a função “MAXX” para calcular o máximo dentro de um argumento: 

Maior média por tipo de escola =  
MAXX( 
    KEEPFILTERS(VALUES('MICRODADOS_ENEM_2020'[TP_ESCOLA])), 
    CALCULATE([foi a média geral de nota]) 
) 

Foi gerado uma média de cada uma das provas, para realizar uma visão geral de cada uma das matérias: 

Prova objetiva de Ciências Humanas: 
Humanas = CALCULATE(AVERAGE(MICRODADOS_ENEM_2020[NU_NOTA_CH]), MICRODADOS_ENEM_2020[NU_NOTA_CH] <> 0 ) 

Prova objetiva de Ciências da Natureza: 
Natureza = CALCULATE(AVERAGE(MICRODADOS_ENEM_2020[NU_NOTA_CN]), MICRODADOS_ENEM_2020[NU_NOTA_CN] <> 0 ) 

Prova objetiva de Linguagens e Códigos: 
Linguagens = CALCULATE(AVERAGE(MICRODADOS_ENEM_2020[NU_NOTA_LC]), MICRODADOS_ENEM_2020[NU_NOTA_LC] <> 0 ) 

Prova objetiva de Matemática: 
Matemática = CALCULATE(AVERAGE(MICRODADOS_ENEM_2020[NU_NOTA_MT]), MICRODADOS_ENEM_2020[NU_NOTA_MT] <> 0 ) 

Prova de redação: 
Redação = (AVERAGE(MICRODADOS_ENEM_2020[NU_NOTA_REDACAO])) 

Desta forma, foram utilizadas as medidas para realizar a média geral: 
foi a média geral de nota = ([Humanas] + [Natureza] + [Linguagens] + [Matemática] + [Redação]) / 5 

Para a análise do percentual de ausência, foi utilizado a diferença da quantidade de ausentes sob o total de inscritos: 
% de ausência = COUNTX(FILTER(MICRODADOS_ENEM_2020, MICRODADOS_ENEM_2020[TP_PRESENCA_CH] = "0"), MICRODADOS_ENEM_2020[NU_INSCRICAO]) / COUNT(MICRODADOS_ENEM_2020[TP_PRESENCA_CH]) 

Já a contagem do total de inscritos, somente o “Count” dos inscritos: 
de inscritos = COUNT(MICRODADOS_ENEM_2020[NU_INSCRICAO]) 
