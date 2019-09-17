#Version: 0.0.1
FROM opensuse/leap:15.1
LABEL maintainer="chri@gallochri.com"
LABEL descriptor="openSUSE Leap Base image"

ENV REFRESHED_AT 2019-09-17

RUN useradd -g users -p opensuse -d /home/frontend -m frontend
RUN echo 'frontend ALL=(ALL) NOPASSWD: ALL' >> /etc/sudoers

RUN echo 'solver.allowVendorChange = true' >> /etc/zypp/zypp.conf; \
    zypper --gpg-auto-import-keys refresh; \
    zypper --non-interactive dup




