FROM node:20 as build-deps

WORKDIR /app

COPY package*.json ./

RUN npm install

COPY . ./

RUN npm run build

FROM nginx:1.20.0-alpine

COPY --from=build-deps /app /usr/share/nginx/html

EXPOSE 5173

# start nginx with desired options
CMD ["nginx", "-g", "daemon off;"]
