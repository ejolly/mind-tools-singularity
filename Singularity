bootstrap: docker
from: debian:latest

# Install necessary linux packages from apt-get
%post
  apt-get update && apt-get install -y eatmydata

  eatmydata apt-get install -y wget bzip2 ca-certificates \
      libglib2.0-0 libxext6 libsm6 libxrender1 \
      git \
      libfreetype6-dev \
      swig \
      mpich \
      pkg-config \
      gcc \
      wget \
      curl \
      vim \
      nano \
      libgl1-mesa-glx \
      ffmpeg \
      fonts-liberation

  # Install anaconda
  echo 'export PATH=/opt/conda/bin:$PATH' > /etc/profile.d/conda.sh && \
      wget --quiet https://repo.continuum.io/archive/Anaconda3-4.4.0-Linux-x86_64.sh -O ~/anaconda.sh && \
      /bin/bash ~/anaconda.sh -b -p /opt/conda && \
      rm ~/anaconda.sh

  # Setup anaconda path
  export PATH="/opt/conda/bin:$PATH"
  conda install -y gcc

  # Install packages needed
  pip install git+https://github.com/IntelPNI/brainiak \
      nltools \
      nilearn \
      hypertools \
      pymvpa2 \
      mne \
      deepdish \
      nelpy \
      dask \
      pynv \
      seaborn

%environment
  PATH="/opt/conda/bin:$PATH"

%runscript
  echo "Welcome MIND travelers. Be warned: the singularity is near..."
  exec /bin/bash
