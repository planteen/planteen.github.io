Find all references to global variables in a file:
use sed to replace any extern to // extern
find . -type f -name "*.c" -exec sed -i 's/extern/\/\/ extern/g' {} \;
find . -type f -name "*.h" -exec sed -i 's/extern/\/\/ extern/g' {} \;
try to compile file (gcc -c file.c)
