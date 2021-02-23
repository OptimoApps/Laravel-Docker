FROM node:14.15.1-alpine3.10
WORKDIR /app
RUN apk add --update --no-cache bash \
	&& apk add --update --no-cache -t .build-deps python make g++ gcc \
	&& yarn global add --prod --no-lockfile laravel-echo-server \
    && apk del .build-deps \
    && yarn cache clean

VOLUME /app

CMD ["laravel-echo-server", "start"]
