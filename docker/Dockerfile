# it's a good idea to pin this, but for demo purposes we'll leave it as is
FROM node:20-alpine as builder

# automatically creates the dir and sets it as the current working dir
WORKDIR /app
# this will allow us to run vite and other tools directly
ENV PATH /app/node_modules/.bin:$PATH

COPY package*.json ./
RUN npm install

# use a more specific COPY, as this will include files like `Dockerfile`, we don't really need inside our containers.
COPY . ./

FROM builder as prod-builder
RUN npm run build

# it's a good idea to pin this, but for demo purposes we'll leave it as is
FROM nginx:latest as production-stage
COPY --from=prod-builder /app/dist /usr/share/nginx/html
COPY docker/nginx.conf /etc/nginx/conf.d/default.conf
EXPOSE 8000
CMD ["nginx", "-g", "daemon off;"]