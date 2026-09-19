
## Activity 1

### Part 1: Software Installation using Package Managers in Bash

**Objective**

Practice using CLI package tools to update local repositories, manage software dependencies, and safely install or remove applications in a Debian-derived Linux environment.

**Key Commands & Syntax**

- `sudo apt update`: Updates the local list of available packages and software repository definitions.
- `sudo apt install <package_name>`: Fetches, verifies, and installs the specified application along with required dependencies.
- `sudo apt remove <package_name>`: Removes the installed software binaries while preserving configuration files.

**Core Takeaways & Security Implications**

- Admin privileges (`sudo`) are required to modify system software locations and package libraries.
- Keeping repositories updated ensures system access to the latest security patches and bug fixes.
- Package management tools (like APT) automatically resolve and install dependencies, mitigating manual configuration errors.

### Part 2: Environment Interaction with Basic Commands (echo & expr)

**Objective**

Learn basic output formatting, string output, environment variable expansion, and simple integer arithmetic directly inside the Bash shell interpreter.

**Key Commands & Syntax**

- `echo`: Displays text strings or environment variable values to standard output (the terminal screen).
  - Example string display: `echo "Initializing Security Scan..."`
- `expr`: Evaluates expression strings and computes basic integer arithmetic.
  - Example addition: `expr 10 + 5`

**Core Takeaways & Security Implications**

- `echo` is essential for script debugging, generating user feedback, and constructing log entries.
- `expr` provides lightweight mathematical logic directly in CLI scripts (e.g., counters, simple metric calculations) without invoking heavy external programming languages.
