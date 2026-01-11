# Creating a Linux Executable for Excalidraw

A simple guide to create a custom terminal command to launch Excalidraw open source whiteboard.

## Purpose
Start Excalidraw by typing `start-excalidraw` in the terminal instead of navigating to the folder and running npm commands manually.

## Prerequisites
- Git installed
- Node.js and npm installed
- Excalidraw cloned from GitHub

## The Complete Script

```bash
#!/bin/bash
cd ~/excalidraw/excalidraw-app
npm start
```

## Understanding the Shebang

The `#!/bin/bash` line is called a **shebang** (or hashbang):
- `#!` tells the OS that this is a script
- `/bin/bash` is the path to the Bash shell interpreter

This tells the system which interpreter to use to execute the script.

## Step-by-Step Instructions

### 1. Create the script file

```bash
touch start-excalidraw
```

### 2. Add the shebang and commands to the file

Open the file in your text editor and add:

```bash
#!/bin/bash
cd ~/excalidraw/excalidraw-app
npm start
```

**What these commands do:**
- `cd ~/excalidraw/excalidraw-app` - Navigate to the Excalidraw app folder
- `npm start` - Start the development server

### 3. Make the file executable

```bash
chmod -x start-excalidraw
```

### 4. Move the file to ~/bin

```bash
mkdir -p ~/bin
mv start-excalidraw ~/bin/
```

This makes it executable from anywhere in the terminal.

### 5. Ensure ~/bin is in your PATH

Most systems include `~/bin` in PATH by default, but if the command doesn't work, add it:

```bash
echo 'export PATH="$HOME/bin:$PATH"' >> ~/.zshrc
source ~/.zshrc
```

(Use `~/.bashrc` instead of `~/.zshrc` if you're using Bash instead of Zsh)

## Usage

Now you can start Excalidraw from anywhere by typing:

```bash
start-excalidraw
```

The app will compile and open in your browser at `http://localhost:3000`

To stop the server, press `Ctrl + C` in the terminal.

## Why Does It Need npm?

Excalidraw is a **web application**, not a standalone binary.

When you clone the GitHub repo, you get the **source code**, not a compiled executable. The source code needs to:

1. **Install dependencies** - All the JavaScript libraries and tools it needs (React, etc.)
2. **Build/compile** - Transform the modern JavaScript/TypeScript code into something browsers can run
3. **Start a development server** - Host the app locally so you can access it in your browser

`npm start` handles the build/compile and starts the development server.

## Troubleshooting

**Command not found after creating the script:**
- Make sure `~/bin` is in your PATH
- Verify the file is executable: `ls -l ~/bin/start-excalidraw`
- Check the shebang is on the first line with no spaces before `#`

**npm: command not found:**
- Install Node.js and npm first
- Verify installation: `node --version && npm --version`

**Permission errors with npm:**
- Enable Corepack: `sudo corepack enable`
- Or fix npm global permissions (see npm documentation)

## Additional Resources

- [Excalidraw GitHub](https://github.com/excalidraw/excalidraw)
- [Linux file permissions guide](https://wiki.archlinux.org/title/File_permissions_and_attributes)
- [Bash scripting tutorial](https://www.gnu.org/software/bash/manual/)

## Contributing

Feel free to open issues or submit PRs if you have improvements to this guide!

## License

This guide is released under CC0 (public domain).
