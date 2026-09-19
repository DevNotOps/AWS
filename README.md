```bash
 aws account put-contact-information --contact-information '
{
"FullName":"jhon adam",
"PhoneNumber":"201050",
"AddressLine1":"egypt",
"City":"behara",
"PostalCode":"5020",
"CountryCode":"BE",
"StateOrRegion":"WA"}'
```

## 1- EC2 
- create EC2 key pair
 ```bash
 aws ec2 create-key-pair --keyname keyname --quiry 'KeyMaterial' --output text | tee key.pam
```
