DOCKER

### INSTALL only if file(s) changed #

# Bad practice::
COPY  . .
RUN npm install

# Good practice
COPY package*.json     
RUN npm install
COPY . .



### Clear cache “after”
RUN apt-get update && apt-get install -y \
curl \
git \
&& rm -rf /var/lib/apt/lists/*

COPY ./package*.json .
RUN npm install && npm cache clean —force