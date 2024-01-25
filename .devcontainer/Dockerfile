# Use an official CUDA image as a base
FROM nvidia/cuda:11.0.3-base-ubuntu20.04

ENV DEBIAN_FRONTEND=noninteractive
# Install some additional dependencies

# Instala paquetes esenciales
RUN apt-get update && apt-get install -y \
    git \
    python3 \
    python3-pip \
    && rm -rf /var/lib/apt/lists/*

# Instala TensorFlow GPU
#RUN pip3 install tensorflow-gpu

# Instala otras bibliotecas necesarias
RUN pip3 install numpy scikit-learn seaborn matplotlib pandas

# Instala herramientas adicionales para machine learning
RUN pip3 install jupyter ipykernel

# Asegúrate de que Jupyter escuche en todas las interfaces
RUN mkdir /root/.jupyter && echo "c.NotebookApp.ip = '0.0.0.0'" >> /root/.jupyter/jupyter_notebook_config.py

# Configura Jupyter para usar el kernel de Python 3
RUN python3 -m ipykernel install --user
# Set the working direcory
WORKDIR /home/labrubius/portafolio

# Copy the current directory contents into the container at /app
COPY . /home/labrubius/portafolio

# Limpiar el sistema
RUN apt-get autoremove -y && apt-get clean -y && rm -rf /var/lib/apt/lists/*
# Expose the port for Jupyter Notebook.
EXPOSE 8888
# Default command when the container starts
CMD ["bash"]