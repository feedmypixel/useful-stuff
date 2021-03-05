# Useful Terraform Stuff


## Terraform
```
terraform --version
```

### Init and install resources
```
terraform init
```

### Help
```
terraform -help <sub_command>
```

### Show
```
terraform show
```

### Plan (tests a files changes)
```
terraform plan
```

### Refresh
```
terrform refresh
```

### Format
```
terraform fmt
```

### Graph
```
terraform graph
```

### View Graph via Graphviz
```
terraform graph | dot -Tsvg > graph.svg
```

### Outputs
```
terraform output
```

### Plan 
```
terraform plan
```

### Plan any dependencies
```
terraform plan-all
```

### Plan - save plan to file
```
terraform plan -out <filename>
```

### Taint
```
terraform taint <vm_instance_name>
```

### Destory
```
terraform destroy
```

### Terragrunt env install
```
tgenv install <version_number>
```

## Terragrunt
```
terragrunt --version
```

### Test a terragrunt file
```
terragrunt plan
```





## Terraform env
```
tfenv install <version_number>
```

### Terraform env use
```
tfenv use <version_number>
```

### Terraform list
```
tfenv list
```

### Terraform list remote
```
tfenv list-remote
```


