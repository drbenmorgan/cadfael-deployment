FROM ubuntu:14.04
MAINTAINER Ben Morgan <Ben.Morgan@warwick.ac.uk>

# Update and install base packages for CadfaelBrew - will be added to
# as we identify base system requirements
RUN apt-get update && apt-get install -y \
  build-essential \
  curl \
  git \
  m4 \
  libbz2-dev \
  libcurl4-openssl-dev \
  libexpat-dev \
  libncurses-dev \
  ruby2.0 \
  texinfo \
  zlib1g-dev \
  libx11-dev \
  libxpm-dev \
  libxft-dev \
  libxext-dev \
  libpng12-dev \
  libjpeg-dev

# Create user
RUN useradd -m -U cadfael

# Now our own user and basic "at container entry" setup
USER cadfael
WORKDIR /home/cadfael

# ---------------------------------------------------------------------
# What actually happens when we RUN the container under "docker run"
# Also look at ENTRYPOINT. However, note that we're using the container
# as a one off builder! May want interactivity and/or daemon style
# containers for continuous builds The sections above could be used
# as a base image here (probably)
# Also, can pass args so could checkout tags, build tarballs
CMD git clone https://github.com/SuperNEMO-DBD/cadfaelbrew.git && \
  cd cadfaelbrew && \
  ./bin/brew cadfael-bootstrap && \
  ./bin/brew install falaise && \
  ./bin/brew ls --versions && \
  ./bin/brew info
