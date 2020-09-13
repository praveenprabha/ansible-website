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

Apache role has the ability to install apache2 package (for now only in Debian), configure the vhosts file in site-available and link them to site-enabled, create DocumentRoot, create VirtualHost entry and finally create a landing page to be used until the required sit is copied. In the main variable file there is an option to change the domainname to the one that you wish. Following section

```sh
site_list:
  - servername: mydevopsdoor.com
    documentroot: /var/www/html/devopsdoor
```
You can change the "servername" variable to the one of your choice. Same is the case with "documentroot"



## Configuring Website.

This includes following steps.

  1. Copying the required folders like - images, js, styles, plugins and .htaccess file. These files and folders are available under site-files folder in the github repository.  
  2. Creating template HTML files to make use of different variable files in "var" folder to create final html page at destination.

Note: index.html, contact.html and course_home.html HTML files and its template has a one-to-one relationship. However, for individual course html files like devopsaws.html, docker.html and other similar files, a single template file ( course_details_template.html.j2 ) is used along with different variable files to generate multiple course html files.


## Points to get better understanding.


DataStructure
```sh
    parent:
      - name: first child
        subtopic:
          - sub_1
          - sub_2
          - sub_3
      - name: second child
        subtopic:
          - sub_4
          - sub_5
          - sub_6
```

This means that "parent" is a list with two items in it. Each item is a dictionary with key as "name" and "subtopic". The first entry in each item, ie name, is a direct key value pair. However, the second one is a list by itself. So, how to iterate through these variables.

```sh
{% for individual_item in parent%}
Name: {{individual_item.name}}
  Following is list:-
  {% for sub_list in individual_item.subtopic %}
      {{  sub_list }}
  {% endfor%}
{% endfor %}

```
Here the first for loop (ie with individual_item) iterates through the two items in the list (which in itself is a dictionary). The second for loop is used to iterate through the list under subtopic. Getting a good understanding of this loop will help understand how variables and jinja templates are used. 




