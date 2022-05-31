FROM golang:1-alpine
LABEL maintainer="Duong Quang Truong <truongres3@gmail.com>"

RUN apk add --no-cache git \
  && go get -d -v github.com/Truogd/kaisa \
  && go install github.com/Truogd/kaisa@latest \
  && rm -rf ~/go/src/github.com/Truogd/kaisas \
  && apk del git

ENTRYPOINT ["kaisa"]

CMD ["--help"]
