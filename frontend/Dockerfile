# base image node

FROM node:16 AS fe-image

#create project directory

RUN mkdir /frontend

# Create work directory

WORKDIR /frontend

# Copy source code into container

COPY . .

# Build dependencies

RUN npm install
RUN npm run build

# BASE nginx image
FROM nginx

#clean up the html folder

RUN rm -r /usr/share/nginx/html/*

# Copy DIST folder content to html folder

COPY --from=fe-image /frontend/dist /usr/share/nginx/html
