FROM node:17.5.0
COPY . /app
WORKDIR /app

RUN npm install -g npm
RUN npm install -g @vue/cli
RUN npm install vue bootstrap bootstrap-vue
# ADD ./../../src/frontend/package.json /app/package.json
# RUN npm install