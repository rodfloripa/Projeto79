# Detecção de Anomalias em Sensores Industriais com Processamento Digital de Sinais e Machine Learning

## 1. Descrição

<p align="justify">
Este projeto apresenta uma abordagem para detecção automática de anomalias em sensores industriais utilizando técnicas de Processamento Digital de Sinais (DSP) combinadas com Machine Learning não supervisionado. Diferentemente de problemas tradicionais de classificação, aplicações industriais raramente dispõem de grandes bases de dados rotuladas indicando exatamente quando ocorreu uma falha, tornando inviável o treinamento de modelos supervisionados em muitos cenários reais.
</p>

<p align="justify">
Na prática, equipamentos industriais permanecem operando durante meses ou anos sem apresentar falhas, enquanto eventos anômalos são raros, imprevisíveis e muitas vezes sequer são registrados corretamente. Além disso, quando uma falha ocorre, normalmente não existe um especialista acompanhando continuamente o processo para identificar o instante exato em que ela começou. Como consequência, construir um conjunto de dados contendo milhares de exemplos corretamente rotulados torna-se uma tarefa extremamente cara e, frequentemente, impossível.
</p>

<p align="justify">
Por esse motivo, métodos não supervisionados representam uma alternativa bastante atrativa para manutenção preditiva. Esses algoritmos aprendem o comportamento normal do processo e identificam automaticamente observações que apresentam desvios significativos em relação ao padrão esperado, dispensando a necessidade de rótulos durante o treinamento.
</p>

<p align="justify">
Outro desafio importante está relacionado à própria natureza dos sinais industriais. Vibração, corrente elétrica, temperatura, pressão e outras variáveis refletem simultaneamente diversos fenômenos físicos. Como consequência, diferentes componentes espectrais frequentemente se sobrepõem no domínio da frequência, dificultando a separação entre o comportamento normal da máquina, ruídos e assinaturas de falhas. Essa característica torna necessária a utilização de técnicas de Processamento Digital de Sinais capazes de extrair informações relevantes antes da etapa de aprendizado de máquina.
</p>
<p align="justify">
Veja como as classes se sobrepõesm na frequência deixando a detecção difícil
<p align="center">
  <img src="https://github.com/rodfloripa/Projeto79/blob/main/fig1.png" > 
</p>
</p>
---

## 2. Objetivos

<p align="justify">
O projeto busca demonstrar como técnicas clássicas de análise de sinais podem ser utilizadas para construir um sistema eficiente de detecção de anomalias. Além disso, apresenta uma comparação entre diferentes métricas extraídas dos sinais, permitindo identificar quais características possuem maior capacidade discriminativa.
</p>

---

## 3. Técnicas Utilizadas

<p align="justify">
Durante o processamento dos sinais são empregadas diversas técnicas estatísticas e de Processamento Digital de Sinais para produzir escores de anomalia. Entre elas destacam-se:
</p>

- Z-Score em janela móvel
- RMS (Root Mean Square)
- Curtose (Kurtosis)
- Envelope espectral utilizando Transformada de Hilbert
- Filtro Butterworth
- Estimativa espectral por Welch
- Normalização RobustScaler
- Isolation Forest

---

## 4. Funcionamento do Projeto

<p align="justify">
O fluxo de execução inicia com a geração de um conjunto de dados contendo amostras normais e amostras anômalas. Cada sensor apresenta distribuições estatísticas distintas, simulando um ambiente industrial realista.
</p>

<p align="justify">
Após a geração dos dados, diferentes algoritmos de Processamento Digital de Sinais são aplicados individualmente para produzir um score de anomalia. Esses scores representam o quanto cada observação se distancia do comportamento esperado.
</p>

<p align="justify">
Alguns métodos utilizam janelas móveis para acompanhar alterações temporais dos sinais. O projeto ainda realiza uma busca automática pelo tamanho de janela que produz o melhor desempenho para cada técnica, aumentando a capacidade de detecção.
</p>

<p align="justify">
As características extraídas são então normalizadas utilizando o RobustScaler, reduzindo a influência de valores extremos antes da etapa de aprendizado de máquina.
</p>

<p align="justify">
Por fim, o algoritmo Isolation Forest recebe essas características para identificar automaticamente observações consideradas anômalas sem depender diretamente de um modelo supervisionado.
</p>

---

## 5. Estrutura do Algoritmo

```text
Geração dos dados
        │
        ▼
Pré-processamento dos sinais
        │
        ▼
Extração de características
(Z-Score, RMS, Curtose,
Envelope, Energia)
        │
        ▼
Busca da melhor janela
        │
        ▼
Normalização RobustScaler
        │
        ▼
Isolation Forest
        │
        ▼
Detecção de Anomalias
        │
        ▼
Avaliação dos Resultados
```

---

## 6. Principais Bibliotecas

```python
numpy
pandas
matplotlib
seaborn
scipy.signal
scikit-learn
```

---

## 7. Métricas de Avaliação

<p align="justify">
O desempenho dos métodos é avaliado utilizando métricas amplamente empregadas em problemas de classificação e detecção de anomalias. Entre elas destacam-se:
</p>

- Precision
- Recall
- Precision-Recall Curve
- Average Precision (PR-AUC)
- ROC-AUC
- Classification Report
- Matriz de Confusão

---

## 8. Técnicas de Processamento Digital de Sinais

### Z-Score

