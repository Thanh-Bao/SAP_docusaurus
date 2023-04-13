## Official docs

https://kasmweb.com/docs/latest/how_to/building_images.html

```title="Dockerfile"
FROM kasmweb/core-ubuntu-jammy:1.13.0
USER root

ENV HOME /home/kasm-default-profile
ENV STARTUPDIR /dockerstartup
ENV INST_SCRIPTS $STARTUPDIR/install
WORKDIR $HOME

######### Customize Container Here ###########


RUN touch $HOME/Desktop/hello.txt

### Add Sudo Access ### Mặc định kasm không có sudo
RUN apt-get update \
    && apt-get install -y sudo \
    && echo 'kasm-user ALL=(ALL) NOPASSWD: ALL' >> /etc/sudoers \
    && rm -rf /var/lib/apt/list/*

## install NVM and node

## install JDK

## install python

## install git

## install docker

## install nginx


### Add Google Chrome
RUN sudo apt-get install -y gdebi-core
RUN apt-get update \
    && wget https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb -O /tmp/google-chrome-stable_current_amd64.deb \
    && gdebi --n /tmp/google-chrome-stable_current_amd64.deb \
    && rm -rf /tmp/google-chrome-stable_current_amd64.deb \
    && sed -i 's|Exec=/usr/bin/google-chrome-stable %U|Exec=/usr/bin/google-chrome-stable --no-sandbox %U|g' /usr/share/applications/google-chrome.desktop \
    && sed -i 's|Exec=/usr/bin/google-chrome-stable|Exec=/usr/bin/google-chrome-stable --no-sandbox|g' /usr/share/applications/google-chrome.desktop \
    && sed -i 's|Exec=/usr/bin/google-chrome-stable --incognito|Exec=/usr/bin/google-chrome-stable --incognito --no-sandbox|g' /usr/share/applications/google-chrome.desktop

### install VSCode

### install eclipse

### install git desktop

### install docker desktop

## install ubuntu desktop 

######### End Customizations ###########

RUN chown 1000:0 $HOME
RUN $STARTUPDIR/set_user_permission.sh $HOME

ENV HOME /home/kasm-user
WORKDIR $HOME
RUN mkdir -p $HOME && chown -R 1000:0 $HOME

USER 1000       

```

## Build image 

```
docker build -t thanhbao/kasm-macos .

```

## Run container

```

docker run -p 6901:6901 -e VNC_PW=password thanhbao/kasm-macos

```
