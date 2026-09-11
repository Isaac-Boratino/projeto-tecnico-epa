# Pesquisa de Contexto e Objetivo — Projeto IoT: Monitoramento de Postes de Iluminação Pública

**Projeto:** Maquete com ESP32 para identificação de postes de luz quebrados, queimados ou acesos em horário errado
**Finalidade:** Feira EPA (Etec de Portas Abertas) — Etec de Boituva

---

## 1. Contextualização do Problema

**Qual problema foi identificado?**
Postes de iluminação pública que ficam quebrados, queimados ou acesos em horário errado (piscando ou ligados de dia), sem detecção rápida do defeito.

**Onde ocorre?**
Contexto urbano/residencial: ruas, calçadas e bairros. A manutenção é responsabilidade das prefeituras (desde 2015), e o reparo geralmente só acontece após reclamação do morador.

**Quem é afetado?**
Pedestres e moradores (ruas escuras à noite), comerciantes locais (menos movimento noturno), motoristas (mais risco de acidente) e as próprias prefeituras (custo de manutenção reativa e reclamações constantes).

**Consequências**
- **Sociais/segurança:** vias mal iluminadas favorecem furtos e roubos; estudos com dados da PNAD Contínua associam melhor iluminação a menos crimes contra o patrimônio, e um experimento em Nova York registrou queda de 36% a 60% em crimes noturnos após reforço de iluminação;
- **Segurança viária:** vias bem iluminadas reduzem acidentes de trânsito;
- **Econômicas:** a prefeitura paga pela energia mesmo com o ponto inativo, e a manutenção corretiva (depois da falha) é mais cara que a preventiva.

---

## 2. Justificativa

**Por que o problema precisa ser resolvido?**
Porque hoje a correção depende quase sempre de alguém perceber o defeito e denunciar — muitos postes continuam quebrados por falta de reclamação, prolongando os riscos de segurança e o desperdício de energia.

**Relevância social e econômica**
Social: iluminação adequada aumenta a sensação de segurança e incentiva o uso de espaços públicos à noite. Econômica: detecção mais rápida evita gasto de energia com pontos com defeito e reduz o custo de manutenção corretiva.

**Soluções atuais e suas limitações**
- *Denúncia manual* (telefone, app da prefeitura): simples, mas lenta e depende do cidadão notar e reportar o problema.
- *Telegestão/IoT comercial* (luminárias conectadas via LoRaWAN, NB-IoT etc., com detecção de falhas e dimerização remota): eficiente, mas tem alto custo de implantação, exige licitações complexas, contratos longos (mínimo 5 anos) e homologação pelo Inmetro — inviável para pequena escala.

Essas duas soluções deixam uma lacuna entre "barato e lento" e "eficiente e caro", que justifica uma alternativa de detecção automática e baixo custo.

---

## 3. Objetivo do Projeto

**Objetivo geral**
Desenvolver, em uma maquete com ESP32, um sistema de baixo custo que identifique automaticamente postes de iluminação pública com defeito (apagados, queimados ou acesos em horário errado) e notifique o responsável pela manutenção, sem depender de denúncia manual.

**Objetivos específicos**
1. Simular, na maquete, três postes monitorados individualmente por sensores conectados ao ESP32;
2. Detectar automaticamente quando um poste é desligado (via botão de simulação de defeito);
3. Notificar o responsável (painel/app simulando a prefeitura) sobre qual poste apresenta falha;
4. Demonstrar a viabilidade da solução com componentes de baixo custo;
5. Apresentar o funcionamento do sistema de forma clara na Feira EPA.

---

## Fontes consultadas

- Jornal de Brasília: https://jornaldebrasilia.com.br/brasilia/escuridao-na-asa-sul-moradores-denunciam-postes-de-iluminacao-publica-queimados/
- Carioca Digital: https://carioca.rio/sistema/solicitacoes-on-line/?atividades=notificar-problemas-com-iluminacao-publica
- CPFL: https://cpfl.com.br/reparos-de-iluminacao-publica
- Portal de Serviços SP: https://servicos.sp.gov.br/fcarta/3036ABC8-2616-45E3-A02C-4C2CAA79B3D1
- Revista USP (PAAM): https://revistas.usp.br/paam/en/article/download/174975/176102/517467
- SciELO Colombia: http://www.scielo.org.co/scielo.php?pid=S0120-63462025000104984&script=sci_abstract&tlng=pt
- CONCCEPAR: https://conccepar.grupointegrado.br/resumo/
- ENCAC/ANTAC: https://eventos.antac.org.br/encac/article/view/6760
- QLuz Palhoça: https://www.qluzpalhoca.com.br/entenda-a-relacao-entre-iluminacao-publica-e-seguranca/
- Exame: https://exame.com/bussola/iluminacao-publica-o-vetor-de-eficiencia-fiscal-e-seguranca/
- Ubidots: https://pt.ubidots.com/solutions/iot-infrastructure-for-the-modern-smart-city
- Futurecom Digital: https://digital.futurecom.com.br/transformaodigital/iluminacao-publica-inteligente-o-uso-de-iot-nas-cidades-inteligentes/
- SBA (CBA 2024): https://www.sba.org.br/cba2024/papers/paper_632.pdf
- Alma IoT: https://almaiot.com.br/iluminacao-inteligente/
- Nexum IoT: https://nexumiot.com.br/iluminacao-publica-inteligente-como-a-tecnologia-iot-pode-transformar-a-iluminacao-publica-como-conhecemos-hoje/
- Demape: https://demape.com.br/telegestao-de-iluminacao-publica-transforme-sua-cidade/
- Conjur: https://www.conjur.com.br/2025-fev-21/telegestao-na-iluminacao-publica-o-engodo-da-dimerizacao-e-a-omissao-da-aprovacao-do-inmetro/
- AALOK: https://aalok.com.br/blog/iluminacao-publica/principais-desafios-dos-municipios-com-iluminacao-publica/
- M3E: https://m3e.com.br/artigos/geotecnologias-e-inovacao/inventario-iluminacao-publica-ppps/

*Observação: material de apoio para orientar o escopo do projeto — na redação final, reescrever com as próprias palavras e citar as fontes em ABNT.*
