# Checkpoint 17

<a name="readme-top"></a>

<!-- TABLE OF CONTENTS -->
<details>
  <summary>Table of Contents</summary>
  <ol>
    <li>
      <a href="#about-the-project">About The Project</a>
    </li>
    <li>
      <a href="#getting-started">Getting Started</a>
      <ul>
        <li><a href="#software-prerequisites">Software Prerequisites</a></li>
        <li><a href="#hardware-prerequisites">Hardware Prerequisites</a></li>
        <li><a href="#installation">Installation</a></li>
      </ul>
    </li>
    <li><a href="#usage-simulation">Usage Simulation</a></li>
  </ol>
</details>


## About The Project
Repository for CI/CD based on Jenkins and a tortoisebot


<!-- GETTING STARTED -->
## Getting Started

### Software Prerequisites
* ROS Noetic
* Docker

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- INSTALLATION -->
### Installation
1. Clone the repo inside ros2_ws/src/
   ```sh
   cd /home/user/ros2_ws/src && \
   git clone https://github.com/mefisto2017/checkpoint17_ros2 && \
   mv checkpoint17_ros2 ros2_ci
   ```
2. Docker instalation
   ```sh
   sudo apt-get update
   sudo apt-get install -y docker.io docker-compose
   sudo service docker start
   ```
3. Docker configuration
   ```sh
   sudo usermod -aG docker $USER
   newgrp docker
   ```
<p align="right">(<a href="#readme-top">back to top</a>)</p>


<!-- USAGE of the simulation -->
## Usage Simulation
1. Test:
```sh
cd /home/user/ros2_ws/src/ros2_ci/docker && \
docker-compose up
```

## Jenkin Test
1. Start jenkins:
```sh
bash ~/webpage_ws/start_jenkins.bash
```
2. Copy the url from :
```sh
~/jenkins__pid__url.txt
```
3. Log :
```sh
user: admin
pw: 402e4b9cc7c744f19249c186070498fa
```
4. Modify the README.MD file

5. Create a pull-request
