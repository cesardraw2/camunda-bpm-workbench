FROM camunda/camunda-bpm-platform:wildfly-latest

ENV VERSION=1.0.0-alpha9 \
    GITHUB=https://github.com/cesardraw2/camunda-bpm-workbench

ADD ${GITHUB}/blob/master/distro/embeddable/camunda-workbench-dist-embeddable-1.0.0-alpha9.jar /camunda/lib/

RUN xmlstarlet ed -L \
      -s //_:process-engine/_:plugins -t elem -n TMP -v "" \
      -s //TMP -t elem -n class -v "org.camunda.bpm.debugger.server.EmbeddableDebugWebsocketBootstrap" \
      -r //TMP -v plugin \
      /camunda/conf/bpm-platform.xml

EXPOSE 8090 9090
