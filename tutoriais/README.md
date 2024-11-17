# Sistema de Monitoramento de Ar com Alerta e Controle

**Descrição:** O Sistema de Monitoramento de Ar com Alerta e Controle para Ambientes de Saúde foi desenvolvido com o objetivo de proporcionar um ambiente seguro e saudável para pessoas que se encontram em situações de risco devido a problemas respiratórios, como pacientes hospitalares, idosos, crianças ou indivíduos com condições pré-existentes, como asma ou doenças pulmonares crônicas. Este sistema utiliza tecnologia de sensores para monitorar a presença de gases nocivos no ambiente e adotar medidas corretivas automaticamente quando necessário.

---

## Índice

1. [Introdução](#introdução)
2. [Requisitos](#requisitos)
3. [Configuração do Ambiente](#configuração-do-ambiente)
4. [Montagem do Circuito](#montagem-do-circuito)
5. [Programação](#programação)
6. [Teste e Validação](#teste-e-validação)
7. [Expansões e Melhorias](#expansões-e-melhorias)
8. [Referências](#referências)

---

## Introdução

A principal função deste projeto é monitorar a qualidade do ar em tempo real e alertar os ocupantes do ambiente sobre a presença de gases nocivos, proporcionando uma resposta rápida para mitigar riscos à saúde. Quando detectado um nível elevado de gases perigosos, o sistema aciona um alarme sonoro, exibe mensagens de alerta no display LCD e ativa um mecanismo automático para a abertura de janelas ou ativação de sistemas de ventilação, garantindo assim a renovação do ar e a melhoria das condições respiratórias no ambiente

---

## Requisitos

### Hardware

- **Placa**: Arduino Uno.
- **Sensores**: Sensor de Gás (MQ-2)
- **Atuadores**: Buzzer Piezoelétrico, LED e Servo Motor.
- **Display**: LCD 16x2 com interface I2C.
- **Outros componentes**: Protoboard, Resistores, Jumpers e Fios

### Software

- **Linguagens**: C/C++ para programação do Arduino.
- **IDE**: Arduino IDE e Tinkercad.
- **Bibliotecas**: Servo.h e Adafruit_LiquidCrystal.h para controle do LCD e comunicação com os sensores.

---

## Configuração do Ambiente

### Passo 1: Instalação do Software
 
- **Arduino IDE:** Faça o download e instale o Arduino IDE acessando o site https://www.arduino.cc/en/software.
![imagem alt](https://github.com/sktapn/maloca-turma-ufrr-2023_Abrah-o/blob/Tutorial-2/tutoriais/download%20arduino.png?raw=true)

### Passo 2: Configuração das Placas
- **Configuração no Arduino:**
  1. Conecte a placa Arduino ao computador utilizando o cabo USB;
  2. Na IDE do Arduino, clique em "Select other board and port" (Selecionar outra placa e porta);
  3. Escolha a opção "Arduino Mega or Mega 2560";
  4. Por último, selecione a porta correta na IDE do Arduino. 
  ![imagem alt](https://github.com/sktapn/maloca-turma-ufrr-2023_Abrah-o/blob/Tutorial-2/tutoriais/arduino.png?raw=true)
---

## Montagem do Circuito

- **Junte a Placa Arduino Uno à protoboard para facilitar as conexões.**
- **Servo MoTOR**
1. x
2. x.
3. x
- **Sensor de Gás **
1. x
2. x
3. x
4. x
- **Display LCD 16x2 (I2C)**
1. Conecte o pino VCC do módulo I2C ao pino de 5V do Arduino.
2. Conecte o pino GND ao GND do Arduino.
3. Conecte o pino SDA ao pino A4 do Arduino.
4. Conecte o pino SCL ao pino A5 do Arduino.
- **LEDs**
1. X.
2. X.
- **Jumpers**:
1. X.
![imagem alt](https://github.com/sktapn/maloca-turma-ufrr-2023_Abrah-o/blob/Tutorial-3/tutoriais/T3_1.png?raw=true)

---

## Programação

### Passo 1: Configuração do Sistema

O sistema inicializa o LCD, servo motor, LED e buzzer. O LCD exibe uma mensagem inicial "Sistema Maloca" enquanto o servo motor é configurado para iniciar com a porta/janela fechada (0 graus). O sensor de gás é configurado para ler os níveis de concentração de gás e o pino do buzzer e LED são configurados para alerta.



```cpp
#include <Adafruit_LiquidCrystal.h>
#include <Servo.h>  // Inclui a biblioteca para o servo motor

// Definindo pinos para o sensor de gás, LED, buzzer e servo
const int gas_input = A0;
const int led = 6;
const int buzzer = 12;
int gas = 0;

// Configuração do Servo
Servo servoMotor;  // Cria um objeto Servo
const int servoPin = 3;  // Define o pino do servo

// Configuração do LCD
Adafruit_LiquidCrystal lcd_1(0x20);  // Substitua por 0x27 se necessário

void setup() {
  // Configurações de pinos
  pinMode(led, OUTPUT);
  pinMode(buzzer, OUTPUT);

  // Inicializando o Serial Monitor, LCD e Servo
  Serial.begin(9600);
  lcd_1.begin(16, 2);
  lcd_1.print("Sistema Maloca");  // Mensagem inicial
  delay(2000);  // Espera 2 segundos
  lcd_1.clear();

  // Configura o servo
  servoMotor.attach(servoPin);
  servoMotor.write(0);  // Inicialmente a porta/janela está fechada
}

```

### Passo 2: Processamento e Lógica de Cálculos e Exibição

O sistema lê continuamente o valor do sensor de gás. Se o nível de gás for superior a 150, o LCD exibe "ATENÇÃO" e "Portas e janelas abertas", e o buzzer emite um som de alerta enquanto o LED acende. O servo motor é acionado para abrir a porta/janela. Caso o nível de gás esteja seguro, o sistema desliga o buzzer, apaga o LED e exibe "Nível Seguro" no LCD, fechando a porta/janela novamente.

```cpp
void loop() {
  // Leitura do valor do sensor de gás
  gas = analogRead(gas_input);

  // Exibindo o valor do gás no Serial Monitor
  Serial.print("Gas Level: ");
  Serial.println(gas);

  // Verificando se o valor do gás excede o limite crítico (150)
  if (gas > 150) {
    // Exibindo a mensagem "ATENCAO" no LCD
    lcd_1.clear();
    lcd_1.setCursor(4, 0);  // Coluna 4, Linha 0 para centralizar "ATENCAO"
    lcd_1.print("ATENCAO");
    delay(2000);  // Espera 2 segundos

    // Exibindo a mensagem "Portas e janelas abertas" no LCD
    lcd_1.clear();
    lcd_1.setCursor(0, 0);  // Coluna 0, Linha 0
    lcd_1.print("Portas e janelas");
    lcd_1.setCursor(3, 1);  // Coluna 3, Linha 1
    lcd_1.print("abertas!");
    delay(2000);  // Espera 2 segundos

    // Exibindo as mensagens no Serial Monitor
    Serial.println("ATENCAO: Nivel Critico!");
    Serial.println("Portas e janelas abertas!");

    // Acionando o buzzer e o LED
    tone(buzzer, 1000);  // Frequência de 1000 Hz
    digitalWrite(led, HIGH);

    // Abrindo a porta/janela
    servoMotor.write(90);  // Gira o servo para 90 graus para abrir
  } else {
    // Se o nível de gás estiver seguro, desligar buzzer e LED
    noTone(buzzer);
    digitalWrite(led, LOW);

    // Limpar o LCD e centralizar a mensagem "Nivel Seguro"
    lcd_1.clear();
    lcd_1.setCursor(3, 0);  // Coluna 3, Linha 0 para centralizar "Nivel Seguro"
    lcd_1.print("Nivel Seguro");

    // Fechando a porta/janela
    servoMotor.write(0);  // Retorna o servo para 0 graus para fechar
  }

  // Pequeno atraso para a próxima leitura
  delay(500);
}

```
---

## Teste e Validação


- **Testar o Sensor de Gás:** Exponha o sensor de gás a uma concentração conhecida de gás ou fumaça e verifique se o valor lido no monitor serial corresponde ao esperado. Certifique-se de que o valor de leitura (variando de 0 a 1023) reflete corretamente a concentração de gás no ambiente.

- **Testar o Funcionamento do LCD:** Verifique se as mensagens "Sistema Maloca", "ATENÇÃO", "Portas e janelas abertas", e "Nível Seguro" estão sendo exibidas corretamente no LCD. Certifique-se de que as mensagens estão centralizadas conforme o esperado e são alteradas corretamente dependendo do nível de gás detectado.

- **Testar o Buzzer:** Aplique uma concentração de gás que faça o valor ultrapassar 150 e verifique se o buzzer emite o som corretamente. Verifique também se o buzzer desliga quando o nível de gás voltar ao seguro, após o sensor registrar um valor abaixo de 150.

- **Testar o LED:** Quando o nível de gás atingir um valor crítico (acima de 150), o LED deve acender. Quando o nível de gás voltar a ser seguro (abaixo de 150), o LED deve apagar. Verifique se o LED responde adequadamente a essas mudanças.

- **Testar o Servo Motor:** Quando o nível de gás for crítico, o servo motor deve mover-se para 90 graus, simulando a abertura da porta/janela. Quando o nível de gás for seguro, o servo motor deve voltar para a posição inicial (0 graus), simulando o fechamento da porta/janela. Certifique-se de que o movimento do servo ocorre sem falhas.

- **Monitor Serial:** Verifique se o valor do gás lido pelo sensor e as mensagens de alerta ("ATENÇÃO: Nível Crítico!" e "Portas e janelas abertas!") estão sendo impressos corretamente no monitor serial. Isso ajudará a monitorar o comportamento do sistema durante os testes.
---
![imagem alt](https://github.com/sktapn/maloca-turma-ufrr-2023_Abrah-o/blob/Tutorial-3/tutoriais/T3_2.png?raw=true)
![imagem alt](https://github.com/sktapn/maloca-turma-ufrr-2023_Abrah-o/blob/Tutorial-3/tutoriais/T3_3.png?raw=true)
![imagem alt](https://github.com/user-attachments/assets/a6b198ee-3a62-430d-827b-1efbe83df590)
![imagem alt](https://github.com/sktapn/maloca-turma-ufrr-2023_Abrah-o/blob/Tutorial-3/tutoriais/T3_Terminal.png?raw=true)

## Expansões e Melhorias

Sugestões para melhorar o projeto, como:

- **Implementação de Alerta Remoto via Wi-Fi:** Integrar um módulo Wi-Fi como o ESP8266 ou ESP32 para enviar notificações de alerta (por exemplo, via e-mail ou aplicativo de mensagens) quando o nível de gás atingir um valor crítico. Isso permite que os responsáveis sejam notificados, mesmo que não estejam no local.
- **Adicionar um Sensor de Temperatura e Umidade:** Incorporar um sensor de temperatura e umidade, como o DHT11 ou DHT22, para monitorar as condições ambientais do ambiente. Isso pode ser útil para alertar o usuário caso a temperatura ou umidade atinja valores fora do padrão, podendo contribuir para a segurança, especialmente em ambientes fechados.
---

## Referências

- Link simulação: https://www.tinkercad.com/things/i6KvDVZZO4X-tutorial-5?sharecode=ruv4A0o9XUV4-9le0fIHyow5g_I2eABiycRlFDVPEoIsharecode=aCFzLU7Zibd8mRkQ5pw7I1kYj_9DKlnJC2mFIFggUw4
- ArduinoIDE: https://www.arduino.cc/
- Tinkercad: https://www.tinkercad.com/

---

