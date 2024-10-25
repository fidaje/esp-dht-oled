
# Monitoraggio Temperatura e Umidità con Arduino e Bot Telegram

Questo progetto utilizza un sensore **DHT11** per monitorare la temperatura e l'umidità, visualizzando i dati in tempo reale su un display **OLED** e consentendo l'accesso remoto alle letture tramite un bot di **Telegram**.

## Caratteristiche

- Misurazione della temperatura e dell'umidità con sensore DHT11.
- Visualizzazione dei dati sul display OLED SSD1306.
- Integrazione con un bot di Telegram per ottenere letture a distanza.
- Gestione della connessione Wi-Fi per un facile accesso a internet.
- Supporto per comando Telegram `/state` per visualizzare la temperatura e l'umidità attuali e `/start` per istruzioni.

## Componenti Necessari

- **Arduino con supporto WiFi** (es. ESP32)
- **DHT11** (sensore di temperatura e umidità)
- **Display OLED SSD1306**
- **Connessione WiFi**
- **Account Telegram** e un bot creato tramite BotFather per ricevere notifiche (includi il token del bot nel codice).

## Connessioni Hardware

1. Collega il sensore **DHT11** al pin **DHTPIN** definito nel codice (ad esempio, pin `2`).
2. Collega il display **SSD1306** all'ESP32 utilizzando i pin **SDA** e **SCL** per l'I2C.

## Installazione delle Librerie

Per eseguire questo progetto, assicurati di avere installate le seguenti librerie in **Arduino IDE**:

- `WiFi.h` e `WiFiClientSecure.h` (inclusi nella libreria di base ESP32).
- `UniversalTelegramBot.h` per la gestione delle richieste del bot Telegram.
- `ArduinoJson.h` per il parsing JSON.
- `Adafruit_Sensor.h`, `DHT.h` per il sensore DHT11.
- `Adafruit_GFX.h` e `Adafruit_SSD1306.h` per il display OLED.

## Configurazione del Codice

Prima di caricare il codice, configura le seguenti variabili nel file `.ino`:

- **WiFi**:
  ```cpp
  #define WIFI_SSID "YOUR_WIFI_SSID"
  #define WIFI_PASSWORD "YOUR_WIFI_PASSWORD"
  ```

- **Bot Telegram**:
  ```cpp
  #define BOT_TOKEN "YOUR_BOT_TOKEN"
  ```

## Utilizzo

1. **Connessione WiFi**: Dopo aver avviato il dispositivo, l'ESP32 tenterà di connettersi alla rete WiFi configurata.
2. **Visualizzazione su OLED**: I dati della temperatura e dell'umidità saranno mostrati sul display OLED in tempo reale.
3. **Bot Telegram**: Usa i seguenti comandi per interagire con il bot:
   - `/start`: Riceverai un messaggio di benvenuto e una guida all'uso.
   - `/state`: Riceverai la temperatura e l'umidità attuali.

## Schermate

Il display OLED visualizza:
- Un’icona di stato per indicare in tentativo di connessione.
- **Temperatura** e **Umidità** in grandi caratteri per una lettura immediata.


## Funzioni Principali del Codice

- **Connessione WiFi**: gestita in fase di `setup()`, la connessione viene monitorata con messaggi sul serial monitor.
- **Lettura DHT11**: il sensore misura temperatura e umidità; i valori letti vengono inviati sia al display OLED sia al bot Telegram.
- **Aggiornamento Telegram**: la funzione `handleNewMessages()` verifica ogni secondo la presenza di nuovi messaggi e gestisce i comandi `/start` e `/state`.

