# Dixer

## What is Dixer?

Dixer is a tool to that can be used to execute a wide range of ETL, data transformation and data migration task. Also includes jobs for performing workflow functions like sending email messages, file and FTP operations, data sources and destinations, delay, make a HTTP or SOAP request and more.

## Why Dixer?

* Automates Administrative Functions and Data Loading.
* It can load millions of rows from one data source to another in very few minutes.
* Dixer eliminates the need of hardcore programmers.
* Dixer offers simple error and event handling.
* Easy workflow with Jobs.
* Multiplatform.
* No need installation and dependences.
* Ease and speed of implementation.
* Standardized data transformation.
* Integrates with almost all bigs relational databases (ORACLE, SAP HANA DB, IBM DB2, MySQL, MSSQL, PostgreSQL and more).

## Motivation

I work with SSIS and Talend, these are great tools to automate data loading and to do data transformation, but there are to big... TOO BIG!

Some requeriments doesn't require all magical features of these tools... a simple loading, or send a email, etc... is fine but you need the complete installation of Talend Studio or SSDT to create the package, this is why I created Dixer, a simple binary to cover a lot of possibilities!

Also is more simple, Do you want pass a lot of rows from Oracle to MSSQL? In SSIS and Talend you need to do a data convertion, but not in Dixer.

Do you want load 7 million rows to a Excel file? In SSIS you need Excel installed and you can't pass all these rows because excel limit (at least deal with a tedious process), with Dixer by default create a sheet an continue with the data.. Doesn't need Excel or other requeriments.

If you want to execute your package in another host, only copy the binary, no need to install anything! (Well, maybe dependences that require the Oracle Instant Client if want to work with Oracle or clidriver to work with IBM DB2).

Simplicity: You can create a complete workflow from scrath using your favorite text editor and format (TOML, YAML, JSON).

## Features

Dixer offers a variety of features. The importans are called **Jobs** with can do this functions:

* Data transformation
* Data migration
* Query execution
* Mail sending
* Process task
* File operations
* FTP operations
* HTTP request
* SOAP request
* Delay
* Bucle of workflow
* Execute a group of jobs or workflow
* Compress
* Decompress
* Amazon S3 tasks

### Aditional features

* Define variables and set it in almost all part of the project.
* Dixer supports expressions to get a custom value.
* Skip a row from migration if this match with a Rule Expression configured.
* Is possible to use derivated columns in mapping for dataflows with Expression Mapping or a variable easily.
* Execute a different workflow for each row migrated from source to destination (example: for each row send a email).
* Events Handling for execute a workflow when a Success, Completion or Error happenned in a **Job**
* Execute parallels **Jobs**
* Security: you can encrypt your package and execute with a password for execution.
* Encrypt password connections: you can encrypt your password of connections to avoid others see your passwords in package file.
* Multiple formats for your package file: You can create your package in TOML, YAML or JSON, choose your favorite!
* Ability to execute a job or complete workflow in a list of defined operative systems.

## Supported sources and destinations

Dixer allow to migrate data from and to:

* Microsoft SQL Server*
* MySQL
* IBM DB2*
* Oracle*
* Excel file (.xlsx)
* CSV
* XML
* JSON
* Firebird SQL
* PostgreSQL
* Variables
* SQLite3*
* Ragged Right File
* Fixed Width File
* SAP HANA DB
* HTML Table (only destination)
* Markdown Table (only destination)

**Microsoft SQL Server requires TLS 1.2 (MSSQL 2008 SP4 or superior, MSSQL 2008 R2 SP3 or superior).*

