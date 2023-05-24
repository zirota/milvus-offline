FROM milvusdb/milvus:v2.2.8 AS builder

FROM redhat/ubi8

COPY --from=builder /milvus /milvus
COPY --from=builder /tini /tini

# /usr/lib/libopenblasp-r0.3.21.so /usr/lib/libopenblas.so.3 &&     ln -s /usr/lib/libopenblas.so.3 /usr/lib/libopenblas.so

ENV PATH=/milvus/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
ENV LD_LIBRARY_PATH=/milvus/lib::/usr/lib
ENV LD_PRELOAD=/milvus/lib/libjemalloc.so

WORKDIR /milvus

ENTRYPOINT ["/tini" "--"]
CMD ["bash"]
