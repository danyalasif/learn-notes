---
title: "YAML"
metaTitle: "YAML | DevNotes"
metaDescription: "A YAML land"
---


## YAML
- Yet Another Markup Language
- 2001
- Natural and Meaningful (Human Readable)

- DataTypes
	- Scalars, Lists, Arrays
- Data Structures
	- Indentation, dahses, colons
- Common uses
	- Config files
	- Storing data

YAML only supports spaces
Supports Unicode

Two styles:
* Block styles
Better for humans
Less Compact
```YAML
host: phl-42
datacenter:
  location: Phil
  cab: 14
roles:
  - web
  - some toher
```
* Flow styles
Compact, extension of json, folding, tags and anchors
```YAML
host: "phl-42"
datacenter: {location: Phil, cab: 14} # need to be on same line and commas between values
roles: [web,some toher]
```

## Mappings, Sequences
```yaml
host: phl-42 # space between key: value is important
datacenter:
  location: phil #2 space indentations
  cab: 13
roles: 
  - webserver
  - wp_database # sequences cannot be wihtout mapping or blank
```


## Scalars
String, number, or boolean

String: '' or "", double string allows for escape sequence
Multiline: | or >
Lots of multiline string


## Structures
You can add multiple directives/documents in one files

add `---` to the top of file when building multidocument file

e.g.
```yaml
---
host: phl2
---
host: someother
```
## Comments

```yaml
# octothorpe space and the comment to add a comment in YAML
```

## Tags
- Setting a cstom URI
- Setting local tags
- Setting a data type


```yaml
host: phl-42
datacenter:
  location: phil
  cab: !!str 13 # !!str changes the datatype to str more !!int !!float
roles: 
  - webserver
  - wp_database
```

## Anchors

Anchors allow to store and reuse data

```yaml
host: phl-42
datacenter:
  location: &PHL phil # now can referrence this anywhere with *PHL
  cab: !!str 13 # !!str changes the datatype to str more !!int !!float
roles: 
  - webserver
  - wp_database
```


Wrote a simple YAML file for ansible to install MariaDB

```yaml
---
- hosts: localhost
  remote_user: ansible
  become: yes
  become_method: sudo
  connection: ssh
  gather_facts: yes
  tasks:
    - name: Installing MariaDB
      yum:
        name: mariadb-server
        state: latest
      notify:
        - startservice
  handlers:
    - name: startservice
      service:
        name: mariadb
        state: restarted

```