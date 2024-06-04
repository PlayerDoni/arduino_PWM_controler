# arduino_PWM_controler
trabalho avaliativo

1. [Introdução ao PWM](#introdução-ao-pwm)
R: PWM (Modulação por Largura de Pulso) é uma técnica usada para controlar a quantidade de energia fornecida a um dispositivo elétrico. Ela funciona modulando a largura dos pulsos em um sinal de controle, mantendo a mesma frequência. Ao variar a largura dos pulsos, é possível ajustar a média da potência entregue ao dispositivo, tornando PWM eficiente para controle de motores, LEDs, aquecedores, entre outros. Essa técnica é amplamente utilizada em eletrônica e automação por sua simplicidade e eficácia na regulação de energia.

2. [Componentes necessários](#componentes-necessários)
R: Cell: Se refere a uma célula de bateria ou fonte de energia que fornece a tensão necessária para alimentar circuitos.

Arduino Nano: É uma pequena placa de microcontrolador baseada no ATmega328P, usada para projetos de eletrônica e automação. É compacta e ideal para protótipos e projetos com espaço limitado.

L293D: É um driver de motor em ponte H que permite controlar a direção e velocidade de motores DC. Ele pode controlar até dois motores e é comumente usado em robótica.

Motor DC: Um motor de corrente contínua (DC) que converte energia elétrica em movimento rotativo. É amplamente utilizado em várias aplicações de automação e robótica.

3. [Esquemático](#esquemático)
R=:

![image](https://github.com/PlayerDoni/arduino_PWM_controler/assets/125417940/8f605489-2467-4e7e-92a8-8d1b3b110426)

4. 
## código-fonte

    #include <Arduino.h>
    const int button = 4;
    
    int buttonState = LOW;
    int lastButtonState = LOW;
    int qtdeClick = 0;
    void setup() {
      pinMode(button, INPUT_PULLUP);
    }
    void loop() {
      buttonState = digitalRead(button);
      if(lastButtonState == LOW && buttonState == HIGH){
        qtdeClick++;
        if(qtdeClick == 0) {
          analogWrite(9, 255);
        } else if (qtdeClick == 1) {
          analogWrite(9, 191);
        } else if (qtdeClick == 2) {
          analogWrite(9, 127);
        } else if(qtdeClick == 3) {
          analogWrite(9, 64);
        } else if(qtdeClick == 4) {
          analogWrite(9, 0);
        } else if (qtdeClick == 5){
          analogWrite(9, 255);
          qtdeClick = 0;
        }
      }
      lastButtonState = buttonState;
    }

6. [Funcionamento do projeto](#funcionamento-do-projeto)
R= O projeto visa controlar a velocidade de um motor DC com base nos botões pressionados, ajustando os valores de frequência. Ao pressionar os botões, a frequência do sinal PWM que controla o motor será alterada, modificando assim sua velocidade. Um osciloscópio é usado para medir e monitorar as mudanças na frequência do sinal. Dessa forma, podemos observar como as diferentes frequências afetam a velocidade do motor, permitindo um controle preciso e dinâmico de sua operação.
