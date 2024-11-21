# Setting up of Jenkins:
```
sudo curl -o /etc/yum.repos.d/jenkins.repo \
    https://pkg.jenkins.io/redhat-stable/jenkins.repo
sudo rpm --import https://pkg.jenkins.io/redhat-stable/jenkins.io-2023.key
sudo yum upgrade --> takes too much time, we can skip
# Add required dependencies for the jenkins package
sudo yum install fontconfig java-17-openjdk
sudo yum install jenkins
sudo systemctl daemon-reload
sudo systemctl start jenkins
sudo systemctl enable jenkins
```

# Disadvantages of Freestyle project:
```
1)Can't be restored if somethig goes wrong
2)can't reuse the code
3)Not possible to review the code (PR)
4)no version control
5)But we can track the changes which we did.
```