FROM rocker/geospatial:4.0.5
MAINTAINER "Ben Best" ben@ecoquants.com

ENV TENSORFLOW_VERSION=gpu
ENV KERAS_VERSION=default

ENV CUDA_VERSION=10.1.243
ENV CUDA_PKG_VERSION=10-1=$CUDA_VERSION-1
ENV NVIDIA_VISIBLE_DEVICES=all
ENV NVIDIA_DRIVER_CAPABILITIES=compute,utility
ENV NVIDIA_REQUIRE_CUDA=cuda>=10.1 brand=tesla,driver>=384,driver<385 brand=tesla,driver>=396,driver<397 brand=tesla,driver>=410,driver<411
ENV CUDA_HOME=/usr/local/cuda
ENV LD_LIBRARY_PATH=$LD_LIBRARY_PATH:$CUDA_HOME/lib64:$CUDA_HOME/extras/CUPTI/lib64:$CUDA_HOME/lib64/libnvblas.so:
ENV NVBLAS_CONFIG_FILE=/etc/nvblas.conf
ENV WORKON_HOME=/opt/venv
ENV PYTHON_VENV_PATH=/opt/venv/reticulate
ENV PYTHON_CONFIGURE_OPTS=--enable-shared
ENV RETICULATE_AUTOCONFIGURE=0
ENV PATH=${PYTHON_VENV_PATH}/bin:${PATH}:${CUDA_HOME}/bin

ENV S6_VERSION=v1.21.7.0
ENV RSTUDIO_VERSION=latest
ENV PANDOC_VERSION=default
ENV TENSORFLOW_VERSION=gpu
ENV KERAS_VERSION=default
ENV PATH=/usr/lib/rstudio-server/bin:$PATH

RUN /rocker_scripts/install_cuda-10.1.sh
RUN /rocker_scripts/config_R_cuda.sh
RUN /rocker_scripts/install_python.sh

# https://github.com/rocker-org/rocker-versioned2/tree/master/scripts
RUN /rocker_scripts/install_shiny_server.sh
RUN /rocker_scripts/install_python.sh
RUN /rocker_scripts/install_tensorflow.sh
RUN /rocker_scripts/install_binder.sh

EXPOSE 3838

#RUN install2.r --error \
#  dbplyr \
#  DiagrammeR \
#  DT \
#  flexdashboard \
#  fs \
#  glue \
#  gt \
#  here \
#  htmltools \
#  httpuv \
#  jsonlite \
#  kableExtra \
#  leaflet \
#  mapedit \
#  plumber \
#  Rcpp \
#  rhandsontable \
#  RPostgres \
#  shiny \
#  shinydashboard \
#  shinydashboardPlus \
#  shinyjs \
#  shinyWidgets \
#  units \
#  urltools \
#  webshot

CMD ["/init"]