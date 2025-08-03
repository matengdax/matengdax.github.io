FROM fedora

WORKDIR /workspace

COPY . .

RUN dnf install -y python3 python3-pip
RUN pip3 install -r .devcontainer/requirements.txt

CMD ["/bin/bash"]