# CP4 – Vinherias com Cloud IoT (ESP32 + DHT22 + Potenciômetro → ThingSpeak)

PoC no Wokwi que lê temperatura/umidade (DHT22) e simula “luminosidade” com um potenciômetro (0–100%).
Envia para o ThingSpeak nos fields: field1=Temperatura, field2=Umidade, field3=Luminosidade (simulada).

## Links
- Wokwi: https://wokwi.com/projects/441109044689648641
- Vídeo: https://youtube.com/watch?v=bQCpf6vmUY4&feature=youtu.be

## Componentes
- ESP32 DOIT DevKit V1
- DHT22 (temperatura/umidade)
- Potenciômetro (simula luminosidade)

## Pinagem
DHT22
- VCC → 3V3
- GND → GND
- DATA → GPIO15

Potenciômetro
- Terminal 1 → 3V3
- Terminal 2 (meio) → GPIO34
- Terminal 3 → GND

## ThingSpeak (canal)

1) Channels > New Channel
   - Field 1: Temperature (°C)
   - Field 2: Humidity (%)
   - Field 3: Luminosity (%)

2) API Keys > copie a Write API Key
   - Cole no código: const char* apiKey = "SUA_WRITE_KEY";

## Como executar (Wokwi)

1) Abrir o link do Wokwi e clicar em Run.
2) Serial Monitor mostra conexão e leituras.
3) ThingSpeak: ver gráficos dos Fields 1, 2 e 3.

## Observações do código

- Sensor: #define DHTTYPE DHT22 (DATA no GPIO15)
- “Luminosidade”: leitura analógica no GPIO34 (potenciômetro), mapeada 0–100%.
- Envio: HTTP GET para http://api.thingspeak.com/update com field1/2/3.
- Rate limit do ThingSpeak: ≥ 15 s (para publicar sem “0”, troque delay(2500) por delay(16000)).


## Integrantes
- Matheus da Costa Barroso
