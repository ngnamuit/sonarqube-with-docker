# sonarqube-with-docker
# Project introduction
This project is guideline to help you set up sonar faster with docker.

# What's sonar?
to be continue

# How to setup
#### 1. Sonar image installing
- Run command line to install:  ```docker pull sonarqube```
- Start sonarqube docker: ``` docker run -p 9000:9000 sonarqube```
- Check sonarqube docker status by ```docker ps | grep "sonarqube"``` -> open `localhost:9000` on your web browser -> to make sure that you started it successfully
- Document ref: https://hub.docker.com/_/sonarqube 

#### 2. Download sonar folder 
- Open link: https://docs.sonarqube.org/latest/analysis/scan/sonarscanner/
- Choose version to download -> Unzip it and you should rename it to `sonar` -> move it to `path/your_source_code`.
- Source code folder structure example:

```
path_your_source_code/
            A/
                file_A1.py
                file_A2.py
            B/
                file_B1.py
                file_B2.py
            C/
                file_C1.py
                file_C1.xml
                file_C1.html
```

- Create new file with name `sonar-project.properties` and edit as the below:

```
sonar.projectKey=demo-sonar

sonar.sources= A, B    # current source that you want to analyze
sonar.exclusions= C    # path/folder_you_wanna_exclude 

sonar.host.url=http://localhost:9000/
sonar.login=admin       #  default login
sonar.password=admin    #  default username
```

#### 3. Run the below commands to start analyzing your project: 
```
cd path/your_source_code
sonar/bin/sonar-scanner -Dproject.settings=sonar-project.properties -X
```

#### 4. Then open `localhost:9000` and you will see `project name` on project tab if you done all of the above steps.



##### *** If you have any issue or concert, please help to leave a comment on issue tab and I will check and resolve it if I can ****
###Thanks and good luck, guys!