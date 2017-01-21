# Useful AWS Stuff

#### Tips
AMI is Amazon Instance (a VM) - good practice to create your own and save it off for quick boot ups


#### Custom metrics
- cloudwatch
- select ‘frontend’ in ‘custom metrics drop down’
- use filter


#### Instances
- ec2
- Auto Scaling
  * Launch Configurations (Select config)
  * Auto scaling groups (Edit in here)

  
## Elastic Beanstalk

#### Init
```bash
eb init
```

#### Create
```bash
eb create
```

#### Deploy
```bash
eb deploy
```

#### Abort
```bash
eb abort
```

#### Logs
```bash
eb logs
```


#### View current events
```bash
eb events -f
```

#### Terminate
Remove environment and delete application
```bash
eb terminate
```

#### Open
Open site in browser

```bash
eb open
```

## S3

#### Policy

Add/Overwrite policy on s3 bucket
```
aws s3api put-bucket-policy --bucket <bucket_name> --policy file://policy.json
```

#### Upload
Upload to S3 bucket with server side encryption

```
aws s3 cp test.txt s3://<bucket_name>/<file_name> --sse
```