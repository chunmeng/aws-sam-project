

# Installation
Prepare the workstation with required tools.

* [x] [Install AWS CLI v2](https://docs.aws.amazon.com/cli/latest/userguide/install-cliv2-linux.html)
  ```bash
  curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
  unzip awscliv2.zip
  sudo ./aws/install
  ```
  After the installation:
  ```bash
  aws --version
  aws-cli/2.0.10 Python/3.7.3 Linux/5.3.0-46-generic botocore/2.0.0dev14
  ```

* [x] [Install AWS SAM CLI](
https://docs.aws.amazon.com/serverless-application-model/latest/developerguide/serverless-sam-cli-install-linux.html)
  ```bash
  pip3 install --user aws-sam-cli
  ```
  __Note__ See troubleshooting section for issue with pip.

  After installtion:
  ```bash
  sam --version
  SAM CLI, version 0.48.0
  ```
## Troubleshooting
1. pip error after upgrade
   [Read here](https://askubuntu.com/questions/1025189/pip-is-not-working-importerror-no-module-named-pip-internal)

   Recovery steps that worked for me:
   * [x] Force reinstall pip
    ```bash
    curl https://bootstrap.pypa.io/get-pip.py -o get-pip.py
    python3 get-pip.py --user --force-reinstall
    ```
    __Note__ If this error is seen during the force-reinstall, some files are misplaced. Copy the files to upper dir and redo the above.
    ```bash
    FileNotFoundError: [Errno 2] No such file or directory: '/home/user/.local/lib/python3.6/site-packages/pip-19.0.1.dist-info/METADATA'
    ```
    
    Do this:
    ```bash
    cp ~/.local/lib/python3.6/site-packages/pip-19.0.1.dist-info/pip-19.0.1.dist-info/* ~/.local/lib/python3.6/site-packages/pip-19.0.1.dist-info/
    ```

# Configuration

* [x] aws configure
  
  Configure the credentials.
  This requires an IAM user with appropriate permission.
  * [ ] Currently use full administrative role. Need to find out exact permission.

# Project Workflow

* [x] Create a project directory
  ```bash
  mkdir go-sam-project
  cd go-sam-project/
  ```
* [x] Initialize the project with template for a specified runtime
  ```bash
  sam init --name sam-app --runtime go1.x --app-template hello-world
  ```


