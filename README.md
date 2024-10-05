# LogIt - Custom Logging Library

**LogIt** is a customizable logging library for C that supports multiple log Types, stream redirection, and configurable log Format.

## Features

- Supports seven log Types: `Fatal`, `Error`, `Warning`, `Debug`, `Trace`, `Info` and `Performance`.
- Each log Type can be redirected to a different stream.
- Log Messages are prefixed with: [TYPE]

## Usage

**Initialize all logs with**:<br> `initializeLogStreams();`<br>

Everyting gets initialized to stderr exept INFO_LOG goes to stdout<br>

**Set output stream with**:<br> `setStream(LogType, FILE*);`<br>
**LogTypes**:
- `FATAL_LOG`, `ERROR_LOG`, `WARNING_LOG`, `DEBUG_LOG`, `TRACE_LOG`, `INFO_LOG`, `PERFORMANCE_LOG`<br>

**start Logging away with**:
`fatal_log();`, `error_log();`, `warning_log();`, `debug_log();`, `trace_log();`, `info_log();`, `performance_log();`

You can use those functions like a normal printf Function

## Important Information

- User is expected to handle `FILE*` opening Errors on his own

## Download

You can choose to Compile yourself( Detailed Explanation only for Unix-like ), or download the static lib (.a) or the dynamic lib (.so)

You always need logIt.h in your Project for Definitions.

## Compilation

**(Not needed if you Downloaded the static or dynamic Library)**<br>

**static Library**<br>

Compile to object Files (.o):
```console
gcc -c logIt.c -o logIt.o
```
Package object Files into a static Library archive (.a):
```console
ar rcs liblogIt.a logIt.o
```

**dynamic Library**<br>

Compile to object Files (.o):
```console
gcc -c logIt.c -fPIC -o logIt.o
```
Link object File into a Shared Library:
```console
gcc  -shared -o liblogIt.so logIt.o	
```
## Integration

**Direct file integration**<br>
If you import the source Files directly into your Project you need to:
- Include logIt.h file in Files where it is used:
```c
#include "filepath/to/logIt.h"
```
- Include logIt.c file in Project Compilation:
```console
gcc main.c logIt.c -o project
```
**Static Library**<br>
To use your static Library you need to:

- Copy logIt.h and liblogIt.a into your Project.
- Copy liblogIt.a into `/lib`, `/usr/lib`, or `usr/local/lib` so it is globally available.
- Include logIt.h in Files where it is used:
```c
#include "filepath/to/logIt.h"
```
- Include static Library during Compilation:
```console
gcc main.c -llogIt
```
- If Library is not in /lib add path during Compilation:
```console
gcc main.c -L. -llogIt
```
-L. = Looks for liblogIt.a in current folder.<br>
-llogIt = **l**inks lib**logIt**.a with main.c

**dynamic Library**<br>
To use your dynamic Library you need to:

- Copy logIt.h into your Project.

- Copy liblogIt.so into `/lib`, `/usr/lib`, or `usr/local/lib` so it is globally available
- Update linker:
```console
ldconfig
```
- Include logIt.h in Files where it is used:
```c
#include "filepath/to/logIt.h"
```
- Include dynamic Library during Compilation:
```console
gcc main.c -llogIt
```
- If Library is not in /lib add path during Compilation:
```console
gcc main.c -L/path/to/lib -rpath=/path/to/lib -llogIt 
```
-L = Looks for liblogIt.a in specified Folder<br>
-rpath = sets Path for programm to find lib during runtime<br>
-llogIt = **l**inks lib**logIt**.so with main.c
