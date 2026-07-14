# Detecção de Anomalias em Sensores Industriais



## 1. Descrição

<p align="justify">
Este projeto apresenta uma abordagem para detecção automática de anomalias em sensores industriais utilizando Processamento Digital de Sinais (DSP) e Machine Learning não supervisionado. Em aplicações industriais, normalmente não existem bases de dados rotuladas, pois falhas são eventos raros, imprevisíveis e dificilmente possuem marcação precisa do instante em que começaram. Dessa forma, métodos não supervisionados, como o Isolation Forest, são particularmente adequados por aprenderem o comportamento normal dos equipamentos e identificarem automaticamente desvios significativos.
</p>

<p align="justify">
Outro desafio importante é a sobreposição de componentes espectrais. Motores, rolamentos, engrenagens e outras fontes geram frequências semelhantes, dificultando a separação entre comportamento normal, ruído e assinaturas de falhas. Por isso, técnicas de DSP são empregadas para extrair características mais representativas antes da etapa de aprendizado.
</p>

## 2. Importância das Características

| Característica | Importância |
|---|---:|
| Vibracao_RMS | 0.988905 |
| Corrente | 0.767461 |
| Tensao | 0.375059 |
| Temp | 0.212666 |
| Pressao | 0.174792 |
| Velocidade | 0.162872 |
| Vibracao_Envelope | 0.047619 |
| Vibracao_Kurt | 0.040096 |

<p align="justify">
Os resultados indicam que o RMS da vibração foi a característica mais relevante para a identificação das anomalias, seguido pela corrente elétrica. Isso evidencia que alterações na energia vibracional possuem maior capacidade de discriminar condições anormais neste conjunto de dados.
</p>

## 3. Conclusão

<p align="justify">
A combinação entre Processamento Digital de Sinais e Machine Learning não supervisionado constitui uma estratégia robusta para manutenção preditiva, permitindo detectar anomalias mesmo na ausência de dados rotulados e diante da sobreposição espectral dos sinais industriais.
</p>
