FROM node:alpine3.12

EXPOSE 5000

WORKDIR /usr/src/app

COPY . .

RUN apk update && \
    npm install -g serve && \
    npm install && \
    REACT_APP_BACKEND_URL=http://localhost:8080 npm run build && \
    rm -rf /usr/src/app/src && \
    rm -rf /usr/src/app/node_modules && \
    chmod a+x /usr/src/app && \
    adduser -D appuser

USER appuser

CMD ["serve", "-s", "-l", "5000", "build"]