# Build stage
FROM node:18-alpine as build-stage
WORKDIR /app
COPY package*.json ./
RUN npm install
COPY . .
RUN npm run build


# Production stage
FROM nginx:stable-alpine as production-stage
COPY --from=build-stage /app/build /usr/share/nginx/html
# EXPOSE PORT IS THE PORT TO PLACE WHEN YOU EXPOSE THE APP
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]
# To deploy on ezhost.dev you need to deploy from a git repo, 
# paste the url of the repo and choose the name you want, 
# when the app is running, go on the expose part, 
# the port is 80 and choose the subdomain you want 
# after go on https://the_subdomain_you_choose.ezhost-app.com and you will see your kanban board  in 2 min you have your kanban board online :)
