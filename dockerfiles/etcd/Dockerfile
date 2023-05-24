FROM milvusdb/etcd:3.5.5-r2 AS builder

FROM redhat/ubi8

COPY --from=builder /opt/bitnami/etcd /opt/bitnami/etcd

ENV APP_VERSION=3.5.5 
ENV BITNAMI_APP_NAME=etcd
ENV ETCDCTL_API=3
ENV PATH=/opt/bitnami/common/bin:/opt/bitnami/etcd/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin

EXPOSE 2379 2380
WORKDIR /opt/bitnami/etcd
USER 1001

ENTRYPOINT ["/opt/bitnami/scripts/etcd/entrypoint.sh"]
CMD ["/opt/bitnami/scripts/etcd/run.sh"]
