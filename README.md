Linux command executable file for Excalidraw open source whiteboard

Purpose: I wanted to start Excalidraw using start-excalidraw in the terminal.

Complete script:

#!/bin/bash
cd ~/excalidraw
npmstart

0. Add the file header #!/bin/bash is called a shebang – it tells the system which interpreter to use to execute the script.
    • #! tells the OS that its  a script
    • /bin/bash is the path to the Bash shell interpreter

1. Make a text file named start-excalidraw

touch start-excalidraw

2. Add the commands to the file. We need to navigate to the excalidraw folder in ~/ so we use cd

cd ~/excalidraw

3. Once in the folder, start excalidraw

npm start

4. Make the file executable

chmod -x your-file-name

5. Move it to /bin. This needs to be done so its executable in the terminal

mv your-file-name ~/bin

Now you can start Excalidraw by simply typing start-excalidraw in the terminal!
------------------------------------------------------------------------------------------------------------------------

Excalidraw uses npm because its a web application, not a standalone binary.

When you cloned the GitHub repo, you got the source code, not a compiled executable. The source code needs to:
    1. Install dependencies - All the JavaScript libraries and tools it needs (React, etc.) 
    2. Build/compile - Transform the modern JavaScript/TypeScript code into something browsers can run 
    3. Start a development server - Host the app locally so you can access it in your browser
