FROM centos:centos7
MAINTAINER Conda Development Team <conda@continuum.io>

RUN yum -y update \
    && yum -y install curl bzip2 \
    && curl -sSL https://repo.continuum.io/miniconda/Miniconda3-latest-Linux-x86_64.sh -o /tmp/miniconda.sh \
    && bash /tmp/miniconda.sh -bfp /usr/local/ \
    && rm -rf /tmp/miniconda.sh \
    && conda install -y python=3 \
    && conda update conda \
    && conda clean --all --yes \
    && rpm -e --nodeps curl bzip2

# install git
RUN yum -y install sudo git

# clean up yum
RUN yum clean all

# creating USER aria-tools
RUN useradd -ms /bin/bash aria-tools
RUN echo "password" | passwd --stdin aria-tools
RUN usermod -aG wheel aria-tools
USER aria-tools
WORKDIR /home/aria-tools

# git clone aria-tools
RUN git clone https://github.com/aria-tools/ARIA-tools.git
RUN conda env create -f ./ARIA-tools/environment.yml

# cleaning conda environments
RUN conda clean --all --yes

# setting PYTHONPATH to ARIA-tools
ENV PYTHONPATH "${PYTHONPATH}:/home/aria-tools/ARIA-tools"

# activating environment
ENV PATH /usr/local/envs/ARIA-tools/bin:$PATH
RUN /bin/bash -c "conda init bash"
RUN /bin/bash -c ". ~/.bash_profile"
