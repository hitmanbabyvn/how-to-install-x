sudo apt install -y python-minimal python-simplejson install dmidecode hwdata ucf hdparm perl libuniversal-require-perl libwww-perl libparse-edid-perl libproc-daemon-perl libfile-which-perl libhttp-daemon-perl libxml-treepp-perl libyaml-perl libnet-cups-perl libnet-ip-perl libdigest-sha-perl libsocket-getaddrinfo-perl libtext-template-perl
cd /tmp
wget http://debian.fusioninventory.org/downloads/fusioninventory-agent_2.4-2_all.deb
sudo dpkg -i fusioninventory-agent_2.4-2_all.deb
echo server=http://192.168.0.31/glpi/plugins/fusioninventory/ >> /etc/fusioninventory/agent.cfg
systemctl restart fusioninventory-agent
pkill -USR1 -f -P 1 fusioninventory-agent
