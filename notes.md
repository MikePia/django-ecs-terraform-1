* Authenticate / login using aws cli
```
aws ecr get-login-password --region us-east-2
aws ecr get-login-password --region {region} | docker login --username AWS --password-stdin {aws_account_id}.dkr.ecr.{region}.amazonaws.com

aws ecr get-login-password --region us-west-1 | docker login --username AWS --password-stdin 760662774875.dkr.ecr.us-west-1.amazonaws.com


docker build -t 760662774875.dkr.ecr.us-west-1.amazonaws.com/django-app:latest .
docker push 760662774875.dkr.ecr.us-west-1.amazonaws.com/django-app:latest
docker build -t 760662774875.dkr.ecr.us-west-1.amazonaws.com/nginx:latest .
docker push 760662774875.dkr.ecr.us-west-1.amazonaws.com/nginx:latest
cd ..

```

## Notes for creating new public/private keys to use
* Use ssh-keygen to create a new key. When it asks to for a filename, 
    * give them an existing directory 
    * (Bash on Windows here) Don't use quotes, even if the path has spaces -- for ex
        * ***/c/Users/Fred Flintstone/.ssh/demo/key-for-demo***
```
ssh-keygen -t rsa -b 2048
Your public key has been saved in /c/Users/Fred Flintstone/.ssh/demo/key-for-demo.pub
```
* To keep it clean, use a variable to enter the key. 
    * When the main file referst to key_pair, use file method:
        * ```public_key = file(var.ssh_pubkey_file)```
    * in variables.tf the default value should be a file path
        * ```default = "~/.ssh/demo/key-for-demo.pub"```
        
