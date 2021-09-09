FROM ubuntu:18.04

EXPOSE 5000

WORKDIR /usr/src/app

COPY . .

RUN apt-get update && apt-get -y install curl && \
    curl -sL https://deb.nodesource.com/setup_14.x | bash && \
    apt install -y nodejs && \
    npm install -g serve && \
    npm install && \
    REACT_APP_BACKEND_URL=http://localhost:8080 npm run build && \
    apt-get purge -y --auto-remove curl && \
    rm -rf /var/lib/apt/lists/* && \
    rm -rf /usr/src/app/src && \
    rm -rf /usr/src/app/node_modules && \
    chmod a+x /usr/src/app && \
    useradd -m appuser

USER appuser

CMD ["serve", "-s", "-l", "5000", "build"]