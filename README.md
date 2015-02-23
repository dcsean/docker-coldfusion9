# What is Docker
Docker is a really cool framework that lets you put different parts of your applications in containers which are much smaller faster lighterweight things that are sort of similar to a VM.
You can learn more about containers and docker specifically at the "[What is Docker](https://www.docker.com/whatisdocker/)" page

# What is ColdFusion?
ColdFusion is two things - a server created by Adobe Inc.  This server parses and serves pages written in one of two dialects of ColdFusion - CFML (markup language) and CFSCRIPT (script).

There are some open source competitors to Adobe ColdFusion server such as Railo and BlueDragon.  This container provides a linux based installation of Adobe's ColdFusion Server 9.0.2.

# How to use this repository

ColdFusion 9 as Docker image on Ubuntu 14.04.

If you are on a VM or something and you need to download the coldfusion binary and patch files from a local file server update prepare.sh and then run it.

    ./prepare.sh

Once you have the CF binary and patches in the /install/build direcotry you can build the Docker container:

    docker build -t cf9 .

And run it with:

    docker run -d -p 8880:80 -v /var/www:/var/www cf9


# Credits
This is entirely based on the work found at https://github.com/naag/docker-coldfusion11 and https://github.com/finalcut/docker-coldfusion10

The silent installation of ColdFusion is accomplished with a ./build/install/installer.profile file. The syntax for that file is described in this [Adobe blog post](: http://blogs.adobe.com/cfdoc/2009/10/performing_a_silent_installation_of_coldfusion_9.html).

The CF installation script was written by Jan Ruusuvuori and seems to only exist in this [forum post](https://forums.adobe.com/message/4721871).

# What odd stuff do I need to know?


1. The admin password for the coldfusion server is `Adm1n$`
2. You can't access the cf-admin interface from the web. You need to use the CF Admin API
3. You can learn more about the coldfusion installation by looking in `./build/install/installer.profile`
4. Finally, I map port 80 on the CF server to port 8880 and I have it in the usage instructions here to make it easier for me to copy paste.  Use whatever port mapping works for you.
