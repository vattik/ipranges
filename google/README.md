# IP ranges of Google Services

## Example of manual getting data from GSTATIC.COM

```shell
rm google.txt google-cloud.txt
wget -O google.txt https://www.gstatic.com/ipranges/goog.txt
wget -O google-cloud.json https://www.gstatic.com/ipranges/cloud.json
jq '.prefixes[] | [.ipv4Prefix][] | select(. != null)' -r google-cloud.json >> google-cloud.txt
jq '.prefixes[] | [.ipv6Prefix][] | select(. != null)' -r google-cloud.json >> google-cloud.txt
rm google-cloud.json
```
