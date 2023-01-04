

FROM rocker/rstudio:4.0.5
 

 
RUN apt-get clean all && \
  apt-get update && \
  apt-get upgrade -y && \
  apt-get install -y \
    libhdf5-dev \
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
 
#COPY user-settings /home/rstudio/.rstudio/monitored/user-settings/user-settings
#COPY .Rprofile /home/rstudio/

RUN apt update


RUN DEBIAN_FRONTEND=noninteractive apt install apt-utils   
RUN DEBIAN_FRONTEND=noninteractive TZ=Etc/UTC apt install r-base -y  libcurl4-openssl-dev libssl-dev  libxml2-dev libfreetype6-dev libpng-dev libtiff5-dev libjpeg-dev libfontconfig1-dev libharfbuzz-dev libfribidi-dev 


RUN DEBIAN_FRONTEND=noninteractive apt install file -y default-jre git

#RUN pkg-config
RUN Rscript -e 'install.packages("devtools")'


RUN Rscript -e 'devtools::install_github("joey711/phyloseq")'

RUN Rscript -e 'devtools::install_github("nhanhocu/metamicrobiomeR")'

RUN Rscript -e 'devtools::install_github("egeulgen/pathfindR")'

RUN Rscript -e 'install.packages(c("RcppEigen","RcppArmadillo","ggsci") )'


COPY stsiRay /root/stsiRay

RUN cd /root/ && ls && R CMD INSTALL stsiRay