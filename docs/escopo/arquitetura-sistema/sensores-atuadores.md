# 3.3 Sensores e Atuadores

## Tabela de Componentes

| Componente | Tipo | Função | Protocolo/Interface |
|---|---|---|---|
| LDR (fotorresistor) | Sensor | Medir a luminosidade de cada poste (aceso/apagado) | Analógico (ADC1) |

## Descrição Detalhada dos Componentes

### LDR (Light Dependent Resistor) — Sensor de Luminosidade

O LDR é um resistor cuja resistência elétrica varia conforme a quantidade de luz que incide sobre ele: quanto mais luz, menor a resistência; no escuro, a resistência sobe bastante. No projeto, um LDR é posicionado em cada poste, "olhando" diretamente para o LED que representa a lâmpada.

Como o ESP32 só consegue ler tensão (não resistência) em seus pinos analógicos, o LDR é ligado em um **divisor de tensão** junto com um resistor fixo de 10 kΩ: a tensão no ponto entre os dois varia proporcionalmente à luz captada, e é esse valor de tensão que o pino ADC1 do ESP32 lê. Esse valor lido é então comparado a um limiar (`limiarLuz`) para decidir se o sistema entende o poste como "aceso" ou "apagado" — limiar que precisa ser calibrado no ambiente real da maquete antes da apresentação, já que a luminosidade ambiente do local pode alterar as leituras.

A escolha do LDR (em vez de, por exemplo, um sensor de corrente no próprio LED) foi proposital: o sistema enxerga o estado real da luz emitida, e não apenas se o circuito está energizado — isso significa que o método de detecção funciona mesmo que a causa da falha não seja o botão de simulação, mas qualquer outro motivo que apague fisicamente a luz do poste.
