ARG NODEVERSION
FROM node:${NODEVERSION}-alpine
RUN npm install -g \
  yarn \
  webpack

ARG SERVERNAME
ARG REACT_APP_PATH
RUN mkdir -p ${REACT_APP_PATH}
WORKDIR ${REACT_APP_PATH}
RUN npx create-react-app ${SERVERNAME} --typescript

WORKDIR ${REACT_APP_PATH}/${SERVERNAME}
RUN npm install @ionic/react \
    react-router \
    react-router-dom \
    @types/react \
    @types/react-router \
    @types/react-router-dom

COPY ./resources/App.tsx ./src/App.tsx

RUN yes | npm run eject
RUN \
  rm -rf ./node-modules \
  && rm -rf ./yarn.lock \
  && yarn install

RUN npm i --save \
  @capacitor/core \
  @capacitor/cli

RUN npx cap init ${SERVERNAME} com.${SERVERNAME}.com --web-dir ./public --npm-client yarn
RUN npx cap add android
RUN npx cap add electron
RUN npx cap add ios

COPY ./resources/gitignore .gitignore
RUN sed -i -e "s/node scripts\/build.js/node scripts\/build.js && npx cap sync/g" package.json

ENTRYPOINT ["npm", "run", "start"]
