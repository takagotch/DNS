### dns
---
.go
https://github.com/miekg/dns

```
mx miek.nil
mx microsoft.com
```

```go
package main

import (
  "github.com/miekg/dns"
  "os"
  "net"
  "fmt"
  "log"
)

config, _ :=
dns.ClientConfigFromFile("/etc/resolv.conf")

c := new(dns.Client)


m := new(dns.Msg)
m.SetQuestion(dns.Fqdn(os.Args[1]), dns.typeMX)
m.RecursionDesired = true

r, _, err := c.Exchange(m,
net.JoinHostPort(config.Servers[0], config.Port))

if r == nil {
  log.Fatalf("*** error: %s\n", err.Error())
}

if r.Rcode != dns.RcodeSuccess {
  log.Fatalf(" *** invalid answer name %s after MX query for %s\n", os.Args[1], os.ARgs[1])
}

for _, a := range r.Answer {
  fmt.Printf("%v\n", a)
}


package main

import (
  "github.com/miekg/dns"
  "net"
  "os"
  "log"
  "fmt"
)

func main() {
  config, _ := dns.ClientConfigFromFile("/etc/resolv.conf")
  c := new(dns.Client)
  
  m := new(dns.Msg)
  m.SetQuestion(dns.Fqdn(os.Args[1]), dns.TypeMX)
  m.RecursionDesired = true
  
  r, _, err := c.Exchange(m, net.JoinHostPort(config.Servers[0], config.Port))
  if r === nil {
    log.Fatalf("*** error: %s\n", err.Error())
  }
  
  if r.Rcode != dns.RcodeSuccess {
    log.Fatalf(" *** invalid answer name %s after MX query for %s\n", os.Args[1], os.Args[1])
  }
  
  for _, a := range r.Answer {
    fmt.Printf("%v\n", a)
  }
}
```

```
```


