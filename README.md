# Django REST Framework Trial

This project was created following the Django REST framework tutorial, in order to create simple pastebin code with web API.

## Prerequisites
Git

Django

virtualenv


## Installing

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
As the original tutorial followed a step-by-step format, each commit follows the tutorial headings outlined in the original documentation. This repository only reaches Part 6 of the Django REST framework tutorial.

## Test Examples
The following details example HTTP calls that can be run:

Firstly, ensure your device has httpie installed by running the following command in Command Prompt:
```
pip install httpie
```
httpie is a cURL-like HTTP client with easy-to-read syntax. We will be using it for the purposes of this example.
### HTTP GET
This command returns you the snippet list in the command line. Modifying the url (e.g. /snippets/2/) will allow you to gain information at the specified url. Furthermore, changing the extension (.api, .json etc.) allows you to control the format in which you receive the requested information.
```python
http 127.0.0.1:8000/snippets.json #return in json
http 127.0.0.1:8000/snippets.api #return in browsable api
```

### HTTP OPTION
This command returns you communication options in the url.
```python
http OPTIONS 127.0.0.1:8000
```

### HTTP POST and DELETE
Now, we will be doing a simple POST and DELETE from the snippets list. Due to authorization needed, only users can post, and only owners of posts can delete them. This will be demonstrated below:

Firstly, input the following code to post "hello world" into the code field of the snippet. We will be logging in as user Penelope.
```python
http -a Penelope:testpassword POST 127.0.0.1:8000/snippet/ code="hello world"
```
Secondly, we can input another snippet using user penny.
```python
http -a penny:testpassword POST 127.0.0.1:8000/snippet/ code="hello earth"
```
Now, let's test the delete functions. Using user penny, we are unable to delete what user Penelope has posted. However, we should be able to delete our own snippets.
```python
http -a penny:testpassword DELETE 127.0.0.1:8000/snippet/1/ #this should return an authorisation error
http -a penny:testpassword DELETE 127.0.0.1:8000/snippet/2/ #this should return an authorisation error
```

### HTTP PUT and PATCH
The PUT command refers to full update of a resource. We can test this on a snippet.
```python
http -a Penelope:testpassword PUT 127.0.0.1:8000/snippet/1/ code="success!!"
```
Upon refreshing the page, the snippet's code field should be updated.

Similarly, the PATCH command updates the resource, but only partially.
```python
http -a Penelope:testpassword PATCH 127.0.0.1:8000/snippet/1/ code="success again!!"
```
Like before, only owners of the posts can update its contents.

## Authors

* **Penelope Chua** - *Initial work* - [penelopechua](https://github.com/penelopechua)


## Acknowledgments

* Django REST framework tutorial - https://www.django-rest-framework.org/
