FROM rocker/rstudio:4.0.5
 

RUN apt-get clean all && \
  apt-get update && \
  apt-get upgrade -y && \
  apt-get install -y \
    libhdf5-dev \
    build-essential \
    libcurl4-gnutls-dev \
    libssl-dev \
    libxml2-dev \
    libpng-dev \
    libxt-dev \
    zlib1g-dev \
    libbz2-dev \
    liblzma-dev \
    libglpk40 \
    libgit2-28 \
  && apt-get clean all && \
  apt-get purge && \
  rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*
 
RUN Rscript -e "install.packages(c('rmarkdown', 'tidyverse', 'workflowr', 'BiocManager'));"
RUN Rscript -e "BiocManager::install(version = '3.12')"
RUN Rscript -e "install.packages('devtools')"
RUN Rscript -e "devtools::install_github('nhanhocu/metamicrobiomeR')"
RUN Rscript -e "devtools::install_github('joey711/phyloseq')"
