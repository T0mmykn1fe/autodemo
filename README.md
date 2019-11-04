# vagrant-automation-demo

This demo uses `vagrant` to run `ansible` which creates an `nginx` reverse proxy, that forwards traffic to the `python` web/app server, with a `postgres` backend.

If everything goes to plan you should see the app on `http://localhost:8080/` in your browser after you `vagrant up`.

## Example output
Example output when running `vagrant up`:

```
$ vagrant up
Bringing machine 'autodemo' up with 'virtualbox' provider...
==> autodemo: Importing base box 'hashicorp/precise64'...
...
==> autodemo: Mounting shared folders...
    autodemo: /vagrant => /Users/andrewkhoury/repos/vagrant-automation-demo
==> autodemo: Running provisioner: file...
==> autodemo: Running provisioner: file...
==> autodemo: Running provisioner: file...
==> autodemo: Running provisioner: ansible...

PLAY [Hello World] ************************************************************ 

GATHERING FACTS *************************************************************** 
ok: [autodemo]

TASK: [Installs nginx web server] ********************************************* 
changed: [autodemo]

TASK: [Move default nginx configs sites-available] **************************** 
changed: [autodemo]

TASK: [Move default nginx configs sites-enabled] ****************************** 
changed: [autodemo]

TASK: [Move our config file into place] *************************************** 
changed: [autodemo]

TASK: [Installs python and pip] *********************************************** 
changed: [autodemo] => (item=python,python-pip)

TASK: [Install tornado - python web server] *********************************** 
changed: [autodemo]

TASK: [start tornado] ********************************************************* 
changed: [autodemo]

TASK: [Install Postgresql] **************************************************** 
changed: [autodemo] => (item=postgresql,postgresql-contrib,python-psycopg2)

TASK: [Lets create a db] ****************************************************** 
changed: [autodemo]

TASK: [Create a table] ******************************************************** 
changed: [autodemo]

TASK: [I guess we should put some data in it] ********************************* 
changed: [autodemo]

TASK: [Lets see whats in the table] ******************************************* 
changed: [autodemo]

NOTIFIED: [start nginx] ******************************************************* 
changed: [autodemo]

PLAY RECAP ******************************************************************** 
autodemo               : ok=14   changed=13   unreachable=0    failed=0  
```
