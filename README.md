# Django REST Framework Trial

This project was created following the Django REST framework tutorial, in order to create simple pastebin code with web API.

### Prerequisites
Git

Django

virtualenv


### Installing

Majority of this project was conducted on virtualenv. Upon downloading the folders, simply start up Git Bash (or Terminal for Mac users) and input the following:
```python
virtualenv env #creates the virtual environment
source env/Scripts/activate #or 'source env/bin/activate' for mac users
pip install django
pip install djangorestframework
```
Navigate to the downloaded tutorial folder using the `cd` command:
```
cd tutorial
```
Using the `ls` command, the file `manage.py` should be inside the folder. Run the server using the following command:
```
python manage.py runserver
```
The server should now be running at http://127.0.0.1:8000/snippets/ in your browser.

## Notes
As the original tutorial followed a step-by-step format, each commit follows the tutorial headings outlined in the original documentation.

## Authors

* **Penelope Chua** - *Initial work* - [penelopechua](https://github.com/penelopechua)


## Acknowledgments

* Django REST framework tutorial - https://www.django-rest-framework.org/
