# Preparing Java for newer versions

## Running jdeprscan.exe

Here's what I did:

1. tell Maven to copy all dependencies into a folder
2. in that folder, run the command:
`find . -exec j deprscan { } \ ;`
Additions:
• set - -class-path to reduce errors
• add 2>/dev/null to ignore errors

## Deprecations documentation

- <https://docs.oracle.com/en/java/javase/19/docs/api/deprecated-list.html>
- <https://dev.java/learn/jvm/tools/core/jdeprscan/>
