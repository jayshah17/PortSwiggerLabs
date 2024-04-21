## Lab Description: DOM XSS in document.write sink using source location.search

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/174392e2-0c14-4e02-bb76-037412046596)

## Solution
We straightaway see a search functionality.

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/86764a4d-297a-4191-b403-94225a498945)

A simple XSS attempt fails:

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/564c94ec-6782-4289-a32f-a96b0639d3b4)

Looking at the page source, the search term displayed is properly encoded. However, it also shows that a javascript takes the search term out of the URL and writes it into an img-tag for some type of tracking:

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/c1742c21-b07d-450c-ba08-62114904418d)


```
<script>
                        function trackSearch(query) {
                            document.write('<img src="/resources/images/tracker.gif?searchTerms='+query+'">');
                        }
                        var query = (new URLSearchParams(window.location.search)).get('search');
                        if(query) {
                            trackSearch(query);
                        }
</script>
```

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/fce632b1-6951-473d-9a6e-10ac0e41d8c6)

Using the browser tools, I can inspect the resulting HTML. It is visible that my search term is embedded without any apparent safeguards:

Of course, the script tags are within a string here, so they are harmless. However, if I can terminate the string by injecting double quotes, then I can manipulate the resulting HTML freely.

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/55bd8af0-5a02-43c5-a9b8-37419c0a7431)

it trigger an alert.

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/52dac4fa-d769-4563-9d30-119873299a59)

Lab Solves with it 

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/ff50ad16-6b9d-4f99-933b-20eeadf57b46)


