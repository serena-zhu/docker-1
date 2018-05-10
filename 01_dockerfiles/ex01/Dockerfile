# From a debian image you will add the appropriate sources to create a TeamSpeak
# server, that will launch along with your container. It will be deemed valid if at least
# one user can connect to it and engage in a normal discussion (no far-fetched setup), so
# be sure to create your Dockerfile with the right options. Your program should get the
# sources when it builds, they cannot be in your repository.

FROM debian
RUN apt-get update && apt-get install -y wget bzip2
RUN wget http://dl.4players.de/ts/releases/3.1.1/teamspeak3-server_linux_amd64-3.1.1.tar.bz2
RUN tar xvf teamspeak3-server_linux_amd64-3.1.1.tar.bz2
RUN touch teamspeak3-server_linux_amd64/.ts3server_license_accepted
EXPOSE 9987
EXPOSE 30033
EXPOSE 10011
ENTRYPOINT cd teamspeak3-server_linux_amd64 && ./ts3server_minimal_runscript.sh 

# docker run -t ex01
# docker run --rm --name 'TSS' -p 9987:9987/udp -p 30033:30033 -p 10011:10011 ex01
# connect with docker machine ip and no password; then enter token

# https://www.teamspeak.com/en/downloads#  (download macOS Client Universal Binary 3.1.8, open file)
# Connections > connect, enter loginname for "Server Nickname or Address" and password for "Server Password" then click connect (this is wrong)

# https://unixblogger.com/2017/11/08/setup-a-teamspeak-3-server-on-linux-ubuntu-debian/
# https://www.vultr.com/docs/how-to-install-teamspeak-3-server-on-ubuntu-16-04-64-bit
# https://www.digitalocean.com/community/tutorials/docker-explained-using-dockerfiles-to-automate-building-of-images
# https://support.teamspeakusa.com/index.php?/Knowledgebase/Article/View/44/16/which-ports-does-the-teamspeak-3-server-use