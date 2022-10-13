---
description: >-
  Cross-Site Scripting (also known as XSS) is a vulnerability/flaw that combines
  the allowance of HTML/script tags as input that renders into a browser without
  encoding or sanitization.
---

# Cross Site Script

## **Quick examples:**

```javascript
alert("XSS Test"); 
alert(document.cookie); // will show the session cookie
```



## Most common locations to test for <mark style="color:red;">XSS</mark> <a href="#_most_common_locations" id="_most_common_locations"></a>

* Search fields that reflect a search string back to the user
* Input fields that reflect user data
* Error messages that return user-supplied text
* Hidden fields that contain user-supplied data
* Any page that displays user-supplied data
  * Message boards
  * Free form comments
* HTTP Headers

## XSS attacks may result in <a href="#_xss_attacks_may_result_in" id="_xss_attacks_may_result_in"></a>

* Stealing session cookies
* Creating false requests
* Creating false fields on a page to collect credentials
* Redirecting your page to a "non-friendly" site
* Creating requests that masquerade as a valid user
* Stealing confidential information
* Execution of malicious code on an end-user system (active scripting)





## Types of XSS <a href="#_types_of_xss" id="_types_of_xss"></a>

### Reflected <a href="#_reflected" id="_reflected"></a>

* Malicious content from a user request is displayed to the user in a web browser
* Malicious content is written into the page after from server response
* Social engineering is required
* Runs with browser privileges inherited from the user in a browser

### DOM-based (also technically reflected) <a href="#_dom_based_also_technically_reflected" id="_dom_based_also_technically_reflected"></a>

* Client-side scripts use malicious content from a user request to write HTML to its page
* Similar to reflected XSS
* Runs with browser privileges inherited from the user in a browser

### Stored or persistent <a href="#_stored_or_persistent" id="_stored_or_persistent"></a>

* Malicious content is stored on the server ( in a database, file system, or other objects) and later displayed to users in a web browser
* Social engineering is not required







