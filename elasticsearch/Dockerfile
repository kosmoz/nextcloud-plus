# 8.1.2 does not work with nextcloud fulltextsearch:
# https://github.com/nextcloud/fulltextsearch_elasticsearch/issues/179
FROM elasticsearch:7.17.2
RUN /usr/share/elasticsearch/bin/elasticsearch-plugin install --batch ingest-attachment
RUN apt-get update && \
  apt-get install -y tesseract-ocr tesseract-ocr-deu tesseract-ocr-eng && \
  rm -rf /var/lib/apt/lists/*
