# Pull Request - Projeto Maloca das iCoisas

## Descrição do Pull Request

### O que foi implementado:
Foi desenvolvido um sistema de monitoramento de temperatura para quartos de pacientes utilizando uma ESP32 e sensores de temperatura. O sistema inclui LEDs para indicar se a temperatura está dentro da faixa segura (verde), ligeiramente elevada (amarelo) ou muito alta (vermelho).


### Contexto e Motivação:
O objetivo deste projeto é garantir que os quartos de pacientes mantenham uma temperatura adequada, especialmente para pacientes vulneráveis, como recém-nascidos e idosos. O sistema permite a monitorização em tempo real e intervenções rápidas em caso de desvios de temperatura.


## Testes Realizados

### Descrição dos Testes:
- Testando Sensores: Verificação do funcionamento do potenciômetro simulando diferentes temperaturas. As leituras de voltagem e temperatura foram monitoradas no terminal serial.
- Validação dos Atuadores: Teste dos LEDs para garantir que acendem corretamente com base na temperatura simulada.
- Monitoramento em Tempo Real: Simulação de diferentes temperaturas e observação da resposta do sistema em tempo real.


### Resultados dos Testes:
- Sensores: Funcionamento correto do potenciômetro, com leituras precisas de voltagem e temperatura.
- Atuadores: LEDs responderam conforme esperado, indicando as faixas de temperatura correta.
- Monitoramento: Sistema respondeu rapidamente às mudanças de temperatura, com exibição precisa dos dados no terminal serial.


## Checklist

- [x] Código atende às normas do projeto e foi formatado de acordo com as diretrizes.
- [x] Código foi testado e validado em ambiente de desenvolvimento com hardware real (Arduino, Raspberry Pi, ESP32) ou simulação (tinkercad).
- [x] Documentação atualizada para refletir as mudanças realizadas.
- [x] Código escrito e comentado em **C** ou **Python** de acordo com os padrões do projeto.
- [x] Testes com sensores e atuadores específicos incluídos e detalhados na descrição dos testes.

## Tipo de Mudança

- [ ] Correção de bug
- [x] Nova funcionalidade
- [ ] Alteração de funcionalidade existente
- [x] Documentação

## Informações Adicionais

### Hardware Utilizado:
ESP32
Potenciômetro
LEDs (Verde, Amarelo e Vermelho)
Jumpers, resistores e Protoboard


### Simulação Utilizado:
- Wokwi

### Observações:
N/A

## Issue Relacionada

Closes #

---
