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

# install libgeos library 
RUN yum -y install https://download1.rpmfusion.org/free/el/rpmfusion-free-release-7.noarch.rpm

# install GCC compiler, git, and geos package
RUN yum -y install sudo gcc git geos-devel

# clean up yum
RUN yum clean all

# creating USER mintpy
RUN useradd -ms /bin/bash mintpy
RUN echo "password" | passwd --stdin mintpy
RUN usermod -aG wheel mintpy
USER mintpy
WORKDIR /home/mintpy

# cloning and installing mintpy
RUN git clone https://github.com/insarlab/MintPy.git
RUN conda env create -f ./MintPy/docs/conda_env.yml

# cleaning conda
RUN conda clean --all --yes

# setting PYTHONPATH to MintPy so you can import it directly
ENV PYTHONPATH "${PYTHONPATH}:/home/mintpy/MintPy"

# activating environment
ENV PATH /usr/local/envs/mintpy/bin:$PATH
RUN /bin/bash -c "conda init bash"
RUN /bin/bash -c ". ~/.bash_profile"
