Tiny Personal Website
=====================
This is a small Python based personal website aimed first and foremost at being a resume.
I originally wrote this 7 or 8 years ago, and recently absolutely borked my
newer website, resulting in me quickly resurrecting this thing in about a day
and a half. This one does the same thing, but better, and faster, with less js.
Feel free to take anything you need :) But keep it open source.

<img src="./example.png" alt="screenshot of jessebot.work which serves as an example website. It features a picture of Jesse a person with blue hair that is almost 30. a blurb about them that you can read in config/config.yaml and link icons to github, gitlab, and linkedin." style="width: 40%;" align="left">

![made-with-docker](https://img.shields.io/badge/Docker-2CA5E0?style=for-the-badge&logo=docker&logoColor=white)
![made-with-python](https://img.shields.io/badge/Python-FFD43B?style=for-the-badge&logo=python&logoColor=blue)
![made-wth-flask](https://img.shields.io/badge/Flask-000000?style=for-the-badge&logo=flask&logoColor=white)
![made-with-bootstrap](https://img.shields.io/badge/Bootstrap-563D7C?style=for-the-badge&logo=bootstrap&logoColor=white)
[![GPLv3 license](https://img.shields.io/badge/License-GPLv3-blue.svg)](http://perso.crans.org/besson/LICENSE.html)

## Getting Started

Clone this github repo into your desired webroot, and install dependencies:
`pip3.10 install -r requirements.txt`

You can configure everything (e.g. website title, your photo, quote, etc)
by editing `config.yaml` and replacing all the Jesse data with your own.

All changes to HTML, CSS, and Python, or your core YAML will require a
restart of gunicorn or a rebuild of the docker container.

### Testing

For docker, you can just do:
   ```bash
   docker build . -t <name of tag you want>

   # to test locally, you can do -p 8000:8080 to forward
   # port 8080 on the container to port 8000 on your local machine
   docker run --rm -p 8000:8080 <name of the tag you used>
   ```

For testing locally with gunicorn, _without_ a docker rebuild:
   ```bash
   gunicorn app:app
   ```

Then you can go to http://127.0.0.1:8000 in a browser to view your changes.


### Deploying on an app platform

You want the following command plugged into where-ever this runs
(e.g. digital ocean app platform):

```bash
gunicorn --worker-tmp-dir /dev/shm app:app
```

And the container port of note is port 8080.
