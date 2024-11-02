# Montagem de Circuito no TinkerCAD
**Descrição:** Neste tutorial, vamos aprender a montar um circuito no TinkerCAD para ligar e desligar LEDs. O objetivo é proporcionar uma base sólida em simulação de circuitos e componentes eletrônicos. Durante o processo, você adquirirá habilidades em simulação de circuitos e programação básica, ideal para iniciantes em eletrônica e programação que desejam explorar projetos práticos.

---

## Índice

1. [Introdução](#introdução)
2. [Requisitos](#requisitos)
3. [Configuração do Ambiente no TinkerCAD](#configuração-do-ambiente-no-tinkercad)
4. [Montagem do Circuito](#montagem-do-circuito)
5. [Configuração do Código](#configuração-do-código)
6. [Teste e Validação](#teste-e-validação)
7. [Referências](#referências)

---

## Introdução

Neste tutorial, vamos aprender a criar um circuito básico para ligar e desligar LEDs usando o TinkerCAD. Este projeto é ideal para iniciantes em eletrônica, proporcionando uma base sólida no entendimento de circuitos e componentes eletrônicos.

---

## Requisitos

### Hardware
- **Placa**: Arduino
- **Atuadores**: LEDs
- **Outros componentes**: Jumpers, resistores


### Software

- **Linguagens**: C/C++ para Arduino
- **IDE**: TinkerCAD (focado para simulação e montagem de circuitos)
- **Bibliotecas**: Não aplicável para simulação básica no TinkerCAD.
---

## Configuração do Ambiente no TinkerCAD

### Passo 1: Configuração Inicial

#### TinkerCAD: Configuração da Plataforma

1. **Criação da Conta**:
   - Acesse [TinkerCAD](https://www.tinkercad.com/) e crie uma conta gratuita.
   - Após o login, selecione "Circuits" no menu principal.

2. **Configuração do Projeto**:
   - Clique em "Create new Circuit".
   - Nomeie o seu projeto e selecione "Arduino" como sua placa principal.

## Montagem do Circuito

<div>
  <img align="center" height "180em" src="https://github.com/user-attachments/assets/461c4d0a-b90e-4bd0-ad75-44a6654f3a04" width="500"/>
<div>


#### Arduino no TinkerCAD

1. **Adicionar Componentes**:
   - Arraste e solte os componentes necessários, como LED, resistores e jumpers, para a área de trabalho.
   - Conecte o LED ao pino digital 13 do Arduino, passando por um resistor de 220 ohms.

## Configuração do Código**:
   - No TinkerCAD, clique em "Code" e selecione "Blocks + Text".
   - Utilize o código exemplo abaixo para ligar e desligar o LED:
     ```cpp
     const int buttonPin = 2;   
     const int ledPin =  13;
     void setup() {
        // put your setup code here, to run once:
        pinMode(buttonPin,INPUT);
        pinMode(ledPin, OUTPUT);

        }

        void loop() {
        // put your main code here, to run repeatedly:
        int pushbutton = digitalRead(buttonPin);

        if(pushbutton==HIGH)
            {
            digitalWrite(13,HIGH);
    
             }
        else
            {
            digitalWrite(13,LOW);
            }
  
        }

     ```

3. **Simulação**:
   - Clique em "Start Simulation" para testar seu circuito.
   - Observe o LED piscando conforme o código.

## Teste e Validação

### Testando Atuadores

1. **Verificação Inicial**:
   - Assegure-se de que todas as conexões estejam corretas no TinkerCAD.
   - Inicie a simulação no TinkerCAD e observe se o LED responde ao estado do botão conforme esperado.

2. **Consistência das Leituras**:
   - Pressione e solte o botão várias vezes para garantir que o LED liga e desliga corretamente a cada ação.
   - Monitore a estabilidade da simulação para detectar quaisquer falhas intermitentes.

### Validação dos Atuadores

1. **Funcionamento Correto**:
   - Verifique se o LED acende e apaga de acordo com a lógica programada no código.
   - Modifique o código para testar diferentes padrões de piscar e confirmar a resposta correta do LED.

### Monitoramento em Tempo Real

1. **Simulação Completa**:
   - Execute a simulação por um período prolongado para garantir que o circuito funcione de forma estável e contínua.
   - Ajuste a lógica conforme necessário para aprimorar a resposta e desempenho do circuito.

## Referências

- **Guia TinkerCAD**: [TinkerCAD Circuits](https://www.tinkercad.com/circuits)
- **Bibliotecas e IDEs**:
  - [Arduino IDE](https://www.arduino.cc/en/software)
  - [TinkerCAD Tutorials](https://blog.tinkercad.com/tag/circuit-tutorials)
- **Materiais Adicionais**:
  - [Documentação ESP32](https://docs.espressif.com/projects/esp-idf/en/latest/esp32/)
  - [Tutoriais de Programação em C/C++](https://www.learn-c.org/)
  - [Tutorial de Flutter](https://flutter.dev/docs/get-started/codelab)