<p align="justify">
Calcula o quanto uma observação se distancia da média local utilizando uma janela móvel. Valores elevados indicam possíveis anomalias.
</p>

### RMS

<p align="justify">
O Root Mean Square mede a energia média do sinal. Alterações repentinas na energia costumam indicar mudanças no estado operacional do equipamento.
</p>

### Curtose

<p align="justify">
A Curtose mede o grau de concentração dos valores em torno da média. Picos elevados normalmente estão associados à ocorrência de impactos ou falhas mecânicas.
</p>

### Envelope de Hilbert

<p align="justify">
O envelope obtido pela Transformada de Hilbert evidencia componentes moduladas do sinal, permitindo identificar padrões relacionados ao desgaste de componentes rotativos.
</p>

### Filtro Butterworth

<p align="justify">
É utilizado para selecionar apenas a faixa de frequência de interesse antes do cálculo do envelope, reduzindo interferências e ruídos.
</p>

### Método de Welch

<p align="justify">
Realiza a estimativa da densidade espectral de potência do sinal, permitindo calcular a energia presente em bandas específicas de frequência.
</p>

---

## 9. Machine Learning

<p align="justify">
Após a extração das características, é empregado o algoritmo Isolation Forest, um método de Machine Learning não supervisionado amplamente utilizado para detecção de anomalias. Diferentemente de classificadores tradicionais, o algoritmo não necessita de exemplos previamente rotulados de falhas. Em vez disso, ele aprende a estrutura dos dados durante o treinamento e identifica automaticamente observações que apresentam comportamento significativamente diferente da maioria das amostras.
</p>

<p align="justify">
Essa característica torna o Isolation Forest especialmente adequado para aplicações industriais, onde falhas são eventos raros, existe forte desbalanceamento entre condições normais e anômalas e, na maioria dos casos, não há disponibilidade de bases históricas contendo rótulos confiáveis para treinamento supervisionado.
</p>

---

## 10. Aplicações

<p align="justify">
A metodologia apresentada pode ser aplicada em diversos setores industriais onde sensores monitoram continuamente equipamentos críticos. Entre as principais aplicações destacam-se manutenção preditiva, monitoramento de motores elétricos, análise de vibração, inspeção de rolamentos, monitoramento de bombas, compressores, turbinas, sistemas elétricos e processos industriais automatizados.
</p>

---

## 11. Resultados

<p align="justify">
<p align="center">
  <img src="https://github.com/rodfloripa/Projeto79/blob/main/fig2.png" > 
</p>

A análise da importância das características demonstra que nem todos os sensores contribuem igualmente para a detecção de anomalias. O atributo derivado da energia do sinal de vibração (Vibração RMS) apresentou a maior relevância, indicando que alterações na energia vibracional constituem o principal indicador das falhas simuladas.
</p>

| Característica | PR-AUC |
|---------------|------------:|
| Vibracao_RMS | **0.98** |
| Corrente | **0.76** |
| Tensao | **0.37** |
| Temp | **0.21** |
| Pressao | **0.17** |
| Velocidade | **0.16** |
| Vibracao_Envelope | **0.04** |
| Vibracao_Kurt | **0.04** |

<p align="justify">
Observa-se que o RMS da vibração foi significativamente mais informativo do que as demais características, seguido pelas medições de corrente elétrica e tensão. Em contrapartida, atributos derivados do envelope de Hilbert e da curtose apresentaram menor contribuição para este conjunto de dados específico. Esse resultado evidencia que a eficácia de uma técnica de Processamento Digital de Sinais depende diretamente das características das falhas presentes e do comportamento espectral dos sinais analisados.
</p>

<p align="justify">
Também é importante destacar que, em ambientes industriais reais, diferentes fontes de vibração frequentemente compartilham faixas de frequência semelhantes. Motores, rolamentos, engrenagens, desalinhamentos, desbalanceamentos e ruídos estruturais podem produzir componentes espectrais sobrepostas, reduzindo a capacidade de técnicas isoladas identificarem claramente uma única origem de falha. Por essa razão, a combinação entre múltiplas características extraídas dos sinais e algoritmos não supervisionados tende a produzir resultados mais robustos do que a utilização de um único indicador.
</p>
### 11.1 Comparando com e sem DSP no Isolation Forest

| Método / Característica | PR-AUC com DSP | PR-AUC sem DSP |
| --- | --- | --- |
| Vibracao | 0.99 | 0.12 |
| IsolationForest | 0.79 | 0.53 |
| Corrente | 0.77 | 0.31 |
| Tensao | 0.38 | 0.57 |
| Temp | 0.21 | 0.30 |
| Pressao | 0.17 | 0.27 |
| Velocidade | 0.16 | 0.22 |
---

## 12. Conclusão

<p align="justify">
Este projeto demonstra que a integração entre Processamento Digital de Sinais e Machine Learning constitui uma abordagem eficiente para detecção de anomalias em ambientes industriais. Técnicas como Z-Score, RMS, Curtose e Envelope de Hilbert extraem informações relevantes diretamente dos sinais, enquanto o Isolation Forest utiliza essas características para identificar automaticamente padrões incomuns. Essa combinação reduz a dependência de inspeções manuais, possibilita monitoramento contínuo dos equipamentos e auxilia na antecipação de falhas, contribuindo para estratégias de manutenção preditiva, redução de custos operacionais e aumento da disponibilidade dos ativos industriais.
</p>
