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
> If you get a message about running terraform init in a folder when running `terragrunt plan`. 
> You can delete the cache folder and run `terragrunt plan` again


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

### Console
```
terragrunt console
```
> In the console you can type the name of a module to see whats available e.g `module.function_service` and enter will provide the properties that are avialable/exported on this module

### Test a terragrunt file
```
terragrunt plan
```

### Apply a terragrunt file
```
terragrunt apply
```

### State
```
terragrunt state
```

### Visibility
A lot of the visibility in Terraform/terragruntcomes from the logs when you run `terragrunt plan`
It will tell you whats changing and you can check over before you `terragrunt apply`.

State is also useful but this a little move complicated


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


