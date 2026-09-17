FROM mcr.microsoft.com/devcontainers/base:ubuntu-22.04

ENV DEBIAN_FRONTEND=noninteractive
ENV DISPLAY=:1

RUN apt-get update && apt-get install -y \
    xfce4 xfce4-terminal dbus-x11 \
    firefox \
    tigervnc-standalone-server tigervnc-common \
    novnc websockify \
    && apt-get clean && rm -rf /var/lib/apt/lists/*

RUN mkdir -p /home/vscode/.vnc
RUN echo "vscode" | vncpasswd -f > /home/vscode/.vnc/passwd
RUN chmod 600 /home/vscode/.vnc/passwd
RUN chown -R vscode:vscode /home/vscode/.vnc

USER vscode
