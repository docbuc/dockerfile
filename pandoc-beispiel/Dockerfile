# Datei Dockerfile
FROM haskell

# Pakete installieren
RUN apt-get update -y && \
    apt-get install -y -o Acquire::Retries=10 \
                     --no-install-recommends \
      texlive-latex-recommended \
      texlive-latex-extra \
      texlive-fonts-recommended \
      texlive-lang-german \
      texlive-pstricks \
      imagemagick \
      unzip \
      python3 \
      ghostscript \
      less && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*

# Pandoc installieren
RUN cabal update && \
    cabal install pandoc-2.1.1 && \
    ln -s /root/.cabal/bin/pandoc /usr/bin/pandoc

# Mitteleuropäische Zeitzone
# (siehe https://serverfault.com/questions/683605)
RUN cp /usr/share/zoneinfo/Europe/Berlin /etc/localtime

# Fonts für LaTeX installieren
# ADD rheinwerkfonts.tgz /usr/local/share/texmf
# RUN texhash

# Volume /data, bei docker run mit dem Arbeitsverzeichnis
# verbinden, also: docker run -v $(pwd):/data
WORKDIR /data
VOLUME  ["/data"]

ENTRYPOINT ["/bin/bash"]
