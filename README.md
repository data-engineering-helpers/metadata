Metadata, metadatalake, Modern Metadata Stack (MMS)
===================================================

# Table of Content (ToC)
* [Metadata, metadatalake, Modern Metadata Stack (MMS)](#metadata-metadatalake-modern-metadata-stack-mms)
* [Overview](#overview)
* [References](#references)
* [Introduction](#introduction)
* [Frameworks](#frameworks)
  * [DataHub](#datahub)
  * [Metaphor](#metaphor)
  * [Open Metadata](#open-metadata)
  * [Marquez](#marquez)
  * [OpenLineage](#openlineage)
  * [Open Data Discovery (ODD) Spec](#open-data-discovery-odd-spec)
  * [Amundsen](#amundsen)
  * [Egeria](#egeria)
  * [Databook](#databook)
  * [Nemo](#nemo)
  * [Dataportal](#dataportal)
  * [Metacat](#metacat)
  * [Nessie](#nessie)
  * [Iceberg catalogs](#iceberg-catalogs)
  * [Hive Metastore](#hive-metastore)
  * [Apache XTable](#apache-xtable)
  * [OpenHouse](#openhouse)
* [Tools](#tools)
  * [SQL parsers](#sql-parsers)
    * [SQLGlot](#sqlglot)
    * [GitSchemas](#gitschemas)

Created by [gh-md-toc](https://github.com/ekalinin/github-markdown-toc.go)

# Overview
[This project](https://github.com/data-engineering-helpers/metadata)
intends to collect, analyze and synthetize referential material
about metadata, in order to facilitate the implementing of metadatalakes.
That is, this project is a first contribution to a
Modern Metadatalake Stack (MMS), much like the initiatives around the rise
of the Modern Data Stack (MDS).

Even though the members of the GitHub organization may be employed by
some companies, they speak on their personal behalf and do not represent
these companies.

# References
* The Rise of the Metadata Lake,
  [Prukalpa](https://prukalpa.medium.com/), Jun. 2021:
  https://towardsdatascience.com/the-rise-of-the-metadata-lake-1e95127594de
* The anatomy of an active metadata platform,
  [Prukalpa](https://prukalpa.medium.com/), Aug. 2021:
  https://towardsdatascience.com/the-anatomy-of-an-active-metadata-platform-13473091ad0d
* [Arxiv - The Data Lakehouse: Data Warehousing and More - 2023 - ](https://arxiv.org/pdf/2310.08697.pdf)
  * Authors: Dipankar Mazumdar, Jason Hughes, JB Onofré (all working at Dremio at the time)
  * Date: October 2023
* [What is Apache XTable (formerly OneTable) — Interoperability for Apache Hudi, Iceberg & Delta Lake](https://dipankar-tnt.medium.com/onetable-interoperability-for-apache-hudi-iceberg-delta-lake-bb8b27dd288d)
  * Author: Dipankar Mazumdar
    ([Dipankar Mazumdar on LinkedIn](https://www.linkedin.com/in/dipankar-mazumdar/),
    [Dipankar Mazumdar on Medium](https://dipankar-tnt.medium.com/))
  * Date: Dec. 2023
* DataHub: A generalized metadata search & discovery tool, Mars Lan, Aug. 2019:
  https://engineering.linkedin.com/blog/2019/data-hub
* [Material for the Data platform - Data-lakes, data warehouses, data lake-houses](https://github.com/data-engineering-helpers/data-lakehouse)
* [Material for the Data platform - Data contracts](https://github.com/data-engineering-helpers/data-contracts)
* [Material for the Data platform - Data quality](https://github.com/data-engineering-helpers/data-quality/blob/main/README.md)
* [Material for the Data platform - Modern Data Stack (MDS) in a box](https://github.com/data-engineering-helpers/mds-in-a-box/blob/main/README.md)
* [Architecture principles for data engineering pipelines on the Modern Data Stack (MDS)](https://github.com/data-engineering-helpers/architecture-principles)
  + [Material for the Data platform - Architecture principles](https://github.com/data-engineering-helpers/architecture-principles/blob/main/material/README.md)
* Specifications/principles for a
  [data engineering pipeline deployment tool](https://github.com/data-engineering-helpers/data-pipeline-deployment)

# Introduction
In the past 10 years, as the modern data stack has matured and become
mainstream, we’ve taken great leaps forward in data infrastructure.
However, the modern data stack still has one key missing component:
context. That’s where metadata comes in. In this increasingly diverse
data world, metadata holds the key to the elusive promised land — a single
source of truth. There will always be countless tools and tech in
a team’s data infrastructure. By effectively collecting metadata,
a team can finally unify context about all their tools, processes, and data.

But what actually is metadata, you ask? Simply put, metadata is
“data about data”.

Today, metadata is everywhere. Every component of the modern data stack
and every user interaction on it generates metadata. Apart from
traditional forms like technical metadata (e.g. schemas) and business
metadata (e.g. taxonomy, glossary), our data systems now create entirely
new forms of metadata.

Cloud compute ecosystems and orchestration engines generate
logs every second, called performance metadata.
Users who interact with data assets and one another generate social metadata.
Logs from BI tools, notebooks, and other applications, as well as
from communication tools like Slack, generate usage metadata.
Orchestration engines and raw code (e.g. SQL) used to create data assets
generate provenance metadata.

![Metadata lake](img/metadata-lake.png)

# Frameworks

## DataHub
* Moto: "A Metadata Platform for the Modern Data Stack"
* GitHub: https://github.com/linkedin/datahub
* Company behind: LinkedIn
* Open source: yes

DataHub is an open-source metadata platform for the modern data stack.
Read about the architectures of different metadata systems and
[why DataHub excels](https://engineering.linkedin.com/blog/2020/datahub-popular-metadata-architectures-explained).
Also read
[the LinkedIn Engineering blog post](https://engineering.linkedin.com/blog/2019/data-hub),
check out
[the Strata presentation](https://speakerdeck.com/shirshanka/the-evolution-of-metadata-linkedins-journey-strata-nyc-2019)
and watch
[the Crunch Conference Talk](https://www.youtube.com/watch?v=OB-O0Y6OYDE).
You should also visit
[DataHub Architecture](https://github.com/linkedin/datahub/blob/master/docs/architecture/architecture.md)
to get a better understanding of how DataHub is implemented and
[DataHub Onboarding Guide](https://github.com/linkedin/datahub/blob/master/docs/modeling/extending-the-metadata-model.md)
to understand how to extend DataHub for your own use cases.

## Metaphor
* Moto: "Data Mastery for the Whole Company"
  "A modern data catalog powered by social data intelligence and AI - from the creators of DataHub"
* Home page: https://metaphor.io/
* Open source: no
* Articles on the principles:
  * The Grand Rewrite of DataHub,
    by [Mars Lan](https://www.linkedin.com/in/marslan/) _et al_,
    Sep. 2023 - https://metaphor.io/blog/the-grand-rewrite-of-datahub
  * The Modern Metadata Platform (MMP): What, Why, and How?
    by [Mars Lan](https://www.linkedin.com/in/marslan/) _et al_,
    Jan. 2022 - https://metaphor.io/blog/the-modern-metadata-platform-what-why-and-how
  * DataHub: A generalized metadata search & discovery tool,
    by [Mars Lan](https://www.linkedin.com/in/marslan/) _et al_,
    Aug. 2019 - https://engineering.linkedin.com/blog/2019/data-hub

## Open Metadata
* Moto: "A Single place to Discover, Collaborate, and Get your data right"
* Home page: https://open-metadata.org/
* GitHub: https://github.com/open-metadata/OpenMetadata
* Organization behind: former employees of Uber and Hortonworks
* Open source: yes

## Marquez
* GitHub: https://github.com/MarquezProject/marquez
* Organization behind: [WeWork](https://www.wework.com/) / Datakin
* Open source: yes

Marquez is an open source metadata service for the collection, aggregation,
and visualization of a data ecosystem's metadata, going together
with OpenLineage (see below). It maintains the provenance of how datasets
are consumed and produced, provides global visibility into job runtime
and frequency of dataset access, centralization of dataset lifecycle
management, and much more. Marquez was released and open sourced by
[WeWork](https://www.wework.com/).

## OpenLineage
* Home page: http://openlineage.io/
* GitHub: https://github.com/OpenLineage/OpenLineage
* Organization behind: WeWork / Datakin
* Open source: yes

OpenLineage is an open standard for metadata and lineage collection designed
to instrument jobs as they are running. OpenLineage is the ground standard
for Marquez (see above). It defines a generic model of run, job,
and dataset entities identified using consistent naming strategies.
The core lineage model is extensible by defining specific facets
to enrich those entities.

## Open Data Discovery (ODD) Spec
* GitHub: https://github.com/opendatadiscovery/opendatadiscovery-specification
* Open standard: yes

Open Data Discovery Specification (ODD Spec): A Universal Standard for
Metadata Collection

## Amundsen
* GitHub: https://github.com/amundsen-io/amundsen
* Company behind: Lyft
* Open source: yes

Amundsen is a data discovery and metadata engine for improving
the productivity of data analysts, data scientists and engineers
when interacting with data. It does that today by indexing data
resources (tables, dashboards, streams, etc.) and powering a page-rank
style search based on usage patterns (e.g. highly queried tables show up
earlier than less queried tables). Think of it as Google search for data.
The project is named after Norwegian explorer
[Roald Amundsen](https://en.wikipedia.org/wiki/Roald_Amundsen),
the first person to discover the South Pole.

## Egeria
* Moto: "Open metadata and governance for enterprises - automatically
capturing, managing and exchanging metadata between tools and platforms,
no matter the vendor"
* Organization behind it: Linux foundation
* Home page: https://egeria-project.org/
* GitHub: https://github.com/odpi/egeria
* Open source: yes

## Databook
* Moto: "Turning Big Data into Knowledge with Metadata at Uber"
* Uber: https://eng.uber.com/databook/
* Company behind: Uber
* Open source: no

Like many technologies at Uber, they Databook is well described in articles,
but has not been open sourced so far.

## Nemo
* Moto: "Data discovery at Facebook"
* Facebook: https://engineering.fb.com/2020/10/09/data-infrastructure/nemo/
* Company behind: Facebook
* Open source: no

## Dataportal
* Moto: "Democratizing Data at Airbnb"

* Medium:
  https://medium.com/airbnb-engineering/democratizing-data-at-airbnb-852d76c51770
* Company behind: Airbnb
* Open source: no

## Metacat
* Moto: "Making Big Data Discoverable and Meaningful at Netflix"
* Medium: https://netflixtechblog.com/metacat-making-big-data-discoverable-and-meaningful-at-netflix-56fb36a53520
* Company behind: Netflix
* Open source: ?

## Nessie
* Home page: https://projectnessie.org/
* GitHub: https://github.com/projectnessie/nessie
* Open source: yes
* Documentation: https://projectnessie.org/nessie-latest/
* Article from Apr. 2024, by [Ciro Greco](https://www.linkedin.com/in/cirogreco/):
  https://towardsdatascience.com/write-audit-publish-for-data-lakes-in-pure-python-no-jvm-25fbd971b17d
* Overview: Transactional catalog for data lakes
  * Git-inspired data version control
  * Cross-table transactions and visibility
  * Open data lake approach, supporting Hive, Spark, Dremio, AWS Athena, etc.
  * Works with Apache Iceberg tables
  * Run as a Docker image or on Kubernetes

## Iceberg catalogs
* Home page: https://iceberg.apache.org/concepts/catalog/
* Iceberg REST catalog OpenAPI specification: https://github.com/apache/iceberg/blob/main/open-api/rest-catalog-open-api.yaml
* Open source: yes
* Iceberg was initially contributed by Netflix
* Overview: You may think of Iceberg as a format for managing data in a single table,
  but the Iceberg library needs a way to keep track of those tables by name. Tasks like
  creating, dropping, and renaming tables are the responsibility of a catalog. Catalogs
  manage a collection of tables that are usually grouped into namespaces. The most important
  responsibility of a catalog is tracking a table’s current metadata, which is provided
  by the catalog when you load a table.
  Iceberg catalogs are flexible and can be implemented using almost any backend system.
  They can be plugged into any Iceberg runtime, and allow any processing engine that supports
  Iceberg to load the tracked Iceberg tables. Iceberg also comes with a number of catalog
  implementations that are ready to use out of the box.
  This includes:
  * REST - a server-side catalog that’s exposed through a REST API
  * Hive Metastore - tracks namespaces and tables using a Hive metastore
  * JDBC - tracks namespaces and tables in a simple JDBC database
  * Nessie - a transactional catalog that tracks namespaces and tables in a database with git-like version control

## Hive Metastore
* Home page (part of the Hive documentation on the Apache wiki): https://cwiki.apache.org/confluence/display/hive/design#Design-Metastore
* GitHub (part of the Hive repository on GitHub): https://github.com/apache/hive/tree/master/metastore
* Open source: yes
  [Apache wiki - AdminManual Metastore 3.0 Administration](https://cwiki.apache.org/confluence/display/Hive/AdminManual+Metastore+3.0+Administration)
* Articles:
  * [Hive Metastore – Different Ways to Configure Hive Metastore](https://data-flair.training/blogs/apache-hive-metastore/)

## Apache XTable
* Home page: https://xtable.apache.org/
* GitHub: https://github.com/apache/incubator-xtable
* Open source: yes
* Articles:
  * [Arxiv - The Data Lakehouse: Data Warehousing and More - 2023 - ](https://arxiv.org/pdf/2310.08697.pdf)
    * Authors: Dipankar Mazumdar, Jason Hughes, JB Onofré (all working at Dremio at the time)
    * Date: October 2023
  * [What is Apache XTable (formerly OneTable) — Interoperability for Apache Hudi, Iceberg & Delta Lake](https://dipankar-tnt.medium.com/onetable-interoperability-for-apache-hudi-iceberg-delta-lake-bb8b27dd288d)
    * Author: Dipankar Mazumdar
      ([Dipankar Mazumdar on LinkedIn](https://www.linkedin.com/in/dipankar-mazumdar/),
      [Dipankar Mazumdar on Medium](https://dipankar-tnt.medium.com/))
    * Date: Dec. 2023

## OpenHouse
* Home page: https://www.openhousedb.org/
* GitHub: https://github.com/linkedin/openhouse
* Open source: yes
* Articles:
  * Open sourcing OpenHouse
    * Author: [Sumedh Sakdeo](https://www.linkedin.com/in/sumedhsakdeo)
    * Date: March 2024
    * Link to the article:
      https://www.linkedin.com/blog/engineering/open-source/open-sourcing-openhouse
  * Taking Charge of Tables: Introducing OpenHouse for Big Data Management
    * Author: [Sumedh Sakdeo](https://www.linkedin.com/in/sumedhsakdeo)
    * Date: July 2023
    * Link to the article:
      https://www.linkedin.com/blog/engineering/data-management/taking-charge-of-tables--introducing-openhouse-for-big-data-mana
* Company behind: LinkedIn
* Overview: OpenHouse is an open source control plane designed for efficient management of tables
  within open data lakehouse deployments. The control plane comprises a declarative catalog and
  a suite of data services. Users can seamlessly define Tables, their schemas, and associated metadata
  declaratively within the catalog. OpenHouse reconciles the observed state of Tables with the desired
  state by orchestrating various data services.

# Tools

## SQL parsers

### SQLGlot
* Home page: https://sqlglot.com/sqlglot.html
* GitHub page: https://github.com/tobymao/sqlglot
* Companion of [SQLMesh](https://sqlmesh.com/)
* SQLGlot is a no-dependency SQL parser, transpiler, optimizer, and engine.
  + It can be used to format SQL or translate between
    [21 different dialects](https://github.com/tobymao/sqlglot/blob/main/sqlglot/dialects/__init__.py)
    like [DuckDB](https://duckdb.org/), [Presto](https://prestodb.io/) / [Trino](https://trino.io/),
    [Spark](https://spark.apache.org/) / [Databricks](https://www.databricks.com/), [Snowflake](https://www.snowflake.com/en/),
    and [BigQuery](https://cloud.google.com/bigquery/). It aims to read a wide variety of SQL inputs and output syntactically
    and semantically correct SQL in the targeted dialects.
    + It is a very comprehensive generic SQL parser with a robust
      [test suite](https://github.com/tobymao/sqlglot/blob/main/tests/).
      It is also quite [performant](https://sqlglot.com/sqlglot.html#benchmarks),
      while being written purely in Python.
    + You can easily [customize](https://sqlglot.com/sqlglot.html#custom-dialects) the parser,
      [analyze](https://sqlglot.com/sqlglot.html#metadata) queries, traverse expression trees,
      and programmatically [build](https://sqlglot.com/sqlglot.html#build-and-modify-sql) SQL.
    + Syntax [errors](https://sqlglot.com/sqlglot.html#parser-errors) are highlighted
      and dialect incompatibilities can warn or raise depending on configurations.
      However, SQLGlot does not aim to be a SQL validator,
      so it may fail to detect certain syntax errors.

### GitSchemas
* GitHub/home page: https://github.com/tdoehmen/gitschemas
* That project features scripts to crawl SQL-files from GitHub, parse them and extract
 structured database schema information from them. The goal is to learn about the semantics
 of database tables in the wild (table names, column names, foreign key relations etc.)

