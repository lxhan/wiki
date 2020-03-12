# AWS

## Install AWS cli (mac)
```sh
curl "https://awscli.amazonaws.com/AWSCLIV2.pkg" -o "AWSCLIV2.pkg"
sudo installer -pkg AWSCLIV2.pkg -target /
```

### Confirm the installation
```sh
which aws
/usr/local/bin/aws

aws --version
```

## Configure AWS cli
```sh
aws configure
AWS Access Key ID [None]: AKIAIOSFODNN7EXAMPLE
AWS Secret Access Key [None]: wJalrXUtnFEMI/K7MDENG/bPxRfiCYEXAMPLEKEY
Default region name [None]: us-west-2
Default output format [None]: json
```

## S3 commands

### List all buckets
```sh
aws s3 ls
```

### List all folders and objects in bucket
```sh
aws s3 ls s3://bucket-name
```

### Download object to local computer
```sh
aws s3 cp s3://bucket-name/files/image.jpg
```

### Upload object
```sh
aws s3 cp ~/Desktop/image.jpg s3://bucket-name/files/image.jpg
```

### Create presigned url that expires in 300 sec
```sh
aws s3 presign s3://bucket-name/files/image.jpg --expires-in 300
```
