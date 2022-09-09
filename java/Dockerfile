ARG IRIS_IMAGE
FROM ${IRIS_IMAGE} AS iris

FROM openjdk:8u312-jre

ARG JAVA_GATEWAY

ENV GWDIR /jgw
ENV ISC_JARDIR /usr/irissys/dev/java/lib/1.8

COPY --from=iris \
     $ISC_JARDIR/intersystems-loader-1.1.0.jar \
     $ISC_JARDIR/intersystems-enslib-jms-3.2.0.jar \
     $ISC_JARDIR/intersystems-jdbc-3.3.1.jar \
     $ISC_JARDIR/intersystems-utils-4.0.1.jar \
     $GWDIR/

ENV GWNAME iris:IRIS:%Java Server
CMD java -Xrs -Djava.system.class.loader=com.intersystems.gateway.ClassLoader -classpath "${GWDIR}/*" com.intersystems.gateway.JavaGateway $JAVA_GATEWAY "" "$GWNAME" 0.0.0.0 "" 2>&1 