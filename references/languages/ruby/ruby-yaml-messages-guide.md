1. create .yml doc in same folder
2. At top of .rb program: require 'yaml'
3. variable = YAML.load_file('file_name.yml')
4. prompt(variable['key'])