# chasing_your_tail
Tool for using nearby wireless signals to help determine if you're being followed. 

Released under the MIT License https://opensource.org/licenses/MIT



Prereq content for easy copying:

sudo apt-get update
sudo apt-get upgrade

wget https://www.kismetwireless.net/repos/kismet-release.gpg.key | sudo apt-key add -
echo "deb https://www.kismetwireless.net/repos/apt/release/$(lsb_release -cs) $(lsb_release -cs) main" |sudo tee /etc/apt/sources.list.d/kismet.list

sudo apt-get update
sudo apt-get install kismet
sudo apt install jq
sudo usermod -aG kismet pi
sudo reboot

groups (to confirm pi is a member of kismet group)

sudo vi /etc/kismet/kismet_site.conf
##add
source=wlan0
source=wlan1
source=hci0

mkdir /home/pi/kismet_logs

sudo vi /etc/kismet/kismet_logging.conf
log_prefix=/home/pi/kismet_logs/

sudo vi /etc/xdg/autostart/display.desktop

##add
[Desktop Entry]
Name=cyt_gui
Exec=/home/pi/Desktop/cyt_gui.sh


@reboot sleep 30 && /home/pi/Desktop/cyt/wlan1_to_mon.sh &
@reboot sleep 60 && /usr/bin/kismet &
