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

# Helpful Alias

If you plan on using this function regularly, you might consider including something like the following in your .*rc file:

```
cook() { 
    local CC_CLONE=<path to this local clone>
    if [[ -z "${1}" ]]; then
        echo "Please provide a cookiecutter url"
    elif [[ "$(docker images -q cookiecutter 2> /dev/null)" == "" ]]; then
        docker build ${CC_CLONE} -t cookiecutter
        echo "Deploying project using ${1}"
        docker run --rm -it -v $PWD:/srv/app -w /srv/app cookiecutter "${1}"
    else
        echo "Deploying project using ${1}"
        docker run --rm -it -v $PWD:/srv/app -w /srv/app cookiecutter "${1}"
    fi
}

alias cook_api="cook https://github.com/tiangolo/full-stack-fastapi-postgresql"
```