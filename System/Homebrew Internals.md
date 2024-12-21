# Homebrew

### **Uninstallation (Optional)**

If you already have installed homebrew on your machine and wish to uninstall, then follow the steps below.

1. Be cautios about software packages installed via homebrew. Packages installed via homebrew can be found in the following directory, _/usr/local/Cellar_ (intel) and _/opt/homebrew/Cellar_ (ARM).
2. To uninstall the software packages installed via homebrew, execute the following commands:

Unscoped packages:

```CMD
brew uninstall -g <package_name>
```
example:

```CMD
brew uninstall -g node
```

Scoped packages:

```CMD
brew uninstall -g <@scope/package_name>
```

example:

```CMD
brew uninstall -g @angular/cli
```

3. To uninstall homebrew, execute the following command:
```CMD
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/uninstall.sh)"
```

4. You may delete the following directories manually, _/usr/local/Cellar_, _/usr/local/Caskroom_, _/usr/local/Homebrew_ (intel) and _opt/homebrew_ (ARM) . I will explain the significance of these folders later.

### **Prerequisites (Recommended)**

If you have Git on your machine,ensure that global remote.origin.url in unset. To check the configuration execute the following command:
```CMD
git config --list
```
A different remote.origin.url setting might throw the following error:

![image](https://github.com/user-attachments/assets/d7943af1-a7c9-4927-a55c-3af5137c76b3)


You may either replace the remote.origin.url to _Homebrew/brew_ using the following command:

```CMD
git config --global --replace-all remote.origin.url "https://github.com/Homebrew/brew.git"
```
or unset remote.origin.url using the following command:

```CMD
git config --global --unset remote.origin.url
```

### **Installation of Homebrew**

1. Run the following command to install Homebrew:

```CMD
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

The installation process will prompt for sudo access. If installation is successful, the following message will be seen:

![image](https://github.com/user-attachments/assets/3255eb45-5237-4a44-b4c9-54290360d2d2)


2. In ARM based system, the Homebrew's bin directory will not be in the classpath. The installation summary will provide addition steps to add the bin directory to path, so that brew command can be used from anywhere.

### **The FileSystems**

**Intel**
1. Homebrew will be installed in the _/usr/local/Homebrew_ directory. This is a local git repository of Homebrew. Navigate to the directory and execute _git config --list_. You will see the _remote.origin.url_ set to _https://github.com/Homebrew/brew_. You can find more information in _/usr/local/Homebrew/.git_.
2. A new directory named _/usr/local/Cellar_ will be created. This directory will contain all the software packages installed via Homebrew.
3. A new directory named _/usr/local/Caskroom_ will be created. This directory will contain GUI applications.
4. Few more supporting directories will be created under _/usr/local/_.
6. The _brew_ command will be added to classpath. This is symbolic link to /_usr/local/Homebrew/bin/brew_.
7. Homebrew may also add symbolic links to packages that it installs to _/usr/local/bin_.

**ARM**

The entire Homebrew package including Cellar, Caskroom and other supporting directories will be create under /opt/homebrew.

### **Installing software packages**

```CMD
brew install telnet
```



**Mohamed Jawahar Hussain**
