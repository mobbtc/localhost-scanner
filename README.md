# Localhost Scanner

A Windows command-line tool that identifies which processes own local TCP and UDP ports and groups results by process name and PID.

## Build with Visual Studio

1. Install Visual Studio with the **Desktop development with C++** workload.
2. In Visual Studio, select **Create a new project**, choose the C++ **Empty Project** template, and name it `localhostscanner`.
3. In **Solution Explorer**, right-click **Source Files** and choose **Add > Existing Item**. Select the `main.cpp` file from this repository.
4. In the toolbar, select **Release** and **x64**.
5. Choose **Build > Build Solution** or press **Ctrl+Shift+B**.

The build produces `localhostscanner.exe`. Look in the solution's `x64\Release` folder or check the **Output** window for the exact path.

## Usage

From PowerShell in the executable's folder:

```powershell
.\localhostscanner.exe
.\localhostscanner.exe --porta 3000
.\localhostscanner.exe --help
```

The `--porta` filter matches either TCP endpoint or the local UDP port. If you launch the executable by double-clicking it, press **Enter** to close the window after the scan.

## Example output

```text
[+] LOCALHOST SCANNER
[+] TCP localhost connections by process

[+] Scanning TCP connections...
[+] Checking UDP endpoints...

[+] Processes with localhost connections:

[+] PID 4120  node.exe
[+]     listening    127.0.0.1:3000

[+] TCP: 1  |  UDP: 0
```

The scanner shows an IPv4 snapshot. TCP results include the remote endpoint when available. A `bind-all` entry uses `0.0.0.0`, meaning the socket is bound to all IPv4 interfaces.
