# devops-netology

# Игнорируются все файлы и каталоги в каталогах .terraform 
**/.terraform/*

# Игнорировать файлы с расширением .tfstate и файлы содержащие в своем названии .tfstate.
*.tfstate
*.tfstate.*

# Игнорировать файлы логов
crash.log
crash.*.log

# Игнорировать файлы с расширениями .tfvars и .tfvars.json - которые содержат конфиденциальные данные

*.tfvars
*.tfvars.json

# Игнорировать файлы с расширениями _override.tf и _override.tf.json
override.tf
override.tf.json
*_override.tf
*_override.tf.json

# Игнорировать файлы конфигурации 
.terraformrc
terraform.rc
