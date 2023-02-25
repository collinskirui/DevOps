### Jenkins Overview
- Jenkins is one of the most popular free open-source CI solutions that is widely used in software engineering
- Completely free, easy to install and rich in features and plugins,as many as 1500 different plugins are available for Jenkins
- Supports distributed builds with master-slave architecture
- Simple and user-friendly interface

<p align="center">
 <img src="images/jenkins_logo.png?raw=true" alt="Logo" width="50%" height="50%" />
</p>


### Why Do We Need Jenkins
1. Developers making code changes in parallel want to make sure that their changes integrate
without errors
-Without Jenkins, manual integration testing happens infrequently and it is time-consuming
2. Developers also want their changes built and tested in a standardized environment
-Jenkins provides a standardized build and test environment

### Jenkins Architecture

<p align="center">
 <img src="images/architecture.png?raw=true" alt="Logo" width="50%" height="50%" />
</p>


### Step by Step Jenkins Set-Up in VM (Ubuntu 22.04 LTS)

1. Check if you have java installed in your machine using this command:
   
    ```java --version```
<p align="center">
 <img src="images/java_version.png?raw=true" alt="Logo" width="50%" height="50%" />
</p>

_If java is not installed kindly check your system properties and install the necessary java package for example for my Ubuntu 22.04 LTS i installed:
22.04 LTS, I installed using:

    ```sudo apt install openjdk-11-jre-headless```

2. Add the repository key to your system

      ```wget -q -O - https://pkg.jenkins.io/debian-stable/jenkins.io.key |sudo gpg --dearmor -o /usr/share/keyrings/jenkins.gpg```

The _gpg --dearmor_ command is used to convert the key into a format that apt recognizes. Next, let’s append the Debian package repository address to the server’s sources.list

3. Append the Debian package repository address to the server’s sources.list:

     ```sudo sh -c 'echo deb [signed-by=/usr/share/keyrings/jenkins.gpg] http://pkg.jenkins.io/debian-stable binary/ > /etc/apt/sources.list.d/jenkins.list'```

_The [signed-by=/usr/share/keyrings/jenkins.gpg] portion of the line ensures that apt will verify files in the repository using the GPG key that you just downloaded._

4. Run   ```sudo apt update```

5. Install Jenkins  ```sudo apt install jenkins```

<p align="center">
 <img src="images/jenkins_install.png?raw=true" alt="Logo" width="50%" height="50%" />
</p>


6. Start Jenkins  ```sudo systemctl start jenkins.service```

7. Check status  ```sudo systemctl status jenkins```

<p align="center">
 <img src="images/jenkins_status.png?raw=true" alt="Logo" width="50%" height="50%" />
</p>


8. Set up Firewall Rules  ```sudo ufw allow 8080```

9. Install open ssh server if not installed and enable it

      ```sudo apt install openssh-server```

      ```sudo systemctl enable --now ssh```

10. Enable the firewall  and open ssh

      ```sudo ufw allow OpenSSH```

      ```sudo ufw enable```

11. Run ```sudo ufw status``` everything should be similiar as follows

<p align="center">
 <img src="images/ufw.png?raw=true" alt="Logo" width="50%" height="50%" />
</p>

12. Set up Jenkins to your browser by first running ```ifconfig``` to see your machine's ip address

13. To set up your installation, visit Jenkins on its default port, 8080, using your server domain name or your IP address: ``` http://your_server_ip_or_domain:8080```

- You should receive the Unlock Jenkins screen, which displays the location of the initial password:

<p align="center">
 <img src="images/unlock_jenkins.png?raw=true" alt="Logo" width="50%" height="50%" />
</p>

14. Navigate to to secrets directory by typing ```cd /var/lib/Jenkins/sercrets```

<p align="center">
 <img src="images/secret.png?raw=true" alt="Logo" width="50%" height="50%" />
</p>


15. List with `ls` command you should be able to see ```initialAdminPassword``` file 

  -  Run ```more initialAdminPassword``` to obtain your password and go back to the jenkins browser to fill in
 
<p align="center">
 <img src="images/password.png?raw=true" alt="Logo" width="50%" height="50%" />
</p>


or

  -  Run ```sudo cat /var/lib/jenkins/secrets/initialAdminPassword```

16. Install the suggested plugins and fill in your information details to set up your account

<p align="center">
 <img src="images/jenkins_interface.png?raw=true" alt="Logo" width="50%" height="50%" />
</p>


- At this point, you have completed a successful installation of Jenkins on your VM


## Contributing

Feel free to contribute to this project:

- Give a GitHub ⭐ if you like it
- Create an [Issue](https://github.com/collinskirui/DevOps/issues) to make a feature request, report a bug or share an idea.
- Create a [Pull Request](https://github.com/collinskirui/DevOps/pulls) if you want to share code or anything useful to this project.


## License

Shield: [![CC BY-NC-SA 4.0][cc-by-nc-sa-shield]][cc-by-nc-sa]

[cc-by-nc-sa]: http://creativecommons.org/licenses/by-nc-sa/4.0/
[cc-by-nc-sa-image]: https://licensebuttons.net/l/by-nc-sa/4.0/88x31.png
[cc-by-nc-sa-shield]: https://img.shields.io/badge/License-CC%20BY--NC--SA%204.0-lightgrey.svg
