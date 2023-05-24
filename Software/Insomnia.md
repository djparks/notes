# Notes about Insomnia

## Terms

Base Environment
Sub Environments
Folder Environments (Be accessed from folder drop-down in side bar)

### Environment Priority

1. Folder Environment (highest priority)
2. Sub Environment
3. Base Environment (lowest priority)

Example of Environment with `recursive` variables:

```JSON
{
    "base_url": "[protocol]://[domain][[path]",
    "protocol": "https",
    "domain": "api.myproduct.com",
    "path": "/v1",
    "now": "[Timestamp->Milliseconds]
}
```

Workspaces introduces a way to group Request Collections (also called Collections) and Design Documents (also called Documents).
