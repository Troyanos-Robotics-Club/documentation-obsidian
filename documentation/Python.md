
# TLDR Python

Lenguaje de programación

# Ambientes Virtuales

Un ambiente virtual es un directorio con todas las dependecias de tu programa. Es una muy buena manera de aislar las dependecias de un proyecto a otro.

Para crear un ambiente virtual, se usa el módulo `venv` y se llama de la siguiente manera:

```sh
$ python -m venv .venv # Crea una carpeta .venv con el ambiente virtual
$ ls -a
main.py
README.md
.venv
```

En esta carpeta se encuentran todas las dependencias de tu proyecto, sin embargo, para poder usarlo, tienes que activarlo:

```sh
$ source .venv/bin/activate
```

Con esto se activa el ambiente virtual.

Para instalar dependencias, usa `pip` y `python` como normalmente lo usarías
