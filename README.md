# The Ultimate ESP32 Hacking Tool: ¡Porque a veces sólo necesitas ser un poco malvado!
### ¿Buscas tumbar la red wifi de tu vecino? ¿O simplemente quieres causar el caos en tu cafetería local? ¿O tu jefe te paga menos de lo que mereces?
No busques más, porque tenemos la herramienta perfecta para ti: ¡la herramienta de hacking ESP32!

## Features
### CLI & Display version
- Wifi Beacon Spammer**: Con nuestra función de spam de balizas, puedes inundar la zona con señales wifi falsas y confundir a cualquiera que intente conectarse a una red legítima.
- WiFi Deauther**: Y cuando las cosas se pongan demasiado aburridas, utiliza nuestra función deautomatización para desconectar a alguien de Internet en un instante. Es como una versión digital de tirar del enchufe en su router. Y no, no es un bloqueador de WiFi, es un deauther. ¿No sabes la diferencia? sólo google script kiddie.
- **Captive Portal**: Nuestra función de portal cautivo le permite redirigir todas las conexiones entrantes a una página de destino personalizada, donde puede recopilar información de inicio de sesión. Puede elegir entre una página de inicio de sesión de Google o una página de WiFi gratuito de McDonald's. ¿Por qué McDonald's? ¡Porque a partir de ahora puedes ganar puntos de recompensa McDonalds como un hacker gordo pero valiente para otras personas!
- **Evil Twin**: Nuestro ataque Evil Twin crea una réplica de otra red WiFi que también se desautentica permanentemente, por lo que no puedes conectarte a la red original. Si ahora te conectas a la wifi falsa, se abre una página de inicio de sesión del router falsa, que te dice que la contraseña del router ha caducado. si finalmente recibes la contraseña compleja de tu vecino de 80 años, puedes informarle de que "0123456789" no es la contraseña más segura.
- **WiFi Scanner**: Busca redes WiFi cercanas y su bssid, canales e intensidad de señal.
- **BLE Spoof**: ¿Estás sin blanca pero quieres flexionar con los AirPods como un niño rico? No temas, la doble imitación es la herramienta de flexión perfecta. Spoof dispositivos de Apple, Google, Samsung y Microsoft. (Algunos dispositivos de Apple son incluso estrellarse)
- ### CLI version only
- **HTTP-Request**
- **ModBus-Request**
- **UPD-Request**
- **ARP-Request**

## CLI (Terminal) version
Experimenta una interfaz similar a la de un Terminal convencional.
Tus comandos recientes se almacenan y se recuperan fácilmente mediante las teclas de flecha, y puedes autocompletar pulsando tabulador.
### **NOTA IMPORTANTE**: Asegúrese de que su monitor de serie es compatible con los códigos de escape para garantizar una visualización de salida precisa.
Si eres usuario de Windows (mis condolencias 🥲). CMD no muestra la salida correctamente. Como alternativa, considere el uso de Putty o un programa similar.
**Instrucciones para usuarios de Mac/Linux**:
- Si ya tienes esp-idf instalado, simplemente usa idf.py monitor.
- Si no, recomiendo usar cu:
1. Determine el puerto serie introduciendo **`ls /dev/cu*`** en el terminal.
2. Para abrir el monitor serie, escriba **`sudo cu -s 115200 -l <serial_port>`**.
3. Para salir del monitor serie, teclee **`~.`**.

**Instrucciones para usuarios de Windows**:
- En primer lugar, descarga e instala Putty.
1. Identify your Serial COM Port in the device manager.
2. In Putty, select 'Serial' as the connection type.
3. Input your COM Port in the 'Serial line' field.
4. Set the speed to 115200 and click 'Open' to start the session.

