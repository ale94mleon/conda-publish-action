FROM continuumio/miniconda3:4.7.10

LABEL "repository"="https://github.com/fcakyon/conda-package-publish-action"
LABEL "maintainer"="Fatih C Akyon"

RUN apt-get update
# to fix: import cv2 > ImportError: libGL.so.1: cannot open shared object file: No such file or directory
RUN apt-get install -y libgl1-mesa-dev

# to fix: import cv2 > ImportError: libjasper.so.1: cannot open shared object file: No such file or directory
RUN apt-get install -y software-properties-common
RUN apt-get update
RUN add-apt-repository "deb http://security.ubuntu.com/ubuntu xenial-security main"
RUN apt-get update
RUN apt-get install libjasper1

RUN conda install -y anaconda-client conda-build conda-verify

COPY entrypoint.sh /entrypoint.sh
ENTRYPOINT ["/entrypoint.sh"]
