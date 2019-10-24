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

COPY ./resources/App.tsx ./App.tsx

RUN yes | npm run eject

RUN npm i @babel/plugin-transform-react-jsx

ENTRYPOINT ["npm", "run", "start"]
