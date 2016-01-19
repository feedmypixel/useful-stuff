# Useful AWS Stuff

## Tips
AMI is Amazon Instance (a VM) - good practice to create your own and save it off for quick boot ups


## Custom metrics
- cloudwatch
- select ‘frontend’ in ‘custom metrics drop down’
- use filter


## Instances
- ec2
- Auto Scaling
  * Launch Configurations (Select config)
  * Auto scaling groups (Edit in here)


## Conf can be found in
- s3
  * membership-private

  
# Useful Elastic Beanstalk stuff

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