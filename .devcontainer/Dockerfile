FROM mcr.microsoft.com/devcontainers/base:ubuntu-22.04

ENV DEBIAN_FRONTEND=noninteractive
ENV DISPLAY=:1

RUN apt-get update && apt-get install -y \
    xfce4 xfce4-terminal dbus-x11 \
    firefox \
    tigervnc-standalone-server tigervnc-common \
    novnc websockify \
    && apt-get clean && rm -rf /var/lib/apt/lists/*

RUN mkdir -p /home/vscode/.vnc && chown -R vscode:vscode /home/vscode/.vnc
RUN echo "vscode" | vncpasswd -f > /home/vscode/.vnc/passwd && chmod 600 /home/vscode/.vnc/passwd && chown vscode:vscode /home/vscode/.vnc/passwd
RUN echo '#!/bin/bash
xrdb $HOME/.Xresources
xsetroot -solid grey
export XKL_XMODMAP_DISABLE=1
/etc/X11/Xsession
startxfce4 &' > /home/vscode/.vnc/xstartup && chmod +x /home/vscode/.vnc/xstartup && chown vscode:vscode /home/vscode/.vnc/xstartup

USER vscode
