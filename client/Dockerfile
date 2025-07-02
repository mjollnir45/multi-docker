FROM node:16-alpine
WORKDIR '/app'
COPY ./package.json ./
RUN npm install

COPY . .
RUN npm runn build

FROM nginx
EXPOSE 3000
COPY ./nginx/default.conf /ect/nginx/conf.d/default.conf
COPY --from=builder /app/build /usr/share/nginx/html

# CMD ["npm", "run", "start"]