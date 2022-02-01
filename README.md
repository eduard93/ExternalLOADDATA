# ExternalLOADDATA

## Running

1. Start docker: `docker compose up -d`
2. Open SQL Home in [SMP](http://localhost:52773/csp/sys/exp/%25CSP.UI.Portal.SQL.Home.zen?$NAMESPACE=USER).
3. Execute query:

```sql
LOAD DATA FROM FILE '/data/in.csv' 
INTO dc.Request(Text, Topic) VALUES (Text, Topic) 
USING {"from":{"file":{"header":"1"}}}
```

4. Confirm error:

```
[SQLCODE: <-400>:<Fatal error occurred>]
[%msg: <java.lang.NoSuchFieldError: EMPTY_STRING_AS_NULL>]
```
