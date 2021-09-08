FROM ubuntu:18.04

EXPOSE 5000

WORKDIR /usr/src/app

RUN apt-get update && apt-get -y install curl

RUN curl -sL https://deb.nodesource.com/setup_14.x | bash
RUN apt install -y nodejs

RUN npm install -g serve

COPY . .

RUN npm install

RUN REACT_APP_BACKEND_URL=http://localhost:8080 npm run build

RUN chmod a+x /usr/src/app
RUN useradd -m appuser
USER appuser

CMD ["serve", "-s", "-l", "5000", "build"]