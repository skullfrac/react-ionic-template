ARG NODEVERSION
FROM node:${NODEVERSION}-alpine
RUN npm install -g yarn



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

CMD tail -f /dev/null