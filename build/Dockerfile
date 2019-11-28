FROM node:10 as builder
MAINTAINER "chevdor@gmail.com"
WORKDIR /polkadot
RUN git clone https://github.com/chevdor/apps.git
RUN cd apps && yarn && \
    WS_URL=ws://my.polkadotcustom.avado.dnp.dappnode.eth:9944 yarn build

RUN ls -lR /polkadot/apps/packages/apps/build

FROM nginx:alpine
# RUN apk --no-cache add ca-certificates
# WORKDIR /app
COPY --from=builder /polkadot/apps/packages/apps/build /usr/share/nginx/html
# CMD ["./app"]
