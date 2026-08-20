# Projeto Técnico VivEtec - Portas Abertas
## Descrição
Repositório do Projeto Técnico para a VivEtec - Portas Abertas. Nele, registramos e administramos o projeto composto por Isaac Freitas Boratino, Tulio Dias Duarte dos Santos, Cauã Bispo Galvão, Gabriel Moura Minzon, Victor Eufrásio Pereira, Rafael Alves Camargo sobre gerenciamento de consumo de energia.
## Resumo do Projeto
**Autor:** Cauã Bispo Galvão — Etec Valdivino Antônio Marcusso, Ensino Médio integrado ao Técnico em Desenvolvimento de Sistemas (trabalho de Sistemas Embarcados, orientado pelo prof. Bruno)

### Problema abordado:
O trabalho trata do consumo excessivo de energia elétrica, que afeta residências, empresas, comércios e até infraestrutura urbana (semáforos, postes). O autor destaca que contas de energia cada vez mais caras impactam a vida das pessoas, e que soluções existentes (casas inteligentes com IA) são caras e pouco acessíveis.

### Objetivo do projeto:
Criar um sistema IoT capaz de informar o consumo de energia do local em que for instalado, ajudando o usuário a controlar seus gastos de forma acessível.

### Solução técnica proposta:
- **Sensor:** SCT-013 (mede o consumo elétrico de forma não invasiva)
- **Microcontrolador:** ESP32 WROOM 32 (Xtensa LX6, 4MB Flash, 520KB RAM, Wi-Fi, baixo custo, consumo de 240mA) — escolhido pela conectividade Wi-Fi e baixo custo
- **Atuador:** Relé (abre/fecha circuitos)
- **Conectividade:** Wi-Fi (permite acesso remoto ao sistema)
- **Protocolo de comunicação:** MQTT (leve, ocupa pouco espaço na placa)
- **Armazenamento/monitoramento:** App Blynk (mobile e acessível) + nuvem TagoIO
- **Alimentação:** Fonte 12V chaveada (compacta, eficiente, com PFC e proteções)

### Funcionamento esperado:
O sistema seria instalado próximo à caixa de disjuntores, medindo o consumo elétrico e notificando o usuário periodicamente (diária ou semanalmente) via app.

### Benefícios esperados:
Conscientizar o usuário sobre seu consumo e ajudá-lo a economizar, com potencial de impacto social/econômico caso o projeto se popularize.

### Limitações apontadas:
Fica inoperante (e vulnerável a danos) em quedas de energia
Depende de Wi-Fi para funcionar
Instalação pode exigir ajuda profissional

### Melhorias futuras sugeridas:
Integração com assistentes de voz (ex: Alexa) e maior resistência a quedas de energia.
