# Terraform基础设施即代码

## 基本概念
- **Provider**: 云服务商插件(AWS/GCP/Azure)
- **Resource**: 基础设施资源定义
- **State**: 资源状态跟踪
- **Module**: 可复用的配置模块

## 示例: AWS EC2
```hcl
provider "aws" {
  region = "us-east-1"
}

resource "aws_instance" "web" {
  ami           = "ami-0c55b159cbf701d0f"
  instance_type = "t3.micro"

  tags = {
    Name = "WebServer"
  }
}
```

## 工作流
```bash
terraform init
terraform plan
terraform apply
terraform destroy
```

---
*更新时间: {DATETIME_STR}*
