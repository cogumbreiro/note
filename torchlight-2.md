# How to play Torchlight 2 offline (Linux)

Create a file `steam_appid.txt` with `200710` as its contents.

    echo 200710 > "~/.local/share/Steam/steamapps/common/Torchlight II/steam_appid.txt" 
  
Now run Torchlight 2:

    "~/.local/share/Steam/steamapps/common/Torchlight II/Torchlight2.bin.x86_64"
  
Note that this will **not** synchronize your game save files with Steam.
