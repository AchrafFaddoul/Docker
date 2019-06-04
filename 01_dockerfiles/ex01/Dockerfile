FROM debian
RUN apt-get update
RUN apt install curl -y
RUN apt -y install wget
RUN wget https://files.teamspeak-services.com/releases/server/3.6.1/teamspeak3-server_linux_amd64-3.6.1.tar.bz2
RUN apt -y install bzip2
RUN apt -y install tar
EXPOSE 9987/udp 10011 30033
RUN tar -xvf teamspeak3-server_linux_amd64-3.6.1.tar.bz2
WORKDIR teamspeak3-server_linux_amd64
CMD sh ts3server_minimal_runscript.sh
