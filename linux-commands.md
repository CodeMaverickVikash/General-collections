-> dpkg in Linux is the primary package manager for Debian and Debian-based systems, such as Ubuntu. The tool installs, builds, removes, configures, and retrieves information for Debian packages. The command works with packages in .deb format.

dpkg [options] action

sudo dpkg -i fileNameWith.deb // to install app of .deb file
dpkg --get-selections // list all installed pkg using dpkg
dpkg --get-selections | grep python // filters by python keyword
dpkg -L python // get location of all installed python pkg
dpkg -r <package> // Removes an installed package. Does not remove configuration files and other data.
sudo dpkg -P <package> // Purges an installed or removed package. Deletes configuration files and other data.

-> apt is an interactive command-line tool for managing deb packages on different Linux distributions. The package manager installs, removes, updates, and upgrades deb packages.

Refer - https://phoenixnap.com/kb/apt-linux

apt [options] command [packages]

apt list --installed // list all installed pkg using apt
apt list --installed pkg_name -a // check specific pkg installed or not, -a for all
sudo apt remove pkg_name // Deletes a package but leaves configuration files.
sudo apt purge pkg_name // Deletes a package and any configuration files.
sudo apt autoremove // Removes no longer required dependencies.
sudo apt search // Searches for packages whose name or description contains the search term.
sudo apt show // Prints details about a specific package.

-> snap store
snap find query
snap list
snap install appname
snap remove appname
snap info appname
snap refresh

-> Extra
pwd // check current dir
nautilus . // open file manager from terminal in current dir
sudo systemctl status/start/stop/restart server_name // to check status of service ex. mongod

Best editors:
1. gedit
2. nano
3. vim

Full ubuntu or linux os update
sudo apt update && sudo apt upgrade -y && sudo apt full-upgrade -y && sudo apt autoremove -y && sudo snap refresh

to increase fonts in ubuntu, don't scele to 125% instead increase fonts using below terminal command
gsettings set org.gnome.desktop.interface text-scaling-factor 1.3
Values try karo:
1.2 → thoda bada
1.3 → comfortable
1.5 → kaafi bada