**IBM-DB2 requires clidriver, use [this link](https://public.dhe.ibm.com/ibmdl/export/pub/software/data/db2/drivers/odbc_cli/) or [this](https://www.ibm.com/support/pages/node/323035) to download it. In Windows is runtime need it, but others OS need it to execute the Dixer binary.*

**Oracle requires [Oracle Instant Client](https://www.oracle.com/database/technologies/instant-client/downloads.html) at runtime.*

**SQLite3 authentication with user and password not supported. Also encrypted databases not supported.*

## Used libraries

Dixer stands on the shoulder of many great open source libraries, in lexical order:

| Library                                                                                                  | Version or commit used                                                                                               | Modified library to use in Dixer                                            | License                                                                                           |
|----------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------|
| [github.com/360EntSecGroup-Skylar/excelize](https://github.com/360EntSecGroup-Skylar/excelize)           | [v2.4.0](https://github.com/360EntSecGroup-Skylar/excelize/tree/v2.4.0)                                              |                                                                             | [BSD 3-Clause "New" or "Revised" License](dependencies-licenses/LICENSE-excelize.txt)             |
| [github.com/antonmedv/expr](https://github.com/antonmedv/expr)                                           | [v1.8.9](https://github.com/antonmedv/expr/tree/v1.8.9)                                                              |                                                                             | [MIT License](dependencies-licenses/LICENSE-expr.txt)                                             |
| [github.com/awalterschulze/gographviz](https://github.com/awalterschulze/gographviz)                     | [v2.0.3](https://github.com/awalterschulze/gographviz/tree/v2.0.3)                                                   |                                                                             | [Apache License 2.0](dependencies-licenses/LICENSE-gographviz.txt)                                |
| [github.com/aws/aws-sdk-go](https://github.com/aws/aws-sdk-go)                                           | [v1.38.54](https://github.com/aws/aws-sdk-go/tree/v1.38.54)                                                          |                                                                             | [Apache License 2.0](dependencies-licenses/LICENSE-aws-sdk-go.txt)                                |
| [github.com/denisenkom/go-mssqldb](https://github.com/denisenkom/go-mssqldb)                             | [a78da2aabd817](https://github.com/denisenkom/go-mssqldb/tree/a78da2aabd817)                                         | [github.com/xhit/go-mssqldb](https://github.com/xhit/go-mssqldb/tree/sdi)   | [BSD 3-Clause "New" or "Revised" License](dependencies-licenses/LICENSE-go-mssqldb.txt)           |
| [github.com/fatih/color](https://github.com/fatih/color)                                                 | [v1.12.0](https://github.com/fatih/color/tree/v1.12.0)                                                               |                                                                             | [MIT License](dependencies-licenses/LICENSE-color.txt)                                            |
| [github.com/godror/godror](https://github.com/godror/godror)                                             | [v0.25.1](https://github.com/godror/godror/tree/v0.25.1)                                                             |                                                                             | [UPL-1.0](dependencies-licenses/LICENSE-godror.txt)                                               |
| [github.com/go-sql-driver/mysql](https://github.com/go-sql-driver/mysql)                                 | [v1.6.0](https://github.com/go-sql-driver/mysql/tree/v1.6.0)                                                         |                                                                             | [Mozilla Public License 2.0](dependencies-licenses/LICENSE-mysql.txt)                             |
| [github.com/hyperboloide/lk](https://github.com/hyperboloide/lk)                                         | [b535f197311](https://github.com/hyperboloide/lk/tree/b535f19731186294f7ae48d8e453186f40a493aa)                      |                                                                             | [MIT License](dependencies-licenses/LICENSE-lk.txt)                                               |
| [github.com/ibmdb/go_ibm_db](https://github.com/ibmdb/go_ibm_db)                                         | [v0.4.1](https://github.com/ibmdb/go_ibm_db/tree/v0.4.1)                                                             |                                                                             | [BSD 3-Clause "New" or "Revised" License](dependencies-licenses/LICENSE-go_ibm_db.txt)            |
| [github.com/jlaffaye/ftp](https://github.com/jlaffaye/ftp)                                               | [5d4190119067](https://github.com/jlaffaye/ftp/tree/5d4190119067)                                                    |                                                                             | [ISC License](dependencies-licenses/LICENSE-ftp.txt)                                              |
| [github.com/joho/godotenv](https://github.com/joho/godotenv)                                             | [v1.3.0](https://github.com/joho/godotenv/tree/v1.3.0)                                                               |                                                                             | [MIT License](dependencies-licenses/LICENSE-godotenv.txt)                                         |
| [github.com/lib/pq](https://github.com/lib/pq)                                                           | [9e747ca506](https://github.com/lib/pq/tree/9e747ca506)                                                              | [github.com/xhit/pq](https://github.com/xhit/pq/tree/sdi-oid)               | [MIT License](dependencies-licenses/LICENSE-pq.txt)                                               |
| [github.com/mattn/go-sqlite3](https://github.com/mattn/go-sqlite3)                                       | [v1.14.7](https://github.com/mattn/go-sqlite3/tree/v1.14.7)                                                          |                                                                             | [MIT License](dependencies-licenses/LICENSE-go-sqlite3.txt)                                       |
| [github.com/mdaines/viz.js](https://github.com/mdaines/viz.js)                                           | [v2.1.2](https://github.com/mdaines/viz.js/tree/v2.1.2)                                                              |                                                                             | [MIT License](dependencies-licenses/LICENSE-viz.js.txt)                                           |
| [github.com/nakagami/firebirdsql](https://github.com/nakagami/firebirdsql)                               | [72ac8744015a](https://github.com/nakagami/firebirdsql/tree/72ac8744015a)                                            |                                                                             | [MIT License](dependencies-licenses/LICENSE-firebirdsql.txt)                                      |
| [github.com/otiai10/copy](https://github.com/otiai10/copy)                                               | [v1.2.0](https://github.com/otiai10/copy/tree/v1.2.0)                                                                |                                                                             | [MIT License](dependencies-licenses/LICENSE-copy.txt)                                             |
| [github.com/pelletier/go-toml](https://github.com/pelletier/go-toml)                                     | [v1.9.3](https://github.com/pelletier/go-toml/tree/v1.9.3)                                                           |                                                                             | [MIT License](dependencies-licenses/LICENSE-go-toml.txt)                                          |
| [github.com/SAP/go-hdb](https://github.com/SAP/go-hdb)                                                   | [v0.105.1](https://github.com/SAP/go-hdb/tree/v0.105.1)                                                              |                                                                             | [Apache License 2.0](dependencies-licenses/LICENSE-go-hdb.txt)                                    |
| [github.com/shopspring/decimal](https://github.com/shopspring/decimal)                                   | [v1.2.0](https://github.com/shopspring/decimal/tree/v1.2.0)                                                          |                                                                             | [MIT License](dependencies-licenses/LICENSE-decimal.txt)                                          |
| [github.com/tamerh/jsparser](https://github.com/tamerh/jsparser)                                         | [v1.5.0](https://github.com/tamerh/jsparser/tree/v1.5.0)                                                             |                                                                             | [MIT License](dependencies-licenses/LICENSE-jsparser.txt)                                         |
| [github.com/tamerh/xml-stream-parser](https://github.com/tamerh/xml-stream-parser)                       | [v1.4.0](https://github.com/tamerh/xml-stream-parser/tree/v1.4.0)                                                    |                                                                             | [BSD 3-Clause "New" or "Revised" License](dependencies-licenses/LICENSE-xml-stream-parser.txt)    |
| [github.com/tiaguinho/gosoap](https://github.com/tiaguinho/gosoap)                                       | [v1.4.4](https://github.com/tiaguinho/gosoap/tree/v1.4.4)                                                            |                                                                             | [MIT License](dependencies-licenses/LICENSE-gosoap.txt)                                           |
| [github.com/xhit/go-simple-mail](https://github.com/xhit/go-simple-mail)                                 | [v2.10.0](https://github.com/xhit/go-simple-mail/tree/v2.10.0)                                                       |                                                                             | [MIT License](dependencies-licenses/LICENSE-go-simple-mail.txt)                                   |
| [github.com/xhit/go-str2duration](https://github.com/xhit/go-str2duration)                               | [v2.0.0](https://github.com/xhit/go-str2duration/tree/v2.0.0)                                                        |                                                                             | [BSD 3-Clause "New" or "Revised" License](dependencies-licenses/LICENSE-go-str2duration.txt)      |
| [github.com/xinsnake/go-http-digest-auth-client](https://github.com/xinsnake/go-http-digest-auth-client) | [v0.6.0](https://github.com/xinsnake/go-http-digest-auth-client/tree/v0.6.0)                                         |                                                                             | [BSD 2-Clause "Simplified" License](dependencies-licenses/LICENSE-go-http-digest-auth-client.txt) |
| [golang.org/x/term](https://golang.org/x/term)                                                           | [6886f2dfbf5b](https://github.com/golang/term/tree/6886f2dfbf5b)                                                     |                                                                             | [BSD-3-Clause](dependencies-licenses/LICENSE-term.txt)                                            |
| [golang.org/x/text](https://golang.org/x/text)                                                           | [22f1617af](https://github.com/golang/text/tree/22f1617af38ed4cd65b3b96e02bab267e560155c)                            | [github.com/xhit/text](https://github.com/xhit/text/tree/sdi)               | [BSD-3-Clause](dependencies-licenses/LICENSE-text.txt)                                            |
| [gopkg.in/yaml.v2](https://gopkg.in/yaml.v2)                                                             | [v2.4.0](https://github.com/go-yaml/yaml/tree/v2.4.0)                                                                |                                                                             | [Apache License 2.0](dependencies-licenses/LICENSE-yaml.txt)                                      |
