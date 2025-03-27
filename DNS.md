# DNS

- Domain Name System that translates human friendly hostnames into machine IP addresses
- ex.) www.googe.com -> 172.217.18.36

## Terminologies

- **Domain Registrar**: where you register your domain name. (Route 53, GoDaddy...)
- **DNS Service**: service to manage DNS records. Usually provided by registrar but you can use route 53 as your dns service but godaddy is your registrar
- **DNS Records**: (A,AAAA,CNAME,NS)
- **Zone File**: contains DNS records
- **Name Server**: resolves DNS queries (Authoritative or Non-Authoritative)
- **Top Level Domain**: .com, .us, .gov, .org
- **Second Level Domain**: amazon.com, google.com
- **Sub Domain**: mail.google.com
- **Protocol**: http, sftp, ssh, smtp

## How DNS Works

### Scenario

You have a webserver hosted at example.com with an IP of 9.10.11.12. You would like to access this server using the domain name from your web browser.

### Steps

1. Enter example.com in the url bar and go
2. Ask your local DNS server usually assigned by company or ISP
3. If the Local server hasn't seen this address before, ask the Root DNS Server (managed by ICANN)
4. The Root server directs callers to a top level domain dns server for the corresponding top level domain (.com, .org, etc)
5. The browser then asks the top level domain dns server (managed by ICANN) for example.com
6. The TLD DNS returns an IP of the SLD DNS Server which is managed by your domain registrar
7. The browser asks the SLD for example.com
8. The SLD DNS server returns the ip of example.com after caching it
9. the browser uses the IP to load the page from example.com

## Records

### Record Parts

Each dns record contains:

- **Domain/Subdomain name**: example.com
- **Record Type**: A, AAAA, CNAME, NS
- **Value**: 12.34.56.78
- **Routing Policy**:
- **TTL**: amount of time the record is cached at DNS Resolvers

### Record Types

- **A**: maps a hostname to IPv4
- **AAAA**: maps a hostname to IPv6
- **CNAME**: maps a hostname to another hostname
- **NS**: Name servers for the hosted zone

## Hosted Zones

A container for records that define how to route traffic to a domain and its subdomains
