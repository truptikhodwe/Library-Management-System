# Online Library Management System (OLMS)

The Online Library Management System (OLMS) is a client-server application developed in C. It provides functionalities for both library administrators and members, facilitating efficient management and access to library resources. The OLMS is built using system calls to perform diverse tasks such as managing processes, handling files, implementing file locking, managing multithreading, and facilitating interprocess communication. Socket programming is employed to establish client-server communication, enabling concurrent access to the library database by multiple clients.
Functionalities

## The OLMS is equipped with the following functionalities:

* **User Authentication:** Members are required to pass through a login system to access their accounts, ensuring data privacy and security.
* **Administrative Access:** Password-protected administrative access is provided to librarians, enabling them to manage book transactions and member information.
* **Book Management:** Administrators can add, delete, modify, and search for specific book details, ensuring efficient management of library resources.
* **File-Locking Mechanisms:** Proper file-locking mechanisms are implemented using system calls to protect critical data sections and ensure data consistency.
* **Concurrent Access:** The system employs socket programming to service multiple clients concurrently, facilitating seamless access to library resources.

## Project Structure

* client.c: Contains the client-side code for interacting with the library management system.
* server.c: Contains the server-side code that handles requests from clients (not provided in the given code, but assumed to exist).

## Prerequisites

* GCC (GNU Compiler Collection)
* A Unix-like operating system (Linux, macOS, etc.)

## Compilation and Running

* gcc -o client client.c
* gcc -o server server.c -lpthread
* ./server
* ./client
* Run the compiled server program. This will start the server on localhost and port 8080.
* Interact with the system:
* Follow the on-screen prompts to interact with the system. You can log in as an administrator or a member, and perform the respective actions available to each role.

## Code Specifications
* User Authentication

    **Function:** old_mem(int client_fd) and new_mem(int client_fd)
    **Description:** Handles the login process for existing and new members, respectively. It prompts for username and password and sends the credentials to the server for validation.
    **Libraries Used:**
    1. stdio.h for input/output operations
    2.  string.h for string manipulation
    3. sys/socket.h and arpa/inet.h for socket programming

* Administrative Access

    **Function:** admin(int client_fd)
    **Description:** Handles the login process for administrators. It prompts for admin credentials and sends them to the server for validation. Upon successful login, it provides access to admin functionalities.
    **Libraries Used:**
    1. stdio.h for input/output operations
    2. string.h for string manipulation
    3. sys/socket.h and arpa/inet.h for socket programming

* **Book Management**

    **Add new book:**
        **Function:** addbook(int client_fd)
        **Description:** Prompts the admin to enter book details and sends them to the server for adding a new book.
        **Libraries Used:**
    * stdio.h for input/output operations
    * string.h for string manipulation
    * sys/socket.h for socket communication

    **Delete book:**
        **Function:** removebook(int client_fd)
        **Description:** Prompts the admin to enter the book ID to be deleted and sends the request to the server.
        **Libraries Used:**
        1. stdio.h for input/output operations
        2. string.h for string manipulation
        3. sys/socket.h for socket communication

    **Modify book count:**
        **Function:** modifybook(int client_fd)
        **Description:** Prompts the admin to enter the book ID and the new count, then sends the request to the server to update the count.
        **Libraries Used:**
        1. stdio.h for input/output operations
        2. string.h for string manipulation
        3. sys/socket.h for socket communication

    **Search for a book:**
        **Function:** searchbook(int client_fd)
        **Description:** Prompts the admin to enter the book ID or name to search for book details, then sends the request to the server.
        **Libraries Used:**
        1. stdio.h for input/output operations
        2. string.h for string manipulation
        3. sys/socket.h for socket communication

* **File-Locking Mechanisms**

    **Description:** Ensures data consistency and protects critical data sections.
    **Implementation:** This would typically be handled on the server-side using mutexes (pthread_mutex_t) to lock critical sections of code that manage shared resources. The specific implementation is assumed to be in server.c and is crucial for ensuring that multiple clients do not simultaneously modify the same data, preventing data corruption.

* **Concurrent Access**

    **Description:** The system employs socket programming to handle multiple client connections simultaneously.
    **Implementation:** This would typically involve using threading or fork to handle each client connection in parallel on the server-side. The client-side code provided uses socket(), connect(), send(), and recv() functions from the sys/socket.h and arpa/inet.h libraries to communicate with the server.
    **Libraries Used:**
    * sys/socket.h: for socket communication
    * arpa/inet.h: for internet operations
    * unistd.h for: close operation

## Additional Functionalities: Fine Calculation
* **Borrowing book:** This function prompts the user to enter the borrow date (in the format YYYY-MM-DD) and sends the borrow request to the server. If the borrow is successful, the book is marked as borrowed.

* **Returning book:** This function prompts the user to enter the return date (in the format YYYY-MM-DD) and sends the return request to the server. If the return is successful, the book is marked as returned. Additionally, if the return date is more than 14 days after the borrow date, a fine of $1 per day is calculated and displayed to the user.

## admin_login.txt

Stores login credentials for the admin.

## books.txt

Stores the details of the books in the library: (BookID, Book Name, Author, Number of Copies).

## borrowed_books.txt

Stores the transaction details for each book that is borrowed: (BookID, Username)

## logins.txt

Stores the login details for each member of library.
