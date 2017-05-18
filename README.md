# datomic-session-store

A Datomic session store for ring applications.

This library differs very little
from [datomic-session-store](https://github.com/gfZeng/datomic-session-store),
but has some Starcity-specific differences that warranted use as a separate
library.

## Usage

Ensure that the following schema attributes are installed:

```edn
{:db/id                 (d/tempid :db.part/db)
 :db/ident              :session/key
 :db/valueType          :db.type/string
 :db/unique             :db.unique/identity
 :db/cardinality        :db.cardinality/one
 :db.install/_attribute :db.part/db}
{:db/id                 (d/tempid :db.part/db)
 :db/ident              :session/account
 :db/valueType          :db.type/ref
 :db/cardinality        :db.cardinality/one
 :db.install/_attribute :db.part/db}
{:db/id                 (d/tempid :db.part/db)
 :db/ident              :session/value
 :db/valueType          :db.type/bytes
 :db/cardinality        :db.cardinality/one
 :db/noHistory          true
 :db.install/_attribute :db.part/db}
```

Our [blueprints](https://github.com/starcity-properties/blueprints) library will
install this schema if used.
