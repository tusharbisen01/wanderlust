
FROM node:20-alpine AS build

WORKDIR /app

COPY frontend/package*.json ./
RUN npm install --ignore-scripts

COPY frontend/ ./

ARG VITE_API_PATH=http://localhost:8080
ENV VITE_API_PATH=$VITE_API_PATH

RUN npm run build

FROM nginx:alpine

COPY --from=build /app/dist /usr/share/nginx/html

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]
