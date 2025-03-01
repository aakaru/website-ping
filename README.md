# Website-Ping
HealthChecker is a tiny, command-line tool written in Go that checks whether a website (or any TCP service) is reachable or down. It uses `net.DialTimeout` to connect to the specified domain and port, providing a quick and easy way to assess the availability of a service.

## Features

*   **Simple Domain Check:** Checks the reachability of a given domain.
*   **Port Specification:** Allows specifying a port number (defaults to 80 if not provided).
*   **Timeout:**  Uses a 5-second timeout to prevent hanging on unreachable hosts.
*   **Clear Status Output:**  Provides a concise "[UP]" or "[DOWN]" status message, along with error details or connection information.
*   **CLI Interface:**  Uses the `urfave/cli/v2` package for a user-friendly command-line interface.

## Installation

1.  **Install Go:**  Make sure you have Go (version 1.18 or later) installed and properly configured.  See [the official Go installation instructions](https://go.dev/doc/install).

2.  **Get the code:**

    ```bash
    go get github.com/your-username/your-repo-name  # Replace with your actual repo
    ```
    This command downloads the code and any dependencies.

3.  **Build (Optional, but recommended):** You can build a binary for easy use:

    ```bash
    cd $(go env GOPATH)/src/github.com/your-username/your-repo-name  # Go to the project directory
    go build
    ```
    This will create an executable named `HealthChecker` (or `HealthChecker.exe` on Windows) in the current directory.  You can move this to a directory in your `PATH` for easy access.

## Usage

```bash
HealthChecker -d <domain> [-p <port>]
```

*  -d or --domain (Required): The domain name or IP address to check. For example: google.com, 192.168.1.1.

*  -p or --port (Optional): The port number to check. Defaults to 80 if not specified. For example: 443, 8080.

##Examples:

* Check if google.com is reachable on port 80:

```bash
./HealthChecker -d google.com
```

Possible outout:

```bash
[UP] google.com is reachable ,
From: 192.168.1.100:56789
To: 172.217.160.142:80
```

* Check if example.com is reachable on port 443:


```bash
./HealthChecker -d example.com -p 443
```

Possible output:

```bash
[UP] example.com is reachable ,
From: 192.168.1.100:58234
To: 93.184.216.34:443
```

* Check if a non-existent domain is reachable:

```bash
./HealthChecker -d thisdomaindoesnotexist.com
```

Possiblr output:

```bash
[DOWN] thisdomaindoesnotexist.com is unreachable ,
Error: dial tcp: lookup thisdomaindoesnotexist.com: no such host
```

* Check a host on a specific, likely closed port:


```bash
./HealthChecker -d google.com -p 12345
```

Possible output:

```bash
[DOWN] google.com is unreachable ,
Error: dial tcp [2a00:1450:4001:82e::200e]:12345: i/o timeout
```

* Check using go run:

```bash
go run . -d google.com -p 443
```

## Building from Source (Alternative to go get)

If you prefer to clone the repository directly:

1. Clone the repository:

```bash
git clone https://github.com/your-username/your-repo-name.git
cd your-repo-name  # Replace with your repo name
```

2. Build the project:

```bash
go build
```

3.Run using the same usage commands as above.

## Dependancies

* urfave/cli/v2 - For creating the command-line interface.

##Contributing 

Contributions are welcome! Here are some ways you can contribute:

1.  Report bugs
2.  Request features
3.  Submit pull requests
4.  Improve documentation

##  License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
