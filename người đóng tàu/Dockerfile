FROM golang:1-alpine
LABEL maintainer="Duong Quang Truong <truongres3@gmail.com>"

RUN apk add --no-cache git \
  && go get -d -v github.com/Truogd/DoS-Kaisa-Tools \
  && go install github.com/Truogd/DoS-Kaisa-Tools@latest \
  && rm -rf ~/go/src/github.com/Truogd/DoS-Kaisa-Tools \
  && apk del git

ENTRYPOINT ["kaisa"]

CMD ["--help"]
