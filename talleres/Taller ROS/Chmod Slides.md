<!-- .slide: data-auto-animate -->
### ⚡🐍Python

Ocasionalmente, puedes necesitar que el archivo de *python* sea un *ejecutable*. Para esto se necesitan 2 condiciones:

1. Cambiar el modo del archivo a ejecutable
2. Agregar `#!/usr/bin/env python3` al principio del archivo

---

Ejemplo con archivo `hello-world.py`

```python
print("hello world")
```

```bash
$ python3 hello-world.py # outputs "hello world"
```

note: 

Mencionar que así se corren los archivos normalmente

---

Agregas la linea para que la terminal pueda saber como correr el archivo de python

```python
#!/usr/bin/env python3

print("hello world")
```

Cambias el modo con el comando `chmod`

```bash
$ chmod +x hello-world.py
```

Ahora se puede llamar así

```bash
$ ./hello-world.py # outputs "hello world"
```

note: 

Mencionar que esto sirve para que otros programas puedan usar el archivo de python
