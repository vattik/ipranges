# IP ranges

Lists IP ranges of misc internet services. Currently, updated only in manual mode.

| Services                  | Downloads                                                                                                                                                                                  |
| ------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Google                    | [google.txt](https://raw.githubusercontent.com/vattik/ipranges/main/google/google.txt), [google-cloud.txt](https://raw.githubusercontent.com/vattik/ipranges/main/google/google-cloud.txt) |
| Mail.Ru and Odnoklassniki | [mail.ru.txt](https://raw.githubusercontent.com/vattik/ipranges/main/mail.ru/mail.ru.txt)                                                                                                  |
| Russian Government        | [ru-government.txt](https://raw.githubusercontent.com/vattik/ipranges/main/ru-government/ru-government.txt)                                                                                |
| VKontakte                 | [vkontakte.txt](https://raw.githubusercontent.com/vattik/ipranges/main/vkontakte/vkontakte.txt)                                                                                            |
| Yandex                    | [yandex.txt](https://raw.githubusercontent.com/vattik/ipranges/main/yandex/yandex.txt)                                                                                                     |

**Latest update:** 2022-03-26

---

##### Example of manual getting data from BGP.HE.NET

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
