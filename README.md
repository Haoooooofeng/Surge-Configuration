# Surge-Configuration
A Surge configuration for Shadowsocks (Including SSEncrypt.module)

## Rule

Rules are matched from the first one to the last one, in the order they appear in the config file. In other words, rules in front have higher priority than rules in the back.

Example:
```
[Rule]  
DOMAIN-SUFFIX,company.com,ProxyA  
DOMAIN-KEYWORD,google,DIRECT  
GEOIP,US,DIRECT  
IP-CIDR,192.168.0.0/16,DIRECT  
FINAL ProxyB
```
Surge supports 6 different types of rule. Each rule consists of 3 parts: rule type, a traffic matcher (except for FINAL rule), and a proxy policy. Rule type is one of DOMAIN, DOMAIN-SUFFIX, DOMAIN-KEYWORD, GEOIP, IP-CIDR, or FINAL. Proxy policy must be one of a proxy name, DIRECT, or REJECT.
* DOMAIN  
```
DOMAIN,www.apple.com,Proxy
```
Rule matches if the domain of request matches exactly.
* DOMAIN-SUFFIX  
```
DOMAIN-SUFFIX,apple.com,Proxy
```
Rule matches if the domain of the request matches the suffix. For example: 'google.com' matches 'www.google.com', 'mail.google.com' and 'google.com', but does not match 'content-google.com'.
* DOMAIN-KEYWORD  
```
DOMAIN-KEYWORD,google,Proxy
```
Rule matches if the domain of the request contains the keyword.
* IP-CIDR  
```
IP-CIDR,192.168.0.0/16,DIRECT
IP-CIDR,10.0.0.0/8,DIRECT
IP-CIDR,172.16.0.0/12,DIRECT
IP-CIDR,127.0.0.1/8,DIRECT
```
Rule matches if the IP address of the request matches the specified range.
* GEOIP  
```
GEOIP,US,DIRECT
```
Rule matches if the GeoIP test result matches the specified country code.
* FINAL  
```
FINAL,DIRECT
```
Rule section must end with a FINAL statement, to specify the default policy.

## Learn More
**Surge** http://surge.run/manual/
