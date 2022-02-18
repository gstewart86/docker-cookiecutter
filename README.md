# docker-cookiecutter

Cookiecutter in a Docker container.

# Usage

To set it up for local development:

```
git clone https://github.com/gstewart86/docker-cookiecutter.git
cd docker-cookiecutter
docker build -t cookiecutter .
docker run --rm -it -v $PWD:/srv/app -w /srv/app cookiecutter <cookie cutter URL>
```
