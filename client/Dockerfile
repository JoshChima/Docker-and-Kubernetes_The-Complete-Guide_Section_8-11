FROM node:alpine as builder
RUN echo "builder up"
WORKDIR /app
COPY ./package.json ./
RUN npm install
COPY . .
RUN npm run build

FROM nginx
EXPOSE 3000
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf
COPY --from=builder /app/build /usr/share/nginx/html
# CMD [ "npm", "run", "start" ]

#docker build -f Dockerfile.dev .