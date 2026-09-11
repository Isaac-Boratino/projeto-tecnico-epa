# Projeto Técnico VivEtec - Portas Abertas

## Descrição
Repositório do Projeto Técnico para a VivEtec - Portas Abertas. Nele, registramos e administramos o projeto composto por Isaac Freitas Boratino, Tulio Dias Duarte dos Santos, Cauã Bispo Galvão, Gabriel Moura Minzon, Victor Eufrásio Pereira, Rafael Alves Camargo sobre monitoramento e detecção automática de falhas em postes de iluminação pública.

## Resumo do Projeto
**Equipe:** Etec Vereador Valdivino Antônio Marcusso, Ensino Médio integrado ao Técnico em Desenvolvimento de Sistemas (Projeto Técnico, orientado pelo prof. Bruno)

### Problema abordado
Postes de iluminação pública que ficam quebrados, queimados ou acesos em horário errado (piscando ou ligados de dia), sem detecção rápida do defeito. A manutenção é responsabilidade das prefeituras desde 2015, e o reparo geralmente só acontece após reclamação do morador — o que prolonga riscos de segurança (vias mal iluminadas favorecem furtos e roubos, e reduzem a segurança viária) e gera desperdício de energia (a prefeitura paga pela conta mesmo com o ponto inativo).

### Objetivo do projeto
Desenvolver, em uma maquete com ESP32, um sistema de baixo custo que identifique automaticamente postes de iluminação pública com defeito (apagados, queimados ou acesos em horário errado) e notifique o responsável pela manutenção, sem depender de denúncia manual.

### Solução técnica proposta
- **Sensor:** LDR (fotorresistor), um por poste, em divisor de tensão com resistor de 10 kΩ, ligado aos pinos ADC1 do ESP32
- **Microcontrolador:** ESP32 DevKit V1 (Xtensa LX6 dual-core, até 240 MHz, 4MB Flash, 520KB RAM, Wi-Fi + Bluetooth) — escolhido pela conectividade Wi-Fi nativa, pelos canais ADC1 compatíveis com uso simultâneo do rádio Wi-Fi, e pelo processamento dual-core para tarefas concorrentes
- **Atuadores:** LED (simula a lâmpada de cada poste) e Buzzer (indicativo sonoro local de demonstração)
- **Entrada de simulação:** botão push-button (`INPUT_PULLUP`), que interrompe fisicamente o circuito do LED para simular a falha de um poste
- **Conectividade:** Wi-Fi 802.11 b/g/n (2,4 GHz), modo estação, WPA2-PSK
- **Protocolo de comunicação:** HTTP/HTTPS — usado tanto para o alerta via bot do Telegram quanto para o envio de dados ao ThingSpeak e para o servidor web local
- **Armazenamento/monitoramento:** Bot do Telegram (alerta pontual de falha) + painel web embutido no próprio ESP32 (status ao vivo dos três postes) + ThingSpeak (histórico e gráficos de luminosidade)
- **Sincronização de horário:** NTP, usado para determinar se é dia ou noite na lógica de detecção de falhas
- **Alimentação:** USB (5V), regulado internamente para 3,3V pelo próprio ESP32 — adequado ao cenário de maquete estacionária

### Funcionamento esperado
O ESP32 lê continuamente os três sensores LDR e compara o estado de cada poste (aceso/apagado) com o horário do dia sincronizado via NTP. Uma falha é identificada em dois cenários: poste apagado à noite (lâmpada queimada/interrompida) ou poste aceso durante o dia (desperdício de energia). Ao detectar a falha, o sistema aciona o LED/buzzer localmente, envia um alerta via Telegram e atualiza o status no painel web; em paralelo, envia periodicamente os valores de luminosidade ao ThingSpeak, construindo um histórico gráfico do comportamento dos postes ao longo do tempo.

### Benefícios esperados
Redução do tempo de detecção de falhas (de um modelo reativo, dependente de denúncia, para detecção em tempo real), redução do desperdício de energia elétrica, redução do custo de manutenção corretiva, e contribuição indireta para a segurança pública ao manter a iluminação das ruas funcionando de forma mais consistente.

### Limitações apontadas
- Depende de conexão Wi-Fi, o que limitaria a escala de uma instalação real (postes espalhados pela cidade);
- A alimentação via USB usada na maquete não se aplica a uma instalação real em poste de rua;
- O limiar de luminosidade (`limiarLuz`) precisa ser calibrado manualmente para as condições de luz do ambiente de teste;
- A validação foi feita em pequena escala (três postes simulados).

### Melhorias futuras sugeridas
Uso de uma tecnologia de longo alcance e baixo consumo (como LoRa) para uma instalação real, adição de sensor de corrente elétrica para diferenciar tipos de falha, implementação de WebSocket no painel para atualização em tempo real, análise de tendência sobre o histórico do ThingSpeak para antecipar manutenção, e migração da fonte de alimentação para painel solar + bateria em uma instalação de campo.
