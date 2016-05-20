### This is Catalog application v.1.1
**Prerequisites:**
Installed:
* Python v2.7.x
* PostgreSQL 9.3.12
* Apache2
* libapache2-mod-wsgi
* python-psycopg2

**To deploy application:**

* Fork the repository into directory /var/www/CatalogApp: https://github.com/NadiiaLukianenko/catalogApp.git
* Create DB and populate data:
```sh
>>> python database_setup.py
>>> python db_populate.py
```
* Configure apache:
```sh
<VirtualHost *:80>
  DocumentRoot "/var/www/catalogApp/catalogApp/"
    WSGIDaemonProcess catalogApp user=grader group=grader threads=5
    WSGIScriptAlias / /var/www/catalogApp/catalogApp.wsgi
    <Directory /var/www/catalogApp/catalogApp/>
        WSGIProcessGroup catalogApp
        WSGIApplicationGroup %{GLOBAL}
        Order allow,deny
        Allow from all
    </Directory>
        ErrorLog ${APACHE_LOG_DIR}/error.log
</VirtualHost>
```
* Run apache:
```sh
sudo service apache2 restart
```
**API endpoints:**

***JSON:***

* */catalog.JSON* - Fetches and returns all data in json format
* */catalog/\<category_name\>.JSON* - Fetches and returns items for *\<category_name\>*

***XML:***

* */catalog.XML* - Fetches and returns all data in xml format
* */catalog/\<category_name\>.XML* - Fetches and returns items for *\<category_name\>*

**What are included:**
```
catalogApp/
/- image
/- static
    |- style.css
/- templates
    |- add_item.html
    |- catalog.html
    |- catalog_selected.html
    |- delete_item.html
    |- edit_item.html
    |- footer.html
    |- header.html
    |- item.html
    |- login.html
|- __init__.py
|- database_setup.py
|- db_populate.py
|- client_secrets.json
catalogApp.wsgi
README.md
```

**Main functionality:**
* Login/Logout
* View categories
* View/Create/Update/Delete items

**Creator:**

Nadiia Lukianenko: Nadiia.Lukianenko@gmail.com
