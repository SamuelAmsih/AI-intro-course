# Getting started with Python and Jupyter notebooks

This course uses **Python 3** and **Jupyter notebooks**.

A Jupyter notebook is a file ending in `.ipynb` that can contain:

- Markdown explanations such as this cell
- executable Python code
- program output
- tables and visualizations
- mathematical notation

For this course, the recommended setup is:

1. Install the latest stable Python 3.14 release.
2. Install Visual Studio Code.
3. Install the Microsoft **Python** and **Jupyter** extensions.
4. Create one reusable Python environment for the course.
5. Install `ipykernel` in that environment.
6. Select that environment as the notebook kernel.

> You do not need a separate environment for every notebook.
>
> The instructions below create one reusable environment named `tari29-python`. You can use it for all introductory TARI29 notebooks unless an exercise explicitly requires another environment.

---

## 1. Install Python

Follow the instructions for your operating system.

### Windows

1. Open the [official Python download page](https://www.python.org/downloads/).
2. Download the latest stable Python 3 release.
3. Run the installer or Python install manager.
4. If an installer offers an option to add Python to `PATH`, enable it.
5. Complete the installation.

Open **PowerShell** and check the installation:

```powershell
py --version
```

The output should be similar to:

```text
Python 3.14.7
```

If `py` is unavailable, try:

```powershell
python --version
```

Do not worry if the final maintenance number is newer than the example. Python 3.14.7, Python 3.14.8, and other Python 3.14 maintenance releases are intended to run the same course material.

---

### macOS

#### Recommended option: official Python installer

1. Open the [official Python download page](https://www.python.org/downloads/).
2. Download the latest stable macOS installer.
3. Open the downloaded `.pkg` file.
4. Follow the installation instructions.

Open **Terminal** and verify the installation:

```bash
python3 --version
```

The output should be similar to:

```text
Python 3.14.7
```

#### Alternative option: Homebrew

Students who already use Homebrew may install Python with:

```bash
brew install python
```

Then verify the installation:

```bash
python3 --version
```

> **Important for Homebrew users:** Do not install course packages directly into Homebrew's base Python installation. Homebrew manages that installation and may prevent `pip` from changing it. Use the reusable course environment created later in these instructions.

Also avoid selecting the older macOS Python at:

```text
/usr/bin/python3
```

when a newer Python 3.14 installation is available.

---

### Linux

Python 3 is often already installed. Check first:

```bash
python3 --version
```

If Python is not available, install it with the package manager for the Linux distribution.

#### Ubuntu or Debian-based distributions

```bash
sudo apt update
sudo apt install python3 python3-pip python3-venv
```

#### Fedora-based distributions

```bash
sudo dnf install python3 python3-pip
```

Check the installation:

```bash
python3 --version
```

The Python version available from a Linux package manager depends on the distribution. A recent Python 3 version should run nearly all basic exercises, although Python 3.14 is recommended when available.

---

## 2. Install Visual Studio Code

1. Download Visual Studio Code from the https://code.visualstudio.com/.
2. Install and open Visual Studio Code.
3. Open the **Extensions** view using the Extensions icon on the left.
4. Search for and install these extensions published by Microsoft:
   - **Python**
   - **Jupyter**

> Installing the Python extension does not install Python itself. Python and the Visual Studio Code extensions are separate installations.

---

## 3. Open the course folder

1. Create a folder for the TARI29 course files.
2. In Visual Studio Code, select **File > Open Folder**.
3. Select the course folder.
4. Open the supplied `.ipynb` file from the Explorer on the left.

Open the entire folder rather than opening only the notebook file. This helps Visual Studio Code discover and remember the environment used by the course.

If Visual Studio Code displays **Restricted Mode**, trust the folder only if the notebook came from the course or another trusted source. Notebook cells can contain executable code.

---

## 4. Create one reusable course environment

A Python environment contains a Python interpreter and the packages installed for that environment.

The following instructions create one reusable environment named:

```text
tari29-python
```

You only need to create it once.

### Windows PowerShell

Open a terminal in Visual Studio Code by selecting **Terminal > New Terminal**.

Create the environment:

```powershell
py -m venv "$HOME\.venvs\tari29-python"
```

Activate it:

```powershell
& "$HOME\.venvs\tari29-python\Scripts\Activate.ps1"
```

After activation, the terminal prompt may begin with:

```text
(tari29-python)
```

Upgrade `pip` inside the environment:

```powershell
python -m pip install --upgrade pip
```

Install the Python kernel needed by Jupyter notebooks:

```powershell
python -m pip install ipykernel
```

Install Matplotlib for the optional plotting examples:

```powershell
python -m pip install matplotlib
```

Register the environment as a named Jupyter kernel:

```powershell
python -m ipykernel install --user --name tari29-python --display-name "Python 3.14 - TARI29"
```

#### If PowerShell prevents activation

The environment can be prepared without activating it:

```powershell
& "$HOME\.venvs\tari29-python\Scripts\python.exe" -m pip install --upgrade pip
```

```powershell
& "$HOME\.venvs\tari29-python\Scripts\python.exe" -m pip install ipykernel matplotlib
```

```powershell
& "$HOME\.venvs\tari29-python\Scripts\python.exe" -m ipykernel install --user --name tari29-python --display-name "Python 3.14 - TARI29"
```

---

### macOS

Open a terminal in Visual Studio Code by selecting **Terminal > New Terminal**.

Create the environment:

```bash
python3 -m venv "$HOME/.venvs/tari29-python"
```

Activate it:

```bash
source "$HOME/.venvs/tari29-python/bin/activate"
```

After activation, the terminal prompt may begin with:

```text
(tari29-python)
```

Upgrade `pip` inside the environment:

```bash
python -m pip install --upgrade pip
```

Install the Python kernel needed by Jupyter notebooks:

```bash
python -m pip install ipykernel
```

Install Matplotlib for the optional plotting examples:

```bash
python -m pip install matplotlib
```

Register the environment as a named Jupyter kernel:

```bash
python -m ipykernel install \
    --user \
    --name tari29-python \
    --display-name "Python 3.14 - TARI29"
```

---

### Linux

Open a terminal in Visual Studio Code by selecting **Terminal > New Terminal**.

Create the environment:

```bash
python3 -m venv "$HOME/.venvs/tari29-python"
```

Activate it:

```bash
source "$HOME/.venvs/tari29-python/bin/activate"
```

Upgrade `pip` inside the environment:

```bash
python -m pip install --upgrade pip
```

Install the Python kernel needed by Jupyter notebooks:

```bash
python -m pip install ipykernel
```

Install Matplotlib for the optional plotting examples:

```bash
python -m pip install matplotlib
```

Register the environment as a named Jupyter kernel:

```bash
python -m ipykernel install \
    --user \
    --name tari29-python \
    --display-name "Python 3.14 - TARI29"
```

---

## 5. Select the Jupyter kernel in Visual Studio Code

Opening a notebook is not enough by itself. Visual Studio Code must also know which Python environment should execute the code.

1. Open the `.ipynb` notebook.
2. Select **Select Kernel** in the upper-right corner.
3. Select **Select Another Kernel** if it is shown.
4. Look under **Jupyter Kernels** or **Python Environments**.
5. Select:

```text
Python 3.14 - TARI29
```

The selected kernel may instead be displayed using its interpreter path.

On Windows, the path should contain something similar to:

```text
.venvs\tari29-python\Scripts\python.exe
```

On macOS or Linux, the path should contain something similar to:

```text
.venvs/tari29-python/bin/python
```

### If the kernel is not listed

Open the Command Palette:

- Windows or Linux: `Ctrl+Shift+P`
- macOS: `Command+Shift+P`

Run:

```text
Developer: Reload Window
```

Then reopen the notebook and use **Select Kernel** again.

You can also run:

```text
Python Environments: Refresh All Environment Managers
```

If necessary, select the interpreter manually.

#### Windows interpreter path

```text
C:\Users\YOUR_USERNAME\.venvs\tari29-python\Scripts\python.exe
```

#### macOS or Linux interpreter path

```text
/Users/YOUR_USERNAME/.venvs/tari29-python/bin/python
```

On Linux, the home directory commonly begins with:

```text
/home/YOUR_USERNAME/
```

---

## 6. Test the notebook setup

Run the following Python code cell after selecting the kernel:

```python
import platform
import sys

print("Python version:", platform.python_version())
print("Python executable:", sys.executable)
print("Hello from the TARI29 notebook!")
```

A successful result should show:

- a recent Python 3 version;
- an executable path containing `tari29-python`;
- the message `Hello from the TARI29 notebook!`.

For example, on macOS:

```text
Python version: 3.14.7
Python executable: /Users/name/.venvs/tari29-python/bin/python
Hello from the TARI29 notebook!
```

For example, on Windows:

```text
Python version: 3.14.7
Python executable: C:\Users\name\.venvs\tari29-python\Scripts\python.exe
Hello from the TARI29 notebook!
```

If the code cell runs without an error, the notebook is ready.

---

## 7. Working with notebook cells

A notebook normally contains two important cell types.

### Markdown cells

Markdown cells contain:

- explanations
- headings
- instructions
- links
- lists
- equations

Markdown cells do not execute Python code.

### Code cells

Code cells contain executable Python.

For example:

```python
course = "TARI29"
print(f"Welcome to {course}!")
```

The output appears below the cell.

### Useful commands

- Select the triangular **Run Cell** button beside a code cell to execute it.
- Press `Shift+Enter` to run the current cell and move to the next cell.
- Press `Ctrl+Enter` to run the current cell and remain in the same cell.
- Select **Run All** to run the complete notebook.
- Select **Restart** to restart Python and remove variables from memory.
- Select **Restart and Run All** to test the notebook from a clean state.

On macOS, `Ctrl+Enter` still runs the current notebook cell. The Control key is used, not the Command key.

---

## 8. Notebook execution order

Notebook cells share one running Python process called a **kernel**.

A variable created in one code cell remains available to later cells:

```python
language = "Python"
```

A later cell can use it:

```python
print(language)
```

However, the second cell fails if the first cell has not been run.

The number beside a code cell shows its execution order. For example:

```text
[1]
[2]
[3]
```

If cells are run in a different order, the notebook may produce confusing results.

A good final check is:

1. Select **Restart**.
2. Select **Run All**.
3. Confirm that all cells run successfully from top to bottom.

---

## 9. Installing additional packages

Python includes a standard library, but packages such as pandas and Matplotlib must be installed separately.

### Recommended method inside a notebook

Use the `%pip` command:

```python
%pip install pandas
```

This installs the package into the environment used by the current notebook kernel.

Another example:

```python
%pip install numpy
```

Restart the kernel if a newly installed package cannot be imported immediately.

### Installing from a terminal

Activate the course environment first.

#### Windows PowerShell

```powershell
& "$HOME\.venvs\tari29-python\Scripts\Activate.ps1"
```

#### macOS or Linux

```bash
source "$HOME/.venvs/tari29-python/bin/activate"
```

Then install the package:

```bash
python -m pip install pandas
```

Use:

```bash
python -m pip
```

rather than a standalone `pip` command. This makes it clearer which Python interpreter receives the package.

---

## 10. Common problems

### “Running cells requires the ipykernel package”

The selected Python environment does not contain `ipykernel`.

First, select:

```text
Python 3.14 - TARI29
```

from the notebook kernel picker.

If the course environment has not been prepared, activate it and install `ipykernel`.

#### Windows PowerShell

```powershell
& "$HOME\.venvs\tari29-python\Scripts\Activate.ps1"
python -m pip install ipykernel
```

#### macOS or Linux

```bash
source "$HOME/.venvs/tari29-python/bin/activate"
python -m pip install ipykernel
```

Then reload Visual Studio Code and reselect the kernel.

---

### The Install button appears and immediately disappears

The automatic installation may have failed in the selected Python environment.

Do not repeatedly press **Install**. Instead:

1. Open **Terminal > New Terminal**.
2. Activate the reusable course environment.
3. Run:

```bash
python -m pip install ipykernel
```

4. Select **Python 3.14 - TARI29** as the kernel.

Running the command in the terminal makes any installation error visible.

---

### The wrong Python interpreter is selected

Run:

```python
import sys

print(sys.executable)
```

The path should include:

```text
tari29-python
```

If it does not, use **Select Kernel** and choose **Python 3.14 - TARI29**.

---

### A package cannot be imported

Check the selected interpreter:

```python
import sys

print(sys.executable)
```

Then install the missing package into the current notebook environment:

```python
%pip install package_name
```

For example:

```python
%pip install matplotlib
```

---

### The notebook shows old or unexpected values

The kernel retains variables from previously executed cells.

Select:

```text
Restart
```

and then:

```text
Run All
```

This runs the notebook from a clean state.

---

### Visual Studio Code is in Restricted Mode

Notebook execution may be restricted in an untrusted workspace.

Trust the folder only when the files came from the course or another trusted source. Do not run code from an unknown notebook without inspecting it first.

---

### PowerShell says that scripts are disabled

You can avoid activation and call the environment's Python directly:

```powershell
& "$HOME\.venvs\tari29-python\Scripts\python.exe" -m pip install ipykernel matplotlib
```

You can then select that interpreter in the Visual Studio Code kernel picker.

---

### macOS selects `/usr/bin/python3`

The path `/usr/bin/python3` normally refers to the Python supplied with macOS.

Select the registered course kernel instead:

```text
Python 3.14 - TARI29
```

The selected executable should be similar to:

```text
/Users/YOUR_USERNAME/.venvs/tari29-python/bin/python
```

---

### Homebrew reports an externally managed environment

Do not use `sudo pip install` and do not force packages into Homebrew's base Python.

Create or use the reusable course environment:

```bash
python3 -m venv "$HOME/.venvs/tari29-python"
source "$HOME/.venvs/tari29-python/bin/activate"
python -m pip install ipykernel matplotlib
```

---

## 11. Using Python without a notebook

Python can also run ordinary files ending in `.py`.

Create a file named `hello.py` containing:

```python
print("Hello, Python!")
```

Run it from a terminal.

### Windows

```powershell
py hello.py
```

### macOS or Linux

```bash
python3 hello.py
```

For this exercise, the Jupyter notebook is recommended because the instructions, examples, code, and results remain together in one file.

---

## 12. Setup checklist

Before starting the exercises, confirm that:

- [ ] Python 3 is installed.
- [ ] `python3 --version`, `python --version`, or `py --version` works.
- [ ] Visual Studio Code is installed.
- [ ] The Microsoft **Python** extension is installed.
- [ ] The Microsoft **Jupyter** extension is installed.
- [ ] The reusable `tari29-python` environment has been created.
- [ ] `ipykernel` is installed in that environment.
- [ ] **Python 3.14 - TARI29** is selected as the notebook kernel.
- [ ] The test cell runs successfully.
- [ ] The displayed Python executable contains `tari29-python`.

---

## Official documentation

- [Download the latest stable Python release](https://www.python.org/downloads/)
- [Read the Python virtual-environment documentation](https://docs.python.org/3/library/venv.html)
- [Read the Python Packaging Guide for virtual environments](https://packaging.python.org/en/latest/guides/installing-using-pip-and-virtual-environments/)
- [Learn about Jupyter notebooks in Visual Studio Code](https://code.visualstudio.com/docs/datascience/jupyter-notebooks)
- [Learn how Visual Studio Code manages Jupyter kernels](https://code.visualstudio.com/docs/datascience/jupyter-kernel-management)
