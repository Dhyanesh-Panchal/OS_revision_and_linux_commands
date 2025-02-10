# Shared Files in Linux

Libraries are collections of precompiled code (functions, classes, or resources) that can be reused across multiple programs.

## Static Libraries (.a files)

Static libraries are used when you want to include the library code directly into your executable at compile time.

- Useful for creating self-contained programs with no external dependencies.
- Essentially archives of object files (.o files) created using the `ar` (archive) utility.
- The code in a static library is copied directly into the executable at compile time.

### Example: Creating a Static Library

1. Compile source files into object files:

   ```bash
   gcc -c file1.c file2.c
   ```
   This generates `file1.o` and `file2.o`.

2. Use the `ar` utility to archive the object files into a static library:

   ```bash
   ar rcs libmylib.a file1.o file2.o
   ```
   - `ar`: The archive utility.
   - `rcs`: Flags for creating (`r`), inserting (`c`), and generating an index (`s`).
   - `libmylib.a`: The name of the static library (conventionally starts with `lib` and ends with `.a`).

3. Link the static library with a program:

   ```bash
   gcc main.c -L. -lmylib -o myprogram
   ```

## Shared Libraries (.so files)

Shared libraries contain code that is loaded into memory at runtime and shared across multiple programs.

- Common in modern Linux systems as they save disk space and memory, and allow for easier updates.
- Not embedded into the executable but linked dynamically when the program runs.

### Example: Creating a Shared Library

1. Compile source files into position-independent object files:

   ```bash
   gcc -fPIC -c file1.c file2.c
   ```
   - `-fPIC`: Generates position-independent code, which is required for shared libraries.

2. Create the shared library:

   ```bash
   gcc -shared -o libmylib.so file1.o file2.o
   ```
   - `-shared`: Tells the compiler to create a shared library.
   - `libmylib.so`: The name of the shared library (conventionally starts with `lib` and ends with `.so`).

## Runtime Linking

At runtime, the program loads the shared library from the system's library paths (e.g., `/usr/lib`, `/lib`).

If the library is in a non-standard location, you can use the `LD_LIBRARY_PATH` environment variable:

```bash
export LD_LIBRARY_PATH=/custom/library/path:$LD_LIBRARY_PATH
