# pyarmor-unpacker
A deobfuscator for PyArmor with correct jump without corruption after deobfuscation.
NOTE: This unpacker does not support PyArmor v8+ yet
I decided it was time that there was a proper PyArmor unpacker released. All the ones that currently are public are either outdated, not working at all or only giving partial output. I plan on making this one support the latest version of PyArmor.

Please star the repository if you found it helpful. I'd really appreciate it.

How to use it
There are 3 different methods for unpacking PyArmor, in the methods folder in this repository you will find all the files needed for each method. Below you will find a detailed write-up on how I started all the way to the end product. I hope more people actually understand how it works this way rather than just using the tool.

Known issues
This is a list of all the known issues/missing features. I don't have enough time to fix them myself so I am heavily relying on contributors.

Issues:

Unsafe way of stopping the second marshal.loads trigger (see write-up) Fixed by issue #9
Async code objects don't get invoked correctly -> programs like discord bots can't be unpacked Fixed by issue #19
From Python 3.10 and higher the absolute jump indexes have been divided by 2 to save storage, we have to add support for that. Fixed by issue #3
Missing features:

Unit tests
Static unpacking for versions below 3.9.7
Multi file support Fixed by issue #11
Better logging
Better prevention of accidentally executing the program for method #3 Fixed by issue #9
How to use
IMPORTANT: USE THE SAME PYTHON VERSION EVERYWHERE, LOOK AT WHAT THE PROGRAM YOU ARE UNPACKING IS COMPILED WITH. If you don't you will face issues.

Method #1
Copy all the files from the method #1 directory into the same directory as the file you want to unpack.
Run the file you want to unpack
Use an injector (I recommend Process Hacker 2) to inject https://github.com/call-042PE/PyInjector (Choose the x64 or x86 version based on your application)
Run the method_1.py file
Now you can run the partially unpacked program using run.py
Method #2
Copy all the files from the method #2 directory into the same directory as the file you want to unpack.
Run the file you want to unpack
Use an injector (I recommend Process Hacker 2) to inject https://github.com/call-042PE/PyInjector (Choose the x64 or x86 version based on your application)
In the dumps directory you can find the fully unpacked .pyc file.
(Optional) Use a decompiler to get the Python source back, since currently 3.9.7 is the minimum version you will have to use: https://github.com/zrax/pycdc
Method #3
NOTE: Don't use the static unpacker for anything below version 3.9.7, The marshal.loads audit log was only added in and after 3.9.7. Any contributors are welcome to add support

Copy all the files from the method #3 directory into the same directory as the file you want to unpack.
In the terminal run this: python3 bypass.py filename.pyc (replace filename.pyc with the actual filename, obviously)
In the dumps directory you can find the fully unpacked .pyc file.
use pylingual(pylingual.io) to extract source code from .pyc file
