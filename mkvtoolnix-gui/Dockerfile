FROM hurricane/dockergui:xvnc
MAINTAINER koreican <shanes429@gmail.com@gmail.com>
# Set environment variables

# User/Group Id gui app will be executed as
ENV USER_ID=99
ENV GROUP_ID=100

# Gui App Name
ENV APP_NAME MKVToolNix
ENV TERM xterm

# Default resolution, change if you like
ENV WIDTH=1600
ENV HEIGHT=1050

# Use baseimage-docker's init system
CMD ["/sbin/my_init"]

# Install MakeMKV

RUN add-apt-repository "deb http://mkvtoolnix.download/ubuntu/xenial/ ./" && \
	add-apt-repository "deb http://mkvtoolnix.download/ubuntu/xenial/ ./" && \
	wget -q -O - https://mkvtoolnix.download/gpg-pub-moritzbunkus.txt | sudo apt-key add - && \
	apt-get update && \
	apt-get install -qy mkvtoolnix mkvtoolnix-gui

# Add scripts to conatainer
ADD startapp.sh /startapp.sh
RUN	chmod +x /startapp.sh
ADD firstrun.sh /etc/my_init.d/firstrun.sh
RUN chmod +x /etc/my_init.d/firstrun.sh


VOLUME ["/config"]
EXPOSE 3389 8080
