This is a mirror of my library hosted at https://create.stephan-brumme.com/portable-memory-mapping/

# Portable Memory Mapping C++ Class

Memory mapping is one of the nicest features of modern operating systems:
after opening a file in memory-mapped mode you can treat the file as a large chunk of memory and use plain pointers.
The operating system takes care of loading the data on demand (!) into memory - utilizing caches, of course.

When using my C++ class `MemoryMapped` it's really easy:
``` cpp
// open file
MemoryMapped data("myfile.txt");

// read byte at file offset 2345
unsigned char a = data[2345];

// or if you prefer pointers
const short* raw = (const short*) data.getData();
short        b   = raw[300];
```

Windows is completely different from Linux when it comes to opening a file in memory-mapped mode.
The class `MemoryMapped` hides all the OS specific stuff in only two files: [MemoryMapped.h](MemoryMapped.h) and [MemoryMapped.cpp](MemoryMapped.cpp).
They compile without any warning with GCC and Visual C++.
