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

## 1- create IAM user
```bash
aws iam create-user --user-name ahmed --tags Key=Department,Value=HR Key=location,Value=egypt
```
### output:

```bash
{
    "User": {
        "Path": "/",
        "UserName": "ahmed",
        "UserId": "AIDAK2R13L6CIPPTND9Q",
        "Arn": "arn:aws:iam::000000000000:user/ahmed",
        "CreateDate": "2026-09-21T11:38:56.897430+00:00",
        "Tags": [
            {
                "Key": "Department",
                "Value": "HR"
            },
            {
                "Key": "location",
                "Value": "egypt"
            }
        ]
    }
}
```

## 5- EC2 
- create EC2 key pair
 ```bash
 aws ec2 create-key-pair --keyname keyname --quiry 'KeyMaterial' --output text | tee key.pam
```
- lanche ec2
```bash
aws ec2 run-instances --image-id ami-0123456789abcdef0 --instance-type t2.micro --key-name user.pem --region eu-west-2
```