### Demonstration
For the full video press on the gif or click this [link](https://www.youtube.com/watch?v=y9GyKebK8XY)

[![HackingTool ClI Demo](https://i.imgur.com/HdnUQXB.gif)](https://www.youtube.com/watch?v=y9GyKebK8XY)

## Handheld display version
![image](https://i.imgur.com/aPWmspx.jpeg)

## How to flash firmware
If you know what you do, and even want to add custom features:
1. download the esp idf toolchain (IMPORTANT: idf-version must be 4.3.2) and the esp32-hacking-tool
2. connect your esp32 to your computer
3. open a terminal and navigate to the esp32-hacking-tool folder
4. run idf.py build flash

or just use the precompiled bin file and flash it with esptool
1. connect your esp32 to your computer
2. To make sure to "clean" your esp32 just run  
   **Mac/Linux**: esptool.py -p /dev/cu."PORT" erase_flash  
   **Windows**: esptool.py -p COM"PORT" erase_flash
3. open a terminal and navigate to the esp32_hackingtool/precompiled_files folder and run following command:  
  **Mac/Linux:** esptool.py -p /dev/cu.usbserial-<PORT> -b 1200000 --before=default_reset --after=hard_reset write_flash --flash_mode dio --flash_freq 80m --flash_size 4MB 0x8000 partition-table.bin 0x1000 bootloader.bin 0x20000 hackingtool.bin  
  **Windows**: esptool.py -p COM<PORT> -b 1200000 --before=default_reset --after=hard_reset write_flash --flash_mode dio --flash_freq 80m --flash_size 4MB 0x8000 partition-table.bin 0x1000 bootloader.bin 0x20000 hackingtool.bin

or for newbies use [this](https://esp.huhn.me) amazing website from [Spacehuhn](https://spacehuhn.com)
1. Download all files from esp32_hackingtool/precompiled_files folder.
2. Open [this Website](https://esp.huhn.me).
3. Press connect and choose your esp32 from the list
4. Enter offset of 0x1000 for the bootloader.bin file
5. Offset of 0x8000 for partition-table.bin
6. And offset of 0x20000 hackingtool.bin
7. Click PROGRAM

## Hardware Requirements
- You can use any ESP32 equipped with a minimum of 4MB of flash memory. External RAM is not required, as only internal RAM is utilized.
- For the display version I used the TTGO T-Display [AliExpress](https://aliexpress.com/item/33050639690.html?algo_pvid=f3353b8c-edf0-4bca-8686-7e315f706d40&algo_exp_id=f3353b8c-edf0-4bca-8686-7e315f706d40-0&pdp_ext_f=%7B%22sku_id%22%3A%2212000022706983282%22%7D&pdp_npi=2%40dis%21EUR%2115.33%2114.41%21%21%21%21%21%402101e9d116721750836725640e9b03%2112000022706983282%21sea) or if you are rich and impatient [Amazon](https://www.amazon.de/Wireless-Bluetooth-T-Display-Entwicklungsplatine-Arduino/dp/B09WHS11BK/ref=sr_1_3?crid=1KVYX4CZDSRJS&keywords=ttgo+esp32&qid=1672175654&sprefix=ttgo+%2Caps%2C218&sr=8-3). Apparently, you can use probably every ESP32 board with an OLED display, simply change the pin definitions in the menuconfig.

## Extra Information
The code is fully written in the ESP-IDF framework, with a little API, so you may easily add new features.

Since I am not allowed to code stuff like this at my job, I decided to create this project in my free time (If you want to support me you can buy me a [coffee](https://www.buymeacoffee.com/kl0ibi)). I hope you enjoy it as much as I did creating it. If you have any questions or ideas, feel free to create issues or even better pull requests. I will try to answer them as soon as possible.
If I have more time, I will add some more features to this project, here are some ideas:

### Future plans
- Create a simply version of the CLI without escape commands
- Add POST, PUT... for networktools-request
- Add ModBus Write for networktools-request
- Add Port Scanner for networktools-request
- Add Ping for networktools-request
- Add IR-Module
- Implement sniffer tools
- Implement more bluetooth tools
- Add a nfc module to read and write nfc tags


### Disclaimer: This project is for educational purposes only. I am not responsible for any damage you cause with this tool. Use it at your own risk. No animals were harmed during the development of this project.
