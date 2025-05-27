
# 📦 Entorno de trabajo para sistemas Linux

Configuración de un entorno de trabajo eficiente en Linux, con ZSH, Kitty, fuentes Nerd y utilidades modernas (lsd, bat). Este entorno proporciona un flujo de trabajo más visual, productivo y cómodo.

---

## 🔹 Instalación de herramientas esenciales

### 📂 7zip
Instalamos 7zip para manejar archivos comprimidos:
```bash
sudo apt install p7zip-full
```


### 📦 lsd (LSDeluxe)
Lsd (abreviatura de LSDeluxe) es un reemplazo moderno para el tradicional comando ls de Unix, diseñado para mejorar la visualización de los archivos en la terminal.
```bash
sudo apt install lsd
```
🔗 Más info: https://github.com/lsd-rs/lsd


### 📦 batcat (bat)
Batcat es la versión distribuida en Debian y Ubuntu del programa bat, una herramienta de línea de comandos que sirve como una versión mejorada del clásico comando cat de Unix.
```bash
sudo apt install bat
```
🔗 Más info: https://github.com/sharkdp/bat


---

## 💻 Terminal ZSH
Instalamos ZSH como shell avanzado:
```bash
sudo apt install zsh
```

---

### 🔤 Hack Nerd Fonts
Instalamos Hack Nerd Fonts para mejorar la visualización en terminales:

1. Nos dirigimos al directorio de fuentes:
```bash
cd /usr/local/share/fonts
```

2. Descargamos la fuente desde [Nerd Fonts](https://www.nerdfonts.com/font-downloads).

3. Movemos el archivo descargado:
```bash
sudo mv ~/Descargas/Hack.zip .
```

4. Descomprimimos:
```bash
7z x Hack.zip
```

5. Eliminamos archivos innecesarios:
```bash
rm Hack.zip LICENSE.md README.md
```

---

## 🐱 Kitty - Instalación y Configuración

### 🔸 Instalación rápida (repositorio oficial, versión estable)
```bash
sudo apt install kitty
```

### 🔸 Instalación desde la última release en GitHub
Kitty es un emulador de terminal moderno y acelerado por GPU.

1. Descargamos el último release:  
🔗 [Repositorio de Kitty](https://github.com/kovidgoyal/kitty)  
📥 `Linux amd64 binary bundle`

2. Descomprimimos en `/opt`:
```bash
cd /opt
sudo 7z x ~/Descargas/kitty-<version>-x86_64.txz
```

3. Creamos un directorio y movemos los archivos:
```bash
sudo mkdir kitty
sudo mv kitty-<version>-x86_64.tar kitty/
cd kitty
sudo tar -xf kitty-<version>-x86_64.tar
sudo rm kitty-<version>-x86_64.tar
```

4. Confirmamos la instalación:
```bash
/opt/kitty/bin/kitty -v
```

### 🔸 Añadir Kitty al PATH
```bash
echo 'export PATH="/opt/kitty/bin:$PATH"' >> ~/.bashrc    # Para bash
echo 'export PATH="/opt/kitty/bin:$PATH"' >> ~/.zshrc     # Para zsh
```
Recargamos la configuración:
```bash
source ~/.bashrc    # Para bash
source ~/.zshrc     # Para zsh
```

### 🔸 Crear un lanzador de escritorio para Kitty
1. Editamos o creamos el archivo:
```bash
nano ~/.local/share/applications/kitty.desktop
```

2. Contenido del archivo:
```ini
[Desktop Entry]
Version=1.0
Type=Application
Name=Kitty Terminal
GenericName=Terminal Emulator
Comment=Fast, feature-rich, GPU based terminal
Exec=/opt/kitty/bin/kitty
Icon=/opt/kitty/share/icons/hicolor/256x256/apps/kitty.png
Categories=System;TerminalEmulator;
Terminal=false
StartupWMClass=kitty
```

3. Hacemos ejecutable el lanzador:
```bash
chmod +x ~/.local/share/applications/kitty.desktop
```

4. Actualizamos el caché de aplicaciones:
```bash
update-desktop-database ~/.local/share/applications/
```

### 🔸 Configurar Kitty
1. Accedemos al directorio de configuración:
```bash
cd ~/.config/kitty
```

2. Creamos y editamos `kitty.conf` y `color.ini` (disponibles en este repositorio).

3. Recargamos Kitty para aplicar cambios.

### 🔸 Copiar configuración a root (opcional)
```bash
sudo mkdir -p /root/.config/kitty
sudo cp ~/.config/kitty/* /root/.config/kitty/
```

---

## 🐚 Configuración avanzada de ZSH

### 🔸 Configurar ZSH (Z Shell)
1. Instalación de pluggins:
```bash
git clone https://github.com/zsh-users/zsh-autosuggestions ~/.zsh/zsh-autosuggestions
echo "source ~/.zsh/zsh-autosuggestions/zsh-autosuggestions.zsh" >> ~/.zshrc
```
```bash
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ~/.zsh/zsh-syntax-highlighting
echo "source ~/.zsh/zsh-syntax-highlighting/zsh-syntax-highlighting.zsh" >> ~/.zshrc
```
```bash
git clone --depth 1 -- https://github.com/marlonrichert/zsh-autocomplete.git ~/.zsh/zsh-autocomplete
echo "source ~/.zsh/zsh-autocomplete/zsh-autocomplete.plugin.zsh" >> ~/.zshrc
```

2. Recargamos la configuración ZSH:
```bash
source ~/.zshrc
```

3. Activamos la shell ZSH en nuestros usuarios:
```bash
usermod --shell /usr/bin/zsh root
usermod --shell /usr/bin/zsh eduard
```

### 🔸 Instalación Powerlevel10k
```bash
git clone --depth=1 https://github.com/romkatv/powerlevel10k.git ~/powerlevel10k
echo 'source ~/powerlevel10k/powerlevel10k.zsh-theme' >>~/.zshrc
```

Cambiamos la ruta de powerlevel10k a absoluta:
```bash
vim ~/.zshrc
```

Instalación de powerlevel10k (abrirá el menú de configuración):
```bash
zsh
```

Editar configuración desde el archivo:
```bash
vim ~/.p10k.zsh
```

---

## 📁 Estructura del proyecto
```
.
├── README.md                # Guía de instalación y configuración
├── kitty/                   # Configuración para el terminal Kitty
├── zsh/                     # Configuración de ZSH
└── powerlevel10k/           # Configuración de Powerlevel10k para ZSH
```

---

## 🎉 Resultado final
Tendrás un entorno Linux optimizado, con:
- Terminal ZSH personalizado (Powerlevel10k)
- Kitty con fuentes Nerd y configuraciones avanzadas
- Utilidades modernas (`lsd`, `batcat`, `7zip`)
- Accesos rápidos y resaltado de sintaxis en terminal

![Entorno final](https://github.com/user-attachments/assets/3ff1ef98-8b14-43fc-b942-08d65cc2e35b)
