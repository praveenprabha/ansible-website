# Ansible Website Project
This is an ansible website project. The task is use to ansible to create a website similar to devopsdoor.com (belonging to the trainer - Mr Basil Varghese). The website devopsdoor is a simple webpage  with static pages. Page contents are available from following github location

[devopsdoor github](https://github.com/basil1987/devopsdoor)

Here ansible is used for following tasks
  1. Installing Apache - necessary software for the website
  2. Copying and Configuring the website 

Ansible Role is used isolate variable, templates, tasks and other files.

## Directory Structure

```sh
.
├── apache
│   ├── files
│   │   └── index.html
│   ├── handlers
│   │   └── main.yaml
│   ├── tasks
│   │   └── main.yaml
│   ├── templates
│   │   └── vhosts.conf.j2
│   └── vars
│       └── main.yaml
└── devopsdoor
    ├── tasks
    │   ├── main.yaml
    │   └── setup-course-details.yaml
    ├── templates
    │   ├── contact.html.j2
    │   ├── course_details_template.html.j2
    │   ├── course_home.html.j2
    │   └── index.html.j2
    └── vars
        ├── ansible-course-var.yaml
        ├── aws-course-var.yaml
        ├── contact.yaml
        ├── course-home.yaml
        ├── devopsaws-course-var.yaml
        ├── docker-course-var.yaml
        ├── jenkins-course-var.yaml
        ├── linux-course-var.yaml
        └── main.yaml
```



## Apache Installation

