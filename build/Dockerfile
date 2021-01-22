FROM node:10 as builder

WORKDIR /polkadot
RUN git clone https://github.com/polkadot-js/apps.git
#RUN git clone https://github.com/chevdor/apps.git
RUN cd apps && yarn && \
    #WS_URL=ws://my.kusama.avado.dnp.dappnode.eth:9944 yarn build
    WS_URL=ws://my.polkadotcustom.avado.dnp.dappnode.eth:9944 yarn build

RUN ls -lR /polkadot/apps/packages/apps/build

FROM nginx:alpine
COPY --from=builder /polkadot/apps/packages/apps/build /usr/share/nginx/html
