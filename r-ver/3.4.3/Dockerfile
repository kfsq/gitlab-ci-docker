FROM rocker/r-ver:3.4.3

LABEL org.label-schema.license="MPL-2.0" \
      org.label-schema.vcs-url="https://github.com/kfsq/gitlab-ci-docker" \
      org.label-schema.vendor="Docker images for use with GitLab CI" \
      maintainer="Kristoffer Winther Balling <kfsq@novonordisk.com>"

RUN apt-get update \
  && apt-get install -y --no-install-recommends \
  ## Debian packages for SSL
  libssl-dev \
  libcurl4-openssl-dev \
  ## Debian packages for GIS
  libgdal-dev \
  libgeos-dev \
  libudunits2-dev \
  ## Debian packages for V8
  libv8-3.14-dev \
  libprotobuf-dev \
  libjq-dev \
  protobuf-compiler \
  # Debian packages Java (for rJava)
  libbz2-dev \
  openjdk-8-jdk \
  # Configure Java for R (for rJava)
  && R CMD javareconf \
  ## Install R packages
  && Rscript -e "install.packages(c( \
  'import', \
  'ggplot2', \
  'knitr', \
  'magrittr', \
  'stringi', \
  'xml2', \
  'shiny', \
  'shinydashboard', \
  'dygraphs', \
  'plotly', \
  'shinyWidgets', \
  'data.table', \
  'stringi', \
  'lubridate', \
  'rhandsontable', \
  'leaflet', \
  'matrixStats', \
  'sp', \
  'whisker', \
  'digest', \
  'RJDBC' \
  ))" \
  ## Clean up
  && cd / \
  && rm -rf /tmp/* \
  && apt-get autoremove -y \
  && apt-get autoclean -y \
  && rm -rf /var/lib/apt/lists/*
