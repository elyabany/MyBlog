# Mitigation

## 1. Output Encoding <a href="#output-encoding" id="output-encoding"></a>

```java
// Use OWASP Java Encoder 
import org.owasp.encoder.Encode; 
// Let's say that the vulnerable Field is `Field1` and Is HTML 
String New_Field1 = Encode.forHtml(field1)
// Let's say that  the vulnerable Field is `Field1` and Is JavaScript
String New_Field1 = Encode.forJavaScript(field1)
```

## 2. Whitelisting&#x20;

Use **Whitelisting** instead of **blacklisting** because in **blacklisting** hackers can find a workaround&#x20;

```java
// Let's say we want to make a blacklist for " script & alert" 
  if (field1.contains("script")) {
            return new IllegalConnectorArgumentsException();
        }
```

in this example we made a blacklist for  <mark style="color:red;">script & alert</mark>  **Attacker** can still Use **XSS Payload** such as&#x20;

```javascript
<a href="javascript:confirm`1`">click</a>

```
