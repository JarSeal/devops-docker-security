FROM node:alpine3.12 AS build-env
WORKDIR /usr/src/app
COPY . .
RUN npm install && \
    REACT_APP_BACKEND_URL=http://localhost:8080 npm run build

FROM nginx:alpine
EXPOSE 5000
WORKDIR /usr/share/nginx/html
RUN rm -rf ./*
COPY --from=build-env /usr/src/app/build /usr/share/nginx/html
COPY nginx.conf /etc/nginx/nginx.conf
RUN chmod a+x /usr/share/nginx/html && \
    adduser -D appuser
USER appuser
CMD ["nginx", "-g", "daemon off;"]
