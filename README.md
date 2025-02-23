# Get Next Line

## Introduction

The **Get Next Line** project is part of the 42 curriculum and focuses on **file I/O operations** and **memory management**. The objective is to implement a function that reads a file **line by line**, handling different file descriptors efficiently.

## Objectives

- Learn how to manage **static and dynamic memory allocation**.
- Understand **file descriptors** and how they interact with `read()`.
- Implement a function that **returns the next line** from a file or standard input.
- Optimize performance while ensuring **leaks and overflows** are avoided.

## Function Prototype

```c
char *get_next_line(int fd);
```

### Requirements:
- Read **one line at a time** from a given file descriptor.
- Manage multiple file descriptors simultaneously.
- Handle different buffer sizes efficiently.
- Ensure proper memory deallocation to prevent **leaks**.
- Return `NULL` when reaching the end of the file or encountering an error.

## Implementation Details

- The program is written in **C**.
- Uses `read()` to fetch data from the file descriptor.
- Stores **remaining data** in a static variable for subsequent calls.
- Uses **dynamic memory allocation** to construct the returned line.
- Handles **newlines (`\n`)** properly and returns lines accordingly.

## Compilation & Usage

### Compilation

```bash
gcc -Wall -Wextra -Werror -D BUFFER_SIZE=42 get_next_line.c get_next_line_utils.c -o gnl
```

### Usage

```c
#include "get_next_line.h"
#include <fcntl.h>
#include <stdio.h>

int main()
{
    int fd = open("test.txt", O_RDONLY);
    char *line;
    
    while ((line = get_next_line(fd)))
    {
        printf("%s", line);
        free(line);
    }
    close(fd);
    return 0;
}
```

## Possible Enhancements

- Implement a **bonus version** to handle multiple file descriptors.
- Optimize performance by minimizing unnecessary memory allocations.
- Improve handling of **binary files**.

## Resources

- [File Descriptors](https://man7.org/linux/man-pages/man2/open.2.html)
- [The Read Function](https://man7.org/linux/man-pages/man2/read.2.html)

## Author

This project was completed as part of the **42 School** curriculum.

---

### Disclaimer

This project is for educational purposes only and follows the **42 project guidelines**.
