# DOCKER-VERSION        1.8.2

FROM hubot
MAINTAINER Tanguy de Lignières, whren@free.fr

ENV HUBOT_PORT 8082
ENV HUBOT_ADAPTER slack
ENV HUBOT_NAME bot-name
ENV HUBOT_SKYPE_USERNAME xxxxxxxxxxxxxxxxxxxxx
ENV HUBOT_SKYPE_PASSWORD xxxxxxxxxxxxxxxxxxxxx
# default values
ENV HUBOT_SKYPE_RECONNECT 240
ENV HUBOT_LOG_LEVEL info
# default values
ENV PORT ${HUBOT_PORT}

EXPOSE ${HUBOT_PORT}

CMD bin/hubot --adapter skype-web
