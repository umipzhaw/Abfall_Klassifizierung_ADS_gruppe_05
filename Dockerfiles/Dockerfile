FROM jupyter/base-notebook

USER root
RUN chmod 777 /home -R
WORKDIR /home/suvi/notebook


RUN conda install --yes \
      r-glpkAPI \
&& conda clean --all --yes

RUN apt-get update

# We need wget to set up the PPA and xvfb to have a virtual screen and unzip to install the Chromedriver
RUN apt-get install -y wget 
RUN apt-get install -y xvfb
RUN apt-get install -y unzip
RUN apt-get install -y gnupg2

# Set up the Chrome PPA
RUN wget -q -O - https://dl-ssl.google.com/linux/linux_signing_key.pub | apt-key add -
RUN echo "deb http://dl.google.com/linux/chrome/deb/ stable main" >> /etc/apt/sources.list.d/google.list

# Update the package list and install chrome
RUN apt-get update -y
RUN apt-get install -y google-chrome-stable

# Set up Chromedriver Environment variables
ENV CHROMEDRIVER_VERSION 2.19
ENV CHROMEDRIVER_DIR /chromedriver
RUN mkdir $CHROMEDRIVER_DIR

# Download and install Chromedriver
RUN wget -q --continue -P $CHROMEDRIVER_DIR "http://chromedriver.storage.googleapis.com/$CHROMEDRIVER_VERSION/chromedriver_linux64.zip"
RUN unzip $CHROMEDRIVER_DIR/chromedriver* -d $CHROMEDRIVER_DIR

# Put Chromedriver into the PATH
ENV PATH $CHROMEDRIVER_DIR:$PATH

RUN apt-get update && apt-get remove -y python && apt-get install -y python3 r-base
RUN cp /usr/bin/python3 /usr/bin/python

# Create a new user
ENV HOME /home/suvi/notebook

RUN apt-get install -y libglib2.0-0 \
    libnss3 \
    libgconf-2-4 \
    libfontconfig1
 
RUN apt-get update \
&& apt-get install -y \
   unzip \
   wget \
   libnss3 \
&& rm -rf /var/lib/apt/lists/* \
&& echo "progress = dot:giga" | tee /etc/wgetrc \
&& mkdir -p /mnt /opt /data \
&& wget https://github.com/andmarios/duphard/releases/download/v1.0/duphard -O /bin/duphard \
&& chmod +x /bin/duphard



# Install additional Python libraries
RUN pip install \ 
        matplotlib \ 
        google-api-python-client \         
        pandas \ 
        selenium \
        tensorflow \        
        chromedriver-py \      
        webdriver-manager \  
        numpy \  
        seaborn \  
        scipy \ 
        bs4 \
        zipfile36 \
        scikit-learn \ 
        beautifulsoup4 \
        folium \
        openpyxl \
        shapely \ 
        requests \ 
        statsmodels \ 
        pygame \
        openrouteservice \
        jupyterthemes \
        pycoingecko \
        opencv-python \
        pytesseract \
        nltk \
        mesa \
        pylint \
        django \
        dash \
        flask \
        fnmatch2 \
        psycopg2-binary \
        sqlalchemy \
        flickrapi \
        xlwt \
        openpyxl \
        pykafka \
        yfinance \
        ta \
        openrouteservice \
        statsmodels \
        pygame \
        pulp \
        mip \
        boto3 \
        keras \ 
        urllib3 \ 
        kaggle \
        mysql-connector-python \
        tensorrt \
        textblob-de \
        geopandas


# COPY kaggle authencation file
COPY ./conf/kaggle.json /home/jovyan/.kaggle/kaggle.json
RUN chown jovyan /home/jovyan/.kaggle/kaggle.json
RUN chmod 600 /home/jovyan/.kaggle/kaggle.json

# COPY user_agents
COPY ./conf/user_agents.txt /home/suvi/notebook/static/user_agents.txt
RUN chown jovyan /home/suvi/notebook/static/user_agents.txt
RUN chmod 600 /home/suvi/notebook/static/user_agents.txt
 

#Code UMIP ADD Jupyter Notebook and data
#ADD Finally_Abgabge_Projekt_ADS_umiker_suvi.ipynb /home/suvi/notebook
ADD Projekt_ADS_Carbage_classification_umiker_suvi_with_docker.ipynb /home/suvi/notebook
