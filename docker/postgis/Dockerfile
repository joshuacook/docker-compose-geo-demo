FROM postgres

ENV POSTGIS_MAJOR 2.3
ENV POSTGIS_VERSION 2.3.2+dfsg-1~exp2.pgdg80+1

COPY initdb.sql /docker-entrypoint-initdb.d/initdb.sql
COPY data/sf_business_businesses.csv /docker-entrypoint-initdb.d/sf_business_businesses.csv
COPY data/sf_business_inspections.csv /docker-entrypoint-initdb.d/sf_business_inspections.csv
COPY data/sf_business_legend.csv /docker-entrypoint-initdb.d/sf_business_legend.csv
COPY data/sf_business_violations.csv /docker-entrypoint-initdb.d/sf_business_violations.csv

RUN apt-get update \
      && apt-get install -y --no-install-recommends \
           postgresql-$PG_MAJOR-postgis-$POSTGIS_MAJOR=$POSTGIS_VERSION \
           postgresql-$PG_MAJOR-postgis-$POSTGIS_MAJOR-scripts=$POSTGIS_VERSION \
           postgis=$POSTGIS_VERSION \
      && rm -rf /var/lib/apt/lists/*

COPY ./initdb-postgis.sh /docker-entrypoint-initdb.d/postgis.sh
