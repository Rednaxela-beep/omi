# omiGlass - Open Source Meta Raybans with 6x of their battery

<p align="center">
<img src="https://github.com/user-attachments/assets/848f664b-183e-4df5-8928-f16f00ff144b" width="45%">
   <img src="https://github.com/user-attachments/assets/3fa00359-74a0-4f85-a233-f4bf12b1db7b" width="45%">
</p>




<p align="center">
  <a href="https://x.com/kodjima33/status/1911852469329727811">
    <img src="https://img.youtube.com/vi/QvFjXgLZX7U/maxresdefault.jpg" alt="Watch the video" width="400"/>
  </a>
  <br>
  <a href="https://x.com/kodjima33/status/1911852469329727811">▶️ Watch Video</a>
</p>


## Want a Pre-built Version?

We will ship a limited number of pre-built kits. Get a Dev [kit here](https://omi.me/glass)

## Community

Join the [Based Hardware Discord](https://discord.gg/omi) for setup questions, contribution guide, and more.

## Getting Started

Follow these steps to set up omiglass:

### Buying guide
   - [Seeed Studio XIAO ESP32 S3 Sense](https://www.amazon.com/dp/B0C69FFVHH/ref=dp_iou_view_item?ie=UTF8&psc=1)
   - x6 150mah batteries like [this](https://a.co/d/i17DjOr) or at least like [this](https://a.co/d/bbFdkic) (but you'll need to increase the size of the casing)
   - 1x 250mah battery like [this](https://a.co/d/2xheiFC)
   - switch like [this](https://a.co/d/gJbWdKn) + [wires](https://a.co/d/ah98wY0) + hinges



### Software

1. Prerequisites
   You need to install Web Application on Linux machine to use OmiGlass. Ubuntu 24 or Debian 12 recommended.
   Install the requered pakages:
    ```
    apt install -y npm
    snap install ollama
    ```
3. Clone the omiglass repository and install the dependencies:

   ```
   git clone https://github.com/BasedHardware/omi.git
   cd omi/omiGlass
   npm install
   ```

   You can also use **yarn** to install, by doing

   ```
   yarn install
   ```

4. Add API keys for Groq and OpenAI into the [keys.ts file](https://github.com/BasedHardware/omi/blob/main/omiGlass/sources/keys.ts).
   Also add URL For the [Ollama](https://github.com/ollama/ollama) self-host REST API. The URL should be http://localhost:11434/api/chat
   <details>
   <summary>Click to understand how to do that</summary>
   Groq API Key
   
      Go to [GroqCloud](https://console.groq.com/login) and sign up.
      After logging in, create an API key in the API Access section.
      Use this key in keys.ts to interact with the Groq API.
   
   OpenAI API Key

   Sign up or log in at OpenAI.
   Navigate to the API Keys section in your account.
   Generate a new API key and add it to keys.ts.
   
   Once you have your keys, ensure they are correctly set the environments for the keys.ts:

   Create '.env' file at the omi/omiGlass directory:

   ```
   nano .env
   ```
Place here your API Keys and save the file:
```
   EXPO_PUBLIC_GROQ_API_KEY=your_groq_api_key
   EXPO_PUBLIC_OLLAMA_API_URL=http://localhost:11434/api/chat
   EXPO_PUBLIC_OPENAI_API_KEY=your_openai_api_key
```            
   </details>

4. For Ollama, self-host the REST API from the repository at [https://github.com/ollama/ollama](https://github.com/ollama/ollama) and add the URL to the `keys.ts` file. The URL should be http://localhost:11434/api/chat

5. Pull the Ollama self-host the REST API
   ```
   ollama pull moondream:1.8b-v2-fp16
   ```

7. Start the application:

   ```
   npm start
   ```

   If using **yarn** start the application with

   ```
   yarn start
   ```
   
8. Open Web version
   
   Note: This is an Expo project. For now, open the localhost link (this will appear after completing step 7) to access the web version.

- [ ] Connect glasses with omi app. Currently the glasses only work with web interface

### Hardware


1. 3D print the glasses mount case using the provided STL file located in hardware folder.
2.  Put components like this
   
<p align="center">
  <img src="https://github.com/user-attachments/assets/45ef303b-0f92-43eb-bfad-1b20a86e948c" width="45%" />
  <img src="https://github.com/user-attachments/assets/3fa00359-74a0-4f85-a233-f4bf12b1db7b" width="45%" />
</p>

How you can contribute in hardware: 
- [ ] Redesign the legs/sides so that it would fit on bigger heads
- [ ] add a switch into design (current design is without switch)

### Firmware
1. Download the 'firmware.ino' from the [firmware folder](https://github.com/BasedHardware/omi/tree/main/omiGlass/firmware) and open  in the Arduino IDE. Note that '.ino' file needs to be inside on 'firmware' folder before opening it.
https://git-scm.com/downloads/win
   - If you don't have the Arduino IDE installed, download and install it from the [official website](https://www.arduino.cc/en/software).
   - Alternatively, follow the steps in the [firmware readme](firmware/readme.md) to build using `arduino-cli`

4. Follow the software preparation steps to set up the Arduino IDE for the XIAO ESP32S3 board:

   - Add ESP32 board package to your Arduino IDE:
     - Navigate to File > Preferences, and fill "Additional Boards Manager URLs" with the URL: `https://raw.githubusercontent.com/espressif/arduino-esp32/gh-pages/package_esp32_index.json`
     - Navigate to Tools > Board > Boards Manager..., type the keyword `esp32` in the search box, select the latest version of `esp32`, and install it.
   - Select your board and port:
     - On top of the Arduino IDE, select the port (likely to be COM3 or higher).
     - Search for `xiao` in the development board on the left and select `XIAO_ESP32S3`.

5. Before you flash go to the "Tools" drop down in the Arduino IDE and make sure you set "PSRAM:" to be "PSRAM: "OPI PSRAM"

![Like this](image.png)

4. Upload the firmware to the XIAO ESP32S3 board.


## License

This project is licensed under the MIT License.
