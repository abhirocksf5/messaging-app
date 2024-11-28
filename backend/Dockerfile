#base Image

FROM node:16

#create project directory

RUN mkdir /backend

#set working directory

WORKDIR /backend

#copy the backend code

COPY . .

# Intall dependencies

RUN npm install

# Create PRIMS CLI to connect to POSTGRES

RUN  npx prisma generate
RUN  npx prisma db push
RUN  npm run build

# Copy openapi.yaml file from /backend/src to /backend/build/src

RUN  cp /backend/src/openapi.yaml /backend/build/src

# Expose the backend to PORT 8080

EXPOSE 8080
# start the backend APi service

CMD ["node","build/src/index.js"]
