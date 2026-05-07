# bbs

* make a 4chan-like or pttweb-like board with Django
* bbs: Bulletin Board System

## To-do-list

* Migration from MySQL to PostgreSQL
* init for 1st time bootstrap image_board
* app post:
    * How to render images/video Thumbnail?
    * edit views/PostDetail to make query for two models(Post/Comment) or even combine them into one to render template post_detail.html
        * [ForeignKey.related_name](https://docs.djangoproject.com/en/4.2/ref/models/fields/#django.db.models.ForeignKey.related_name)
            * edit/checkt post_detail.html
            * To display the comments associated with the post, you can use the related_name attribute in the ForeignKey field of the Comment model. Here’s an example:
            * post is the Post object that we want to display comments for, and comments is the related_name that we defined in the ForeignKey field of the Comment model.
* app accounts:
    * custom login/logged out page
    * user permission relations

## Prerequisites

* Linux host such as Arch Linux, Debian, Ubuntu, RHEL ...etc
* PostgreSQL
* uv
    * An extremely fast Python package and project manager, written in Rust.
    * [docs.astral.sh/uv/](https://docs.astral.sh/uv/)
* setup python django project with uv
    * run scripts/setup_with_uv.sh
* tree
    * a CLI tools to list contents of directories in a tree-like format.
* docker/podman (just pickup one to do conatiner image building and running)

## Quick Start

* setup PostgreSQL with Podman/Docker compose in postgresql/


* Setup bbs with uv

```shell
# database migrate
uv run  main/manage.py migrate

# create admin
uv run main/manage.py createsuperuser

#run django with uv
uv run  main/manage.py runserver 18080


# open URL with browser or test with cli tools: curl/wget/k6/...etc
# main
http://127.0.0.1:18080

# cms
http://127.0.0.1:18080/admin/login/?next=/admin/

#for help
python3 manage.py help

#Creating a superuser for Django CMS system
python3 manage.py createsuperuser

#run devserver
python manage.py runserver 18080


#check gunicorn
gunicorn --version
#run with gunicorn
#some test codes in misc
gunicorn --workers=2 test_gunicorn01:app
#run with django project
#src: https://docs.djangoproject.com/en/4.2/howto/deployment/wsgi/gunicorn/
gunicorn locallibrary.wsgi


#Warning: You'll need to run these commands every time your models change in a way that will affect the structure of the data that needs to be stored (including both addition and removal of whole models and individual fields).
python3 manage.py makemigrations
python3 manage.py migrate

python3 manage.py sqlmigrate posts 0001

#run test
python3 manage.py test
#Showing more test information
python3 manage.py test --verbosity 2
#Speeding things up
python3 manage.py test --parallel auto
#Running specific tests
python3 manage.py test catalog.tests.test_models
python3 manage.py test catalog.tests.test_views
python3 manage.py test catalog.tests.test_forms

#deploy check
python3 manage.py check --deploy

#Starts the Python interactive interpreter
python3 manage.py shell

#src: https://docs.python.org/3.8/library/sys.html#sys.path
#A list of strings that specifies the search path for modules. 
#Initialized from the environment variable PYTHONPATH, plus an installation-dependent default.
python -c "import sys; print(sys.path)"

#add env PYTHONPATH
export PYTHONPATH=/path/to/your/module:$PYTHONPATH

#add packages by poetry
poetry add "psycopg[binary,pool]"
poetry add django-environ

#add packages by poetry to extras section
poetry add diagrams --optional --extras diagrams

#export requirements.txt if needed
poetry export -f requirements.txt --output requirements.txt
poetry export -f requirements.txt --output requirements.txt --without-hashes
```

## uv

* tips

```shell
uv self update

uv python list

uv python install 3.13.13

uv add psycopg[binary]
```

## python3

* [Python 3.13.13 Release date: April 7, 2026](https://www.python.org/downloads/release/python-31313/)

## Test

* [django / pass multiple models to my ListView](https://stackoverflow.com/questions/67223248/django-pass-multiple-models-to-my-listview)
* table join
* [Changing to a custom user model mid-project](https://docs.djangoproject.com/en/4.2/topics/auth/customizing/#changing-to-a-custom-user-model-mid-project)
* [Writing your first Django app, part 2](https://docs.djangoproject.com/en/4.2/intro/tutorial02/)
* [Playing with the API](https://docs.djangoproject.com/en/4.2/intro/tutorial02/#playing-with-the-api)
* [get_user_model()](https://docs.djangoproject.com/en/4.2/topics/auth/customizing/#django.contrib.auth.get_user_model)
* [[Day24] - Django-REST-Framework User Management](https://ithelp.ithome.com.tw/articles/10278976)
* [django.contrib.auth](https://docs.djangoproject.com/en/4.2/ref/contrib/auth/)
* [Django_BBS](https://github.com/devbruce/Django_BBS)

```shell
$ python manage.py shell
>>> from django.contrib.auth import get_user_model
>>> from myapp.models import BlogPost
>>> user = get_user_model().objects.create_user(username='testuser', password='12345')
>>> post = BlogPost.objects.create(author=user, date='2023-11-16', title='Test Post', post='This is a test post.')
>>> post.author.username
'testuser'
```

## reference implementation
* [github.com/blackdesert575/pttweb](https://github.com/blackdesert575/pttweb)
* [github.com/pinry/pinry](https://github.com/pinry/pinry)
* [pypi.org/project/Boorunaut](https://pypi.org/project/Boorunaut/)
* [forked from gnstaxo/imageboard](https://github.com/blackdesert575/imageboard)
* [szurubooru](https://github.com/rr-/szurubooru)
    * Image board engine, Danbooru-style.
* [A Complete Beginner's Guide to Django - Part 1](https://simpleisbetterthancomplex.com/series/2017/09/04/a-complete-beginners-guide-to-django-part-1.html)
* [jenkins](https://www.jenkins.io/)
  * init 1st setup guide pages (Post-installation setup wizard)?
    * [github.com/jenkinsci/jenkins/tree/master/core/src/main/resources/jenkins/install](https://github.com/jenkinsci/jenkins/tree/master/core/src/main/resources/jenkins/install)
    * [github.com/jenkinsci/jenkins/tree/master/core/src/main/resources/jenkins/install/SetupWizard](https://github.com/jenkinsci/jenkins/tree/master/core/src/main/resources/jenkins/install/SetupWizard)

## Misc

* Upgrade Django to a new version
  * [docs.djangoproject.com/en/6.0/howto/upgrade-version/](https://docs.djangoproject.com/en/6.0/howto/upgrade-version/)
* Django supported-versions
  * [www.djangoproject.com/download/#supported-versions](https://www.djangoproject.com/download/#supported-versions)
* [stackoverflow.com/questions/79118841/how-to-migrate-from-poetry-to-uv-package-manager](https://stackoverflow.com/questions/79118841/how-to-migrate-from-poetry-to-uv-package-manager)
* [chatgpt-line-bot](https://github.com/Lin-jun-xiang/chatgpt-line-bot)
* [gpt4free](https://github.com/xtekky/gpt4free)
