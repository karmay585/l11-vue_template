FROM node:22.2-slim

# Install dependencies
RUN apt-get update && apt-get install -y \
    vim \
    zip \
    unzip \
    curl

RUN npm install -g @vue/cli


#CMD ["sh", "-c", "npm install && npm run serve"]
#CMD ["sh", "-c", "yarn install && yarn run serve"]