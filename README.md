# Heading level 1
## Heading level 2
### Heading level 3
#### Heading level 4
##### Heading level 5
###### Heading level 6

## List
- First item
- Second item
- Third item
- Fourth item
#### -----------------
* First item
* Second item
* Third item
* Fourth item
#### -----------------
+ First item
+ Second item
+ Third item
+ Fourth item
#### -----------------
- First item
- Second item
- Third item
    - Indented item
    - Indented item
- Fourth item

## Ordered list
1. First item
2. Second item
3. Third item
4. Fourth item
#### -----------------
1. First item
1. Second item
1. Third item
1. Fourth item
#### -----------------
1. First item
8. Second item
3. Third item
5. Fourth item
#### -----------------
1. First item
2. Second item
3. Third item
    1. Indented item
    2. Indented item
4. Fourth item


## Bold and *Italic*
Italicized text is the *cat's meow*.
**Italicized** text is the _cat's meow_.
A*cat*meow

## 
I just love **bold text**.
I just love __bold text__.
Love**is**bold

## Table 01
| Name       | Age | Occupation      |
|------------|-----|-----------------|
| John       | 30  | Software Engineer |
| Emily      | 25  | Graphic Designer |
| Michael    | 35  | Data Analyst     |
| Jessica    | 28  | Project Manager  |

## table 02
| Item                | Quantity | Price (USD) |
|---------------------|---------:|------------:|
| Laptop              |        2 |      1000   |
| Smartphone          |        3 |       500   |
| Headphones          |        5 |        50   |
| External Hard Drive |        1 |       150   |

## table 03
| Syntax      | Description | Test Text     |
| :---        |    :----:   |          ---: |
| Header      | Title       | Here's this   |
| Paragraph   | Text        | And more      |


## paragraph
This is the first `paragraph`. It contains some text to demonstrate how Markdown handles paragraphs. Each continuous block of text, separated by a blank line, is treated as a separate paragraph.

**This is the second paragraph. Markdown is a lightweight markup language that allows you to write simple and easy-to-read formatted text. It's widely used for creating documentation, `README` files, blogs, and more**.

*And this is the third paragraph*. Markdown provides various features such as headers, lists, code blocks, [links](https://www.devopseasylearning.com/), images, and more. It's a convenient and human-readable way to create formatted content without needing to deal with complex HTML or other markup languages.


## Block of code 
```
#!/bin/bash

# Simple bash script to calculate the factorial of a number

read -p "Enter a number: " number

if [[ $number -lt 0 ]]; then
    echo "Error: Factorial is not defined for negative numbers."
elif [[ $number -eq 0 ]]; then
    echo "Factorial of 0 is 1."
else
    factorial=1
    for (( i=1; i<=$number; i++ )); do
        factorial=$(( factorial * i ))
    done
    echo "Factorial of $number is $factorial."
fi
```

```sh
#!/bin/bash

# Simple bash script to calculate the factorial of a number

read -p "Enter a number: " number

if [[ $number -lt 0 ]]; then
    echo "Error: Factorial is not defined for negative numbers."
elif [[ $number -eq 0 ]]; then
    echo "Factorial of 0 is 1."
else
    factorial=1
    for (( i=1; i<=$number; i++ )); do
        factorial=$(( factorial * i ))
    done
    echo "Factorial of $number is $factorial."
fi

mkdir tia
groupadd hr 
usermod -aG hr tia
```

```Dockerfile
FROM httpd
LABEL maintainer="ektech"
LABEL env="dev"
ARG port=80
USER root
RUN apt -y update
WORKDIR /usr/local/apache2/htdocs/

RUN rm -rf *
ADD ./code/* /usr/local/apache2/htdocs/

ENTRYPOINT ["httpd-foreground"]
EXPOSE ${port}
```

```s
pipeline {
    agent any
    
    environment {
        DOCKER_REGISTRY = "your-docker-hub-account/your-docker-repo"
        SSH_KEY_CREDENTIALS = "your-ec2-ssh-credentials-id"
        EC2_INSTANCE_IP = "your-ec2-instance-ip"
    }
    
    stages {
        stage('Build Docker Image') {
            steps {
                git 'https://github.com/tia12/s5-git-exercise.git'
                sh 'docker build -t ${DOCKER_REGISTRY}:${BUILD_NUMBER} .'
            }
        }
        
        stage('Push Docker Image') {
            steps {
                withDockerRegistry(credentialsId: 'docker-hub-credentials', url: '') {
                    sh 'docker push ${DOCKER_REGISTRY}:${BUILD_NUMBER}'
                }
            }
        }
        
        stage('Deploy to EC2') {
            steps {
                script {
                    // Copy the SSH private key to the Jenkins agent
                    withCredentials([sshUserPrivateKey(credentialsId: "${SSH_KEY_CREDENTIALS}", keyFileVariable: 'SSH_KEY')]) {
                        // SSH commands to deploy the image on EC2
                        sh "scp -i ${SSH_KEY} -o StrictHostKeyChecking=no -r ./code ec2-user@${EC2_INSTANCE_IP}:~"
                        sh "ssh -i ${SSH_KEY} -o StrictHostKeyChecking=no ec2-user@${EC2_INSTANCE_IP} 'docker stop my-httpd-container || true'"
                        sh "ssh -i ${SSH_KEY} -o StrictHostKeyChecking=no ec2-user@${EC2_INSTANCE_IP} 'docker rm my-httpd-container || true'"
                        sh "ssh -i ${SSH_KEY} -o StrictHostKeyChecking=no ec2-user@${EC2_INSTANCE_IP} 'docker pull ${DOCKER_REGISTRY}:${BUILD_NUMBER}'"
                        sh "ssh -i ${SSH_KEY} -o StrictHostKeyChecking=no ec2-user@${EC2_INSTANCE_IP} 'docker run -d -p 80:${port} --name my-httpd-container ${DOCKER_REGISTRY}:${BUILD_NUMBER}'"
                    }
                }
            }
        }
    }
}
```


```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: my-httpd-app
  labels:
    app: httpd
spec:
  replicas: 3  # Number of replicas (pods) to run
  selector:
    matchLabels:
      app: httpd
  template:
    metadata:
      labels:
        app: httpd
    spec:
      containers:
        - name: my-httpd-container
          image: your-registry/your-httpd-image:latest  # Replace with your actual image URL
          ports:
            - containerPort: 80

```

## links
- Kubernetes manifest generator [click here to access the web](https://k8syaml.com)
- Groovy validator online [here](https://onecompiler.com/groovy)
- Bash script validator online [here](https://replit.com/languages/bash)
- Yaml validator online [here](http://www.yamllint.com)
- vscode online [here](https://vscode.dev)
- Ubuntu VM online [here](https://linuxcontainers.org/lxd/try-it)
- Unix Permissions Calculator [here](http://permissions-calculator.org)
- crontab guru [here](https://crontab.guru)
- How Secure Is My Password? [here](https://www.security.org/how-secure-is-my-password/)
- kubeapps for helm chart [here](https://hub.kubeapps.com)
- Bitnami helm charts [here](https://github.com/bitnami/charts)
- Stable helm charts [here](https://github.com/helm/charts/tree/master/stabl)

[Click here to visit our website](https://www.devopseasylearning.com/)