# **📌 Everything Software Testers Should Know About PIP**

## **What is PIP?**

* **Layman’s Explanation:** Think of PIP as an **App Store for Python**.
* **Technical Explanation:** PIP is Python’s package manager that installs and manages dependencies from PyPI.

## **Checking PIP Installation**

```sh
pip --version
```

## **Installing Packages**

```sh
pip install selenium
pip install requests==2.26.0  # Specific version
pip install --upgrade selenium  # Upgrade package
```

## **Installing Multiple Packages from `requirements.txt`**

1. Create `requirements.txt`:

   ```
   selenium==4.10.0
   pytest==7.0.1
   requests==2.26.0
   ```
2. Install all at once:

   ```sh
   pip install -r requirements.txt
   ```

## **Checking Installed Packages**

```sh
pip list
pip show pytest  # Show package details
pip list --outdated  # Show outdated packages
```

## **Uninstalling Packages**

```sh
pip uninstall selenium
pip uninstall -r requirements.txt -y  # Remove multiple packages
```

## **Freezing Installed Packages**

```sh
pip freeze > requirements.txt  # Save installed packages
pip install -r requirements.txt  # Reinstall from file
```

## **Finding Outdated Packages**

```sh
pip list --outdated
pip install --upgrade $(pip list --outdated | awk '{print $1}')
```

## **Using Virtual Environments**

```sh
python -m venv test_env
source test_env/bin/activate  # (Linux/Mac)
test_env\Scripts\activate  # (Windows)
pip install selenium pytest  # Install inside venv
deactivate  # Exit virtual environment
```

## **Changing PIP Configuration**

```sh
pip config list  # Show PIP settings
pip config set global.index-url https://pypi.tuna.tsinghua.edu.cn/simple  # Change PyPI mirror
```

## **📌 Summary of Important Commands**

| Command                            | Description                |
| ---------------------------------- | -------------------------- |
| `pip install <package>`            | Install a package          |
| `pip install <package>==<version>` | Install a specific version |
| `pip install --upgrade <package>`  | Upgrade a package          |
| `pip uninstall <package>`          | Uninstall a package        |
| `pip list`                         | List installed packages    |
| `pip show <package>`               | Show package details       |
| `pip list --outdated`              | Show outdated packages     |
| `pip freeze > requirements.txt`    | Save installed packages    |
| `pip install -r requirements.txt`  | Install from a file        |
| `pip config list`                  | Show PIP settings          |

---

## **🚀 Final Thoughts**

* PIP simplifies dependency management.
* Virtual environments keep projects isolated.
* Using `requirements.txt` helps maintain consistency across environments.

💡 **Master these PIP commands to efficiently manage Python dependencies!** 🚀
