FROM ubuntu:20.04
ENV DEBIAN_FRONTEND noninteractive

# Reference https://docs.yoctoproject.org/4.0/ref-manual/system-requirements.html#ubuntu-and-debian
RUN apt update && \
   apt upgrade -y --fix-missing && \
   apt -y install locales gawk wget git diffstat unzip texinfo gcc build-essential chrpath socat cpio python3 python3-pip python3-pexpect xz-utils debianutils iputils-ping python3-git python3-jinja2 libegl1-mesa libsdl1.2-dev pylint3 xterm python3-subunit mesa-common-dev zstd liblz4-tool

RUN pip install --upgrade pip
RUN pip install pycrypto

RUN ["locale-gen", "en_US.UTF-8"]
RUN ["dpkg-reconfigure", "locales"]

RUN useradd --create-home -s /bin/bash user
WORKDIR /home/user
USER user
RUN mkdir /home/user/.ssh && mkdir /home/user/bin
COPY --chown=user bashrc /home/user/.bashrc

CMD ["/bin/bash"]
