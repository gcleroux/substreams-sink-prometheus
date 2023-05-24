FROM node:20 as build

WORKDIR /app

COPY . .
RUN npm ci && npm run build

FROM gcr.io/distroless/nodejs20 as main

ENV SUBSTREAMS_API_TOKEN=${SUBSTREAMS_API_TOKEN:-server_none}

COPY --from=build /app /app
WORKDIR /app

EXPOSE 9012

ENTRYPOINT ["/nodejs/bin/node", "./dist/bin/cli.js" ]
