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