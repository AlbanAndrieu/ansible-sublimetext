## alban.andrieu.sublimetext

[![Travis CI](http://img.shields.io/travis/AlbanAndrieu/ansible-sublimetext.svg?style=flat)](http://travis-ci.org/AlbanAndrieu/ansible-sublimetext) [![Branch](http://img.shields.io/github/tag/AlbanAndrieu/ansible-sublimetext.svg?style=flat-square)](https://github.com/AlbanAndrieu/ansible-sublimetext/tree/master) [![Donate](https://img.shields.io/gratipay/AlbanAndrieu.svg?style=flat)](https://www.gratipay.com/AlbanAndrieu)  [![Ansible Galaxy](http://img.shields.io/badge/galaxy-alban.andrieu.sublimetext-blue.svg?style=flat)](https://galaxy.ansible.com/list#/roles/1776) [![Platforms](http://img.shields.io/badge/platforms-ubuntu-lightgrey.svg?style=flat)](#)

Ensures that sublimetext is properly installed and configured on `Ubuntu` using `Ansible` script.
Default settings is using sublimetext luna.
This ``Simple`` role allows you to install [sublimetext](https://www.sublimetext.org) with basic plugins. 

This playbook is be used by [Docker Hub](https://hub.docker.com) to create a [Docker](http://docker.io) image.      

Taken from
------------------

https://www.sublimetext.org/downloads/

###Requirements

Tools which might be needed by [sublimetext](https://www.sublimetext.org), like jdk, maven...
See available playbook on [GitHub](https://github.com/search?p=3&q=user%3AAlbanAndrieu+ansible%2A&type=Repositories)

### Installation

This role requires at least Ansible `v1.6.3`. 

To install it, run:

    ansible-galaxy install alban.andrieu.sublimetext



### Role variables

List of default variables available in the inventory:

```yaml
        sublimetext_enabled: yes                       # Enable module
    
    #user: 'albandri' #please override me
    user: "{{ lookup('env','USER') }}"
    sublimetext_owner: "{{ user }}"
    sublimetext_group: "{{ sublimetext_owner }}"
    #home: '~' #please override me
    home: "{{ lookup('env','HOME') }}"
    sublimetext_owner_home: "{{ home }}"
    sublimetext_base_dir: "/usr/local/sublimetext"
    sublimetext_link_base_dir: "/opt"
    sublimetext_dir_tmp: "/tmp" # or override with "{{ tempdir.stdout }} in order to have be sure to download the file"
    
    ## Most likely you dont need to edit 
    #todo sublimetext_service_enabled   : 'yes'
    sublimetext_major: "4"
    sublimetext_minor: "4"
    #kepler 3.7.2.1
    sublimetext_version: "{{sublimetext_major}}.{{sublimetext_minor}}"
    sublimetext_name: "luna"
    sublimetext_archive_extracted: "sublimetext"
    #sublimetext_archive: "sublimetext-jee-kepler-SR2-linux-gtk-x86_64.tar.gz"
    #modeling
    #sublimetext_archive: "sublimetext-modeling-{{sublimetext_name}}-R-linux-gtk-x86_64.tar.gz"
    #java
    #sublimetext_archive: "sublimetext-java-{{sublimetext_name}}-SR1-linux-gtk-x86_64.tar.gz"
    #javaee
    sublimetext_archive: "sublimetext-jee-{{sublimetext_name}}-SR1-linux-gtk-x86_64.tar.gz"
    
    #modeling
    #sublimetext_url: "https://www.sublimetext.org/downloads/download.php?file=/technology/epp/downloads/release/{{sublimetext_name}}/R/{{sublimetext_archive}}&r=1"
    #java
    #sublimetext_url: "https://www.sublimetext.org/downloads/download.php?file=/technology/epp/downloads/release/{{sublimetext_name}}/SR1/{{sublimetext_archive}}&r=1"
    #javaee
    sublimetext_url: "https://www.sublimetext.org/downloads/download.php?file=/technology/epp/downloads/release/{{sublimetext_name}}/SR1/{{sublimetext_archive}}&r=1"
    sublimetext_home_dir: "{{sublimetext_base_dir}}/{{sublimetext_name}}-{{sublimetext_version}}"
    
    sublimetext_plugins_enabled: yes                          # Enable plugins
    sublimetext_plugins_emf_enabled: no                       # Enable plugins
    sublimetext_plugins_cdt_enabled: no                       # Enable plugins
    sublimetext_plugins_cmakeed_enabled: no                   # Enable plugins
    sublimetext_plugins_openinterminal_enabled: no            # Enable plugins
    sublimetext_plugins_protobuf_enabled: no                  # Enable plugins
    sublimetext_plugins_yedit_enabled: no                     # Enable plugins
    sublimetext_plugins_shelled_enabled: no                   # Enable plugins
    sublimetext_plugins_webpageed_enabled: no                 # Enable plugins
    sublimetext_plugins_pydev_enabled: no                     # Enable plugins
    sublimetext_plugins_m2e_enabled: no                       # Enable plugins
    sublimetext_plugins_subclipse_enabled: no                 # Enable plugins
    
    sublimetext_ini_enabled: yes                              # Enable overriding sublimetext.ini
    #default is 256m
    sublimetext_launcher_XXMaxPermSize: "256m"
    #default is 256m
    sublimetext_XXMaxPermSize: "1024m"
    #default is -Xms40m
    sublimetext_Xms: "512m"
    #default is -Xmx512m
    sublimetext_Xmx: "2048m"
    
    docker_files_generated_directory: "./"
    docker_files_enable: no
    docker_volume_directory                  : "{{ sublimetext_base_dir }}"
    docker_working_directory                 : "/home/vagrant"
    docker_image_name                        : "nabla/ansible-sublimetext"
```


### Detailed usage guide

Use :

    `docker run -e "DISPLAY=`ipconfig getifaddr en0`:0.0" nabla/ansible-sublimetext`

Once [sublimetext](https://www.sublimetext.org) is installed using ansible, a [Docker](https://www.docker.com/) [image](https://registry.hub.docker.com/u/nabla/ansible-sublimetext/) is automatically created by [Docker Hub](https://registry.hub.docker.com/), 
so please do not hesitate to enhance ansible script it will then improve docker image automatically.

Run the following command :

     `ansible-playbook -i hosts -c local -v sublimetext.yml -vvvv --ask-sudo-pass | tee setup.log`


### Authors and license

`alban.andrieu.sublimetext` role was written by:
- [Alban Andrieu](fr.linkedin.com/in/nabla/) | [e-mail](mailto:alban.andrieu@free.fr) | [Twitter](https://twitter.com/AlbanAndrieu) | [GitHub](https://github.com/AlbanAndrieu)
- License: [GPLv3](https://tldrlegal.com/license/gnu-general-public-license-v3-%28gpl-3%29)

### Feedback, bug-reports, requests, ...

Are [welcome](https://github.com/AlbanAndrieu/ansible-sublimetext/issues)!

***

README generated by [Ansigenome](https://github.com/nickjj/ansigenome/).
