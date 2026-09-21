# AWS CLI Quick Reference

This README contains a few common AWS CLI commands for managing account information, IAM users, and EC2 instances.

## Prerequisites
- AWS CLI installed and configured
- Valid AWS credentials
- A default region or explicit `--region` in commands

## 1. Update account contact information

```bash
aws account put-contact-information \
  --contact-information '{
    "FullName":"John Adam",
    "PhoneNumber":"201050",
    "AddressLine1":"Egypt",
    "City":"Behara",
    "PostalCode":"5020",
    "CountryCode":"BE",
    "StateOrRegion":"WA"
  }'
```

## 2. Create an IAM user

```bash
aws iam create-user \
  --user-name ahmed \
  --tags Key=Department,Value=HR Key=location,Value=egypt
```

Expected output includes a `User` object with the username, ARN, and tags.

## 3. Create an EC2 key pair

```bash
aws ec2 create-key-pair \
  --key-name my-key \
  --query 'KeyMaterial' \
  --output text > my-key.pem

chmod 400 my-key.pem
```

This saves the private key to `my-key.pem` and restricts permissions so it is not readable by other users.

## 4. Launch an EC2 instance

```bash
aws ec2 run-instances \
  --image-id ami-0123456789abcdef0 \
  --instance-type t2.micro \
  --key-name my-key \
  --region eu-west-2
```

## 5. Verify the instance

```bash
aws ec2 describe-instances --region eu-west-2
```

## Notes
- Replace example values with your own AWS account data.
- Use `--profile <profile-name>` if you are not using the default AWS profile.
- Always store private keys securely and avoid committing them to source control.
