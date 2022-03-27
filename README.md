# IP ranges

Lists IP ranges of misc internet services. Currently, updated only in manual mode.

Latest update: 2022-03-26

## Example of manual getting data from BGP.HE.NET

```javascript
{
  const IPs = [];
  document.querySelectorAll('#table_prefixes4 tr > *:first-child, #table_prefixes6 tr > *:first-child').forEach(function(el){
    const val = el.innerText.replace(/^\s+/, '').replace(/\s+$/, '');
    if (/^\d{1,3}\.\d{1,3}\.\d{1,3}\.\d{1,3}(?:\/\d{1,2})?$/.test(val) // IPv4
      || /^[a-fA-F\d:]{2,}(?:\/\d{1,3})?$/.test(val) && val.replace(/[^:]/g, '').length > 1 // IPv6
    ) {
      IPs.push(val);
    } else {
      console.log('Wrong value: ' + val);
    }
  });
  if (IPs.length) {
    const w = window.open();
    w.document.body.innerHTML = '<pre></pre>';
    w.document.querySelector('pre').textContent = IPs.join('\n');
  } else {
    console.log('IP ranges not found!');
  }
}
```
