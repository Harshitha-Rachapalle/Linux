**man**: manual command displays what other commans does eg: man ls = it lists files/directories

## shebang 

it shows who is executing .these are called executables.

**#!/bin/bash :** Ideal for **complex automation scripts** with functions, arrays, and advanced string manipulation.

**#!/bin/dash :** Frequently used for Linux init scripts due to its speed and lightweight nature.Preferred in environments where small memory usage is crucial, like embedded systems.

**#!/bin/sh :** Best for writing scripts that need to work across various operating systems, as sh is often linked to Dash or Bash.Suitable for **simple tasks**

#!/bin/ksh


* after shebang in a script , try to mention author data in a comment # format.

*  **set -x** is used for debug mode. it prints in output with comand . so that easy to understand result


