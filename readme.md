<h1 align="center">42 GetNextLine Project</h1>

<p align="center">
  <strong>A C library that reads a line from a file descriptor, handling one line at a time.</strong>
</p>

<h2>Table of Contents</h2>
<ul>
  <li><a href="#project-overview">Project Overview</a></li>
  <li><a href="#key-features">Key Features</a></li>
  <li><a href="#installation">Installation</a></li>
  <li><a href="#usage">Usage</a></li>
  <li><a href="#example">Example</a></li>
  <li><a href="#error-handling">Error Handling</a></li>
  <li><a href="#contributing">Contributing</a></li>
  <li><a href="#license">License</a></li>
  <li><a href="#contact">Contact</a></li>
</ul>

<h2 id="project-overview">Project Overview</h2>
<p>
  The GetNextLine project is designed to create a function that reads a line from a file descriptor. It supports various scenarios where multiple lines may need to be read continually and efficiently while managing memory dynamically.
</p>

<h2 id="key-features">Key Features</h2>
<ul>
  <li>Reads a complete line from a file descriptor until either a newline or EOF is reached.</li>
  <li>Supports multiple calls, maintaining the state between them to allow consecutive line reads from the same file descriptor.</li>
  <li>Handles buffer management and dynamic memory allocation, freeing memory when lines are no longer needed.</li>
  <li>Compatible with both text and binary files.</li>
  <li>Simple interface for easy integration into larger projects.</li>
</ul>

<h2 id="installation">Installation</h2>
<p>To install the GetNextLine project, follow these instructions:</p>
<pre>
<code>
# Clone the repository
git clone https://github.com/yourusername/42-getnextline.git

# Navigate into the directory
cd 42-getnextline

# Compile the project
make
</code>
</pre>

<h2 id="usage">Usage</h2>
<p>To utilize the GetNextLine function in your C program, include the header file and call the function with the appropriate parameters.</p>

<pre>
<code>
#include "get_next_line.h"

char *line;
int fd = open("example.txt", O_RDONLY);
while (get_next_line(fd, &line) > 0) {
    printf("%s\n", line);
    free(line); // Free the line after use
}
close(fd);
</code>
</pre>

<h2 id="example">Example</h2>
<p>Below is a simple program that demonstrates the use of the GetNextLine function:</p>

<pre>
<code>
#include <stdio.h>
#include <fcntl.h>
#include "get_next_line.h"

int main() {
    char *line;
    int fd = open("example.txt", O_RDONLY);
    if (fd < 0) {
        perror("Error opening file");
        return 1;
    }

    while (get_next_line(fd, &line) > 0) {
        printf("%s\n", line);
        free(line);
    }

    close(fd);
    return 0;
}
</code>
</pre>

<h2 id="error-handling">Error Handling</h2>
<p>The GetNextLine function returns:
<ul>
  <li>1 if a line is read successfully.</li>
  <li>0 if EOF is reached.</li>
  <li>-1 if an error occurs (with appropriate error handling implemented).</li>
</ul>
This allows you to manage file reading flows effectively.</p>

<h2 id="contributing">Contributing</h2>
<p>Contributions are welcome! If you’d like to improve the project, please follow these steps:</p>
<ul>
  <li>Fork the repository.</li>
  <li>Create a new branch for your feature or bug fix.</li>
  <li>Commit your changes and push the branch.</li>
  <li>Submit a pull request.</li>
</ul>

<h2 id="license">License</h2>
<p>This project is licensed under the MIT License. See the <a href="LICENSE">LICENSE</a> file for more information.</p>

<h2 id="contact">Contact</h2>
<p>For any questions or inquiries, feel free to reach out at <a href="mailto:your-email@example.com">mahmoud.skhairi@gmail.com</a>.</p>

<h2>Happy Coding!</h2>
