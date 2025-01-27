# syntax=docker/dockerfile:1.7

#grab latest base-notebook image
FROM quay.io/jupyter/base-notebook:latest

# tmp switch to root to install libs
USER root
RUN apt-get update && apt-get install -y libmariadb3 libmariadb-dev python3-dev build-essential

# Switch back to jovyan (local user used for Notebook Docker images) to avoid accidental container runs as root
USER $NB_UID
#install packages. Do not use cache.
RUN pip install --no-cache-dir matplotlib scikit-learn pandas mariadb