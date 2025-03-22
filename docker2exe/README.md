# image2exe

`image2exe` is a command-line tool designed to convert Docker images into standalone executable files. This tool simplifies the process of packaging and distributing Docker-based applications as single binary files, allowing users to run containerized applications without needing to manage Docker commands.

## Features

- Converts any Docker image into a standalone executable
- Supports cross-platform (Windows, Linux, macOS)
- Custom working directory support
- Environment variable passing
- Volume mounting capabilities
- Optional image embedding for complete self-containment



## Usage

### Basic Usage

Convert a Docker image to an executable:

```bash
./image2exe --name <executable-name> --image <docker-image>
```

**Example:**

```bash
./image2exe --name myapp --image nginx
```

### Command-line Options

- `--name` (Required): Name of the output executable
- `--image` (Required): Docker image to convert
- `--output`: Output directory (default: `./dist`)
- `--module`: Go module name for the generated code
- `--workdir`, `-w`: Working directory inside the container
- `--env`, `-e`: Environment variables to pass
- `--volume`, `-v`: Volumes to mount
- `--target`, `-t`: Target platforms (default: all supported platforms)
- `--embed`: Embed Docker image in the binary



## Running Generated Executables

After generation, executables will be located in the `dist` directory. You can run them like any normal executable:

**Windows:**

```powershell
.\dist\myapp-windows-amd64.exe [commands...]
```

**Linux/MacOS:**

```bash
./dist/myapp-linux-amd64 [commands...]
```

**Example commands:**

```bash
# Run a simple echo command
./myapp-linux-amd64 echo "Hello World"

# Start an interactive shell
./myapp-linux-amd64 sh

# Run a complex command
./myapp-linux-amd64 sh -c "ls -la && echo 'Done!'"
```





