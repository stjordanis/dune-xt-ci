ARG CC
ARG COMMIT
ARG BASE
FROM dunecommunity/dune-xt-docker_base_${BASE}_${CC}:${COMMIT}

WORKDIR ${SUPERDIR}

ARG project_name
ARG modules_to_delete
ENV MY_MODULE=${project_name}

# run our local scripts look for an OPTS env entry
# and ensure ${MY_MODULE} from checkout is used via clean mount point
# and removes xt-la, xt-grid, xt-functions for xt-common, etc
RUN set -eu && \
    rm -rf ${modules_to_delete} && \
    ${SRC_DCTRL} ${BLD} all && \
    ${SRC_DCTRL} ${BLD} bexec "${BUILD_CMD} bindings || echo no bindings" && \
    rm -rf ${MY_MODULE}  && \
    mkdir ${MY_MODULE}


# THE END
ENV DEBIAN_FRONTEND teletype
