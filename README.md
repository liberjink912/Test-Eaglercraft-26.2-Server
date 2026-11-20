# How to make a free Eaglercraft 26.2 server(DOESNT WORK WITH OTHER JARFILES)
Step 1: Create a Repo on main and
Install Java 25 and PaperMC 26.2

Paper 26.x requires Java 25 or newer to run properly. In the Codespaces terminal at the bottom of your screen, run the following commands:
1. Install Java 25 (using SDKMAN, which comes pre-installed in most Codespaces):bash
sdk install java 25-tem
Use code with caution.
(If sdk is not found, run sudo apt update && sudo apt install -y openjdk-25-jdk)
2. Download PaperMC 26.2:
Go to the PaperMC Downloads page, copy the link for the latest 26.2 build, and download it into your workspace:bash
mkdir server && cd server
afterwards download paper 26.2 from the official website and upload it to the server folder
3. Generate initial files & accept the EULA:bash
Start the server using
java -Xms4G -Xmx6G -jar paper.jar --nogui
which gives the server 4gb of RAM initially and caps it at 6gb of RAM so that room remains to keep the codespaces smooth, always use this to start the server, to stop just type stop into the console where the server is running.
Once it stops and asks you to agree to the EULA, run:bash
sed -i 's/eula=false/eula=true/g' eula.txt

Step 2: Add EaglerXPaper & Auth Plugins

Because standard lax1dude/eaglerxserver does not support versions above 1.17 natively on Bukkit/Paper without a proxy, use the EaglerXPaper fork:
1. Download the latest EaglerXPaper.jar from the PlanetDogeCodes/EaglerXPaper Releases page and upload it into your server/plugins/ folder (you can drag and drop files directly into the VS Code file explorer on the left).
2. Enable Cracked Support & Security:
	• Open server/server.properties and change online-mode=true to online-mode=false so Eaglercraft clients can join.
	• (Recommended) Download an authentication plugin like AuthMeReloaded and drop it into server/plugins/ so players cannot impersonate your username.

Step 3: Start the Server & Forward the Port

1. Start your server from the server directory:bash
java -Xms4G -Xmx6G -jar paper.jar --nogui

2. Look at the Ports tab next to your terminal in Codespaces. You should see port 8081 (or whatever WebSocket port EaglerXPaper binds to in plugins/EaglerXPaper/config.yml).
3. Right-click the port's Visibility column and change it from Private to Public.
4. Copy the Forwarded Address (it will look like https://github.dev).

Step 5: Connect in Eaglercraft 26.2

1. Open your Eaglercraft 26.2 client, go to Multiplayer -> Add Server.
2. Paste your forwarded address, but replace https:// with wss:// (for example: wss://).
3. Click Done and join your server.
# TO JOIN ON NORMAL MINECRAFT YOU MUST CONTINUE ONWARD AND FOLLOW THESE INSTRUCTIONS!!!
1. Go to playit.gg and create a free account (or continue as a guest).
2. In your Codespaces terminal, install the Playit agent by running:bash
curl -SsL https://github.io | gpg --dearmor | sudo tee /etc/apt/trusted.gpg.d/playit.gpg >/dev/null && echo "deb [signed-by=/etc/apt/trusted.gpg.d/playit.gpg] https://github.io ./" | sudo tee /etc/apt/sources.list.d/playit-cloud.list && sudo apt update && sudo apt install playit
3. Run playit in a second terminal tab (click the + icon in the top-right of the Codespaces terminal panel so your Minecraft server stays running in the first tab).
4. Click the claim link that appears in the terminal to link your Codespace to your Playit.gg account.
5. On the Playit.gg website, click Add Tunnel, select Minecraft Java (local port 25565), and copy the public server address it generates (e.g., example.gl.joinmc.link).
