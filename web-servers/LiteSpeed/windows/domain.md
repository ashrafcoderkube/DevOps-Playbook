### Domain Configuration File for LiteSpeed on Windows

#### Non-SSL Configuration

```xml
<virtualHost>
    <name>mywebsite.local</name>
    <root>C:/litespeed/mywebsite/html</root>
    <docRoot>C:/litespeed/mywebsite/html</docRoot>
</virtualHost>
```

#### SSL Configuration

```xml
<listener>
    <address>*:443</address>
    <name>SSLListener</name>
    <secure>1</secure>
    <sslCert>C:/litespeed/ssl/server.crt</sslCert>
    <sslKey>C:/litespeed/ssl/server.key</sslKey>
</listener>

<virtualHost>
    <name>sslsite.local</name>
    <root>C:/litespeed/sslsite/html</root>
    <docRoot>C:/litespeed/sslsite/html</docRoot>
</virtualHost>
```

#### Enabling Proxy Configuration (Optional)

If you want to set up a reverse proxy, you need to update the configuration file:

```xml
<virtualHost>
    <name>proxy.local</name>
    <root>C:/litespeed/proxy/html</root>
    <docRoot>C:/litespeed/proxy/html</docRoot>
    <context>
        <type>proxy</type>
        <uri>/*</uri>
        <address>http://backend.local</address>
    </context>
</virtualHost>
```

This configuration file includes settings for both non-SSL and SSL domains on a LiteSpeed server running on Windows. Adjust the paths and settings as needed for your specific setup.

