FROM node:18

RUN npm install -g fide-ratings-scraper && \
    echo "PORT=80" >> .env

CMD [ "fide-ratings-scraper", "api" ]

EXPOSE 80