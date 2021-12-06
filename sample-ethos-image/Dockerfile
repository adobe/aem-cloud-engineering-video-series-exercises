ARG aem_base
FROM ${aem_base}

ADD target/container/root /

ARG content_mode
ARG precompile_clientlibs=false
RUN CONTENT_MODE=${content_mode} LOG_ERROR_WHITELIST=/opt/aem/error_whitelist.txt PRECOMPILE_CLIENTLIBS=${precompile_clientlibs} /opt/aem/scripts/create_segmentstore.sh
