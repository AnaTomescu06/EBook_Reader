Proiect TSC 2025 – OpenBook
Descriere generală
OpenBook este un e-book reader portabil, conceput pentru a fi eficient energetic, accesibil și ușor de reprodus. La baza sa se află microcontrolerul ESP32-C6, care coordonează funcționarea tuturor componentelor.


Funcționalitate hardware
OpenBook este un e-book reader bazat pe tehnologie e-paper, alimentat de la o baterie Li-Po și construit în jurul modulului ESP32-C3-WROOM. Dispozitivul are capacitatea de a monitoriza parametrii de mediu (temperatură, umiditate, dioxid de carbon și particule fine), de a salva aceste date pe un card microSD și de a le afișa pe un ecran e-paper cu consum redus.

ESP32-C3-WROOM
Reprezintă unitatea centrală de control, dotată cu conectivitate Wi-Fi și Bluetooth Low Energy.

Suportă interfețele SPI, I2C și UART pentru conectarea componentelor externe.

Este alimentat la 3.3V, tensiune furnizată de un stabilizator LDO.

Sistem de alimentare
Portul USB-C este utilizat atât pentru alimentare, cât și pentru comunicare.

Încărcarea bateriei Li-Po este gestionată de circuitul integrat MCP73832.

Un stabilizator LDO 3.3V furnizează tensiunea necesară pentru ESP32 și alte componente logice.

Un convertor DC-DC 5V asigură alimentarea senzorilor care necesită o tensiune mai ridicată, precum cei de CO₂ și PM.

Senzori de mediu
BME680: senzor multi-funcțional pentru măsurarea temperaturii, umidității și compușilor gazoși volatili (VOC); comunică prin I2C și este alimentat la 3.3V.

MH-Z19B: senzor de dioxid de carbon (CO₂), funcționează la 5V și comunică prin UART.

PMSA003: senzor pentru particule în suspensie (PM2.5), comunică prin UART și este alimentat la 5V.

Ecran
Ecran e-paper monocrom de 1.5”, cu o rezoluție de 200x200 pixeli.

Este conectat prin interfață SPI, împărțind magistrala cu cardul SD.

Card microSD
Modul pentru stocarea datelor de mediu sau a fișierelor text (ex. eBook-uri).

Comunică prin SPI cu microcontrolerul.

Interfață de control
Trei butoane tactile, conectate la pini GPIO, permit interacțiunea cu utilizatorul (ex. navigare prin meniu, actualizare ecran).
