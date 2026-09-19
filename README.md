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
- lanche ec2
```bash
aws ec2 run-instances --image-id ami-0123456789abcdef0 --instance-type t2.micro --key-name user.pem --region eu-west-2
```
