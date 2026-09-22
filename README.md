```bash
 aws account put-contact-information \
--contact-information '{ \
"FullName":"jhon adam", \
"PhoneNumber":"201050", \
"AddressLine1":"egypt", \
"City":"behara", \
"PostalCode":"5020", \
"CountryCode":"BE", \
"StateOrRegion":"WA" \
}'
```
---------------------------------------------------------------------------------------------------------------------
1- create IAM user
```bash
aws iam create-user \
--user-name ahmed \
--tags Key=Department,Value=HR Key=location,Value=egypt
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
----------------------------------------------------------------------------------------------------------------------

5- EC2 
- create EC2 key pair
 ```bash
 aws ec2 create-key-pair \
--keyname keyname \
--quiry 'KeyMaterial'
--output text | tee key.pam
```

- lanche ec2

```bash
aws ec2 run-instances \
--image-id ami-0123456789abcdef0 \
--instance-type t2.micro \
--key-name user.pem \
--region eu-west-2
```
-----------------------------------------------------------------------------------------------------------------------
6- s3

- create bucket
```bash
aws s3 mb s3://bucket_name
```
```bash
make_bucket: bucket_name
```
- list s3 buckets
```bash
aws s3 ls
```
```bash
2026-09-22 00:19:56 whoami
```
- upload file to s3 bucket
```bash
aws s3 cp file_name s3://bucket_name/file_name
```
```bash
upload: ./main.txt to s3://bucket_name/file_name
```
- download files from s3 bucket
```bash
aws s3 cp  s3://whoami/main.txt main.txt
```
```bash
download: s3://whoami/main.txt to ./main.txt
```
- delete files form s3 bucket
```bash
aws s3 rm  s3://whoami/main.txt
```
```bash
delete: s3://whoami/main.txt
```
- list s3 bucket contant
```bash
s3 ls s3://bucket_name
```
```bash
2026-09-22 00:32:41         14 main.txt
```
- delete all files in s3 bucket
```bash
aws s3 rm s3://whoami --recursive
```
- delete s3 bucket
### if bucket is empty
```bash
aws s3 rb s3://bucket_name
```
### if not empty
```bash
aws s3 rb s3://whoami --force
```
-------------------------------------------------------------------------------------------------------------------------
7. Databases

```bash
aws rds create-db-instance \
--db-instance-identifier db_name \
--db-instance-class machine_type \
--master-username db_username \
--master-user-password db_password \
--engine db_type \
--allocated-storage db_storage_size
```
