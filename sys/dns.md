# DNS

## Useful resources
- [DNS Dumpster](https://dnsdumpster.com/)

## Analyze yourself
```sh
# Trace the DNS query for google.co.uk.
dig +trace www.google.co.uk. # The last "." is implicit, but it's there for the root (root name servers)

# +trace works like doing the following calls one after the other
dig +norecurse @192.5.5.241 www.google.co.uk # Ask a root NS for the next step for google.co.uk
# 192.5.5.241 only knows about the .uk domains, so it gives a list of referrals for it
# Pick one of them (the referrals) and repeat
dig +norecurse @195.66.240.130 www.google.co.uk

# ...keep repeting
# dig +norecurse @referral-i www.google.co.uk
# dig +norecurse @referral-i+1 www.google.co.uk
# ...
#
# Until result:
#
# ;; AUTHORITY SECTION:
# www.google.co.uk.       300     IN      A       74.125.225.216
# www.google.co.uk.       300     IN      A       74.125.225.223
# ...
# This is the result(s) we want ^^
```

## Useful commands

### Check specific records with dig
```
dig -t [txt|a|cname|ptr|...] google.com
```

### Check using a specific server
```
dig @NS_IP_OR_FQDN google.com
```

### Find the DNS Authority Record for a DNS Domain (SOA)
```sh
# Get soa and serial
dig +short SOA google.com | cut -d " " -f 1,3
```

### Get the NAME from the IP (uses PTR)
```
dig -x IP
```
