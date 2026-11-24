# Linux Commands & Package Management

## 1. DPKG (Debian Package Manager)
`dpkg` installs, builds, removes, and manages local `.deb` packages on Debian and Ubuntu systems.

```bash
# Install a .deb package
sudo dpkg -i <filename.deb>

# List all installed packages
dpkg --get-selections

# Filter installed packages by keyword
dpkg --get-selections | grep <keyword>

# Get file locations installed by a package
dpkg -L <package_name>

# Remove package (keeps configuration files)
dpkg -r <package_name>

# Purge package (removes package and all configuration files)
sudo dpkg -P <package_name>
```

---

## 2. APT (Advanced Package Tool)
`apt` is the interactive high-level package management tool for Debian/Ubuntu distributions.

> Reference: [PhoenixNAP APT Guide](https://phoenixnap.com/kb/apt-linux)

```bash
# List all installed packages
apt list --installed

# Check if a specific package is installed (-a for all versions)
apt list --installed <pkg_name> -a

# Search for packages by keyword or description
sudo apt search <search_term>

# View details about a package
sudo apt show <pkg_name>

# Remove package (leaves configuration files)
sudo apt remove <pkg_name>

# Purge package (deletes package and configuration files)
sudo apt purge <pkg_name>

# Remove orphaned dependencies
sudo apt autoremove
```

---

## 3. Snap Package Management
```bash
snap find <query>       # Search Snap store
snap list               # List installed snaps
snap install <appname>  # Install application
snap remove <appname>   # Remove application
snap info <appname>     # View details about an app
snap refresh            # Update all installed snaps
```

---

## 4. Full Ubuntu / Linux System Update
One-liner command to fully update apt packages, kernel/distro upgrades, clean orphans, and update snaps:
```bash
sudo apt update && sudo apt upgrade -y && sudo apt full-upgrade -y && sudo apt autoremove -y && sudo snap refresh
```

---

## 5. Handy Utilities & System Commands
```bash
# Print current directory
pwd

# Open file manager (Nautilus) in current folder
nautilus .

# Manage system services (e.g., mongod, nginx)
sudo systemctl status <service_name>
sudo systemctl start <service_name>
sudo systemctl stop <service_name>
sudo systemctl restart <service_name>
```

---

## 6. Recommended Linux Text Editors
1. **gedit** (GUI editor)
2. **nano** (Simple terminal editor)
3. **vim** (Powerful terminal editor)

---

## 7. Ubuntu Font & Display Scaling Tip
Instead of using fractional scaling (which can blur some apps), scale the system font cleanly via GNOME settings:
```bash
gsettings set org.gnome.desktop.interface text-scaling-factor 1.3
```

| Factor | Result |
| :--- | :--- |
| `1.2` | Slightly larger |
| `1.3` | Balanced & comfortable |
| `1.5` | Noticeably large |
