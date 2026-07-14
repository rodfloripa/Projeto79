# Detecção de Anomalias em Sensores Industriais com Processamento Digital de Sinais e Machine Learning

## 1. Descrição

<p align="justify">
Este projeto apresenta uma abordagem para detecção automática de anomalias em sinais provenientes de sensores industriais utilizando técnicas de Processamento Digital de Sinais (DSP) combinadas com algoritmos de Machine Learning. O objetivo é identificar comportamentos incomuns antes que eles evoluam para falhas críticas, contribuindo para estratégias de manutenção preditiva e aumento da confiabilidade operacional.
</p>

<p align="justify">
Inicialmente são gerados dados sintéticos representando medições de sensores como temperatura, pressão, vibração, corrente elétrica, tensão e velocidade. Em seguida, diferentes técnicas de extração de características são aplicadas para transformar os sinais em indicadores capazes de evidenciar alterações de comportamento.
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
Após a extração das características, o algoritmo Isolation Forest é utilizado para separar automaticamente observações normais e anômalas. O método constrói árvores aleatórias capazes de isolar rapidamente pontos incomuns, tornando-se bastante eficiente para problemas de detecção de outliers em grandes conjuntos de dados.
</p>

---

## 10. Aplicações

<p align="justify">
A metodologia apresentada pode ser aplicada em diversos setores industriais onde sensores monitoram continuamente equipamentos críticos. Entre as principais aplicações destacam-se manutenção preditiva, monitoramento de motores elétricos, análise de vibração, inspeção de rolamentos, monitoramento de bombas, compressores, turbinas, sistemas elétricos e processos industriais automatizados.
</p>

---

## 11. Resultados Esperados

<p align="justify">
A combinação entre técnicas clássicas de Processamento Digital de Sinais e algoritmos modernos de Machine Learning permite aumentar significativamente a capacidade de identificar alterações sutis nos sinais monitorados. A busca automática pelo melhor tamanho de janela torna os métodos adaptáveis a diferentes tipos de sensores, enquanto o Isolation Forest fornece uma etapa robusta de identificação de comportamentos incomuns.
</p>

---

## 12. Conclusão

<p align="justify">
Este projeto demonstra que a integração entre Processamento Digital de Sinais e Machine Learning constitui uma abordagem eficiente para detecção de anomalias em ambientes industriais. Técnicas como Z-Score, RMS, Curtose e Envelope de Hilbert extraem informações relevantes diretamente dos sinais, enquanto o Isolation Forest utiliza essas características para identificar automaticamente padrões incomuns. Essa combinação reduz a dependência de inspeções manuais, possibilita monitoramento contínuo dos equipamentos e auxilia na antecipação de falhas, contribuindo para estratégias de manutenção preditiva, redução de custos operacionais e aumento da disponibilidade dos ativos industriais.
</p>
