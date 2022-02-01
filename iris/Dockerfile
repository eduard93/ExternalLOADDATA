ARG IRIS_IMAGE
FROM ${IRIS_IMAGE}

USER ${ISC_PACKAGE_MGRUSER}

COPY --chown=$ISC_PACKAGE_MGRUSER:$ISC_PACKAGE_IRISGROUP irissession.sh /
COPY --chown=$ISC_PACKAGE_MGRUSER:$ISC_PACKAGE_IRISGROUP src /tmp

RUN chmod +x /irissession.sh

SHELL ["/irissession.sh"]

RUN \
  zn "USER" \
  do $SYSTEM.OBJ.LoadDir("/tmp", "ck", , 1) \
  do ##class(%File).RemoveDirectoryTree("/tmp") \
  set g = ##class(%Net.Remote.ObjectGateway).%OpenId("%Java Server") \
  set g.Port = 55555 \
  set g.Server = "jgw" \
  set sc = g.%Save()

# bringing the standard shell back
SHELL ["/bin/bash", "-c"]