# Create HANA Cloud

https://developers.sap.com/tutorials/hana-cloud-deploying.html

default DB username: `DBADMIN`

# Query HANA on terminal

Install https://tools.hana.ondemand.com/#hanatools

extract and run `hdbsetup.exe`

```
hdbsql -n 9a515a48-184a-456f-bc52-c402b68554c9.hana.trial-us10.hanacloud.ondemand.com:443 -e -u YOUR_USERNAME -p YOUR_PASSWORD
```

`-e` flag is enable SSL

# Query HANA with VSCode

Install extension HANHA

---

At `Connection Options` box

- `Encrypted connection` field: checked
- `Validate Server Certificate` field: checked
- `SSL Crypto Provider` field: empty
- `SSL Trust Store` field: empty (not verify)
