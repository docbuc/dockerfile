# Datei Dockerfile
FROM ubuntu:20.04
ENV TZ="Europe/Berlin" 
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && \
    echo $TZ > /etc/timezone && \
    apt-get update -y && \
    apt-get install -y -o Acquire::Retries=10 \
                     --no-install-recommends \
      texlive-latex-recommended \
      texlive-latex-extra \
      texlive-fonts-recommended \
      texlive-lang-german \
      texlive-pstricks \
      texlive-fonts-extra \
      imagemagick \
      unzip \
      python3 \
      ghostscript \
      locales \
      joe \
      vim \
      curl \
      wget \
      ca-certificates \
      less && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*

# Pandoc installieren
RUN curl -L https://github.com/jgm/pandoc/releases/download/2.14/pandoc-2.14-1-amd64.deb \
   -o /tmp/pandoc.deb && \
   dpkg -i /tmp/pandoc.deb && \
   rm /tmp/pandoc.deb

# Fonts installieren
# (die Font-Datei dürfen wir nicht weitergeben)
# ADD myfonts.tgz /usr/local/share/texmf
# RUN texhash 

# Volume /data, bei docker run mit dem Arbeitsverzeichnis
# verbinden, also: docker run -v $(pwd):/data 
# Fedora, RHEL:    docker run -v $(pwd):/data:z
VOLUME  ["/data"]

# Startkommando
ENTRYPOINT ["/bin/bash"]
