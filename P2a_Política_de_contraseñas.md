# Política de contraseñas

## Contexto
Por defecto, la mayoría de sistemas operativos, vienene con una política de contraseña muy laxa, una contraseña segura presenta una barrera más al atacante, que en su intento de acceder al sistema, indudablemete dejará más rastro y en algunos casos a provocar el abandondo de ataque.

## Objetivos
* Entender el sistema de contraseñas del sistema operativo linux
* Entender el PAM (Plugable authentication Module)
* Instalar y configurar la libreria _pwquality_
* Comprobar y verificar que se ha llevado la práctica de forma correcta
* Documentar la práctica.

## Política contraseñas débiles

 1. Restricciones
 
 ```bash
 # /etc/security/pwquality.conf

minlen = 6   # Longitud mínima de 6 caracteres
dcredit = 0  # No se requiere ningún número
ucredit = 0  # No se requiere ninguna letra mayúscula
lcredit = 0  # No se requiere ninguna letra minúscula
ocredit = 0  # No se requieren caracteres especiales

```

2. Ejemplo contraseña:

Tiene mínimo de 6 caracteres, No incluye letras mayúsculas ni minúsculas, No tiene caracteres especiales ni una mezcla de diferentes tipos de caracteres.

```bash
passwd 123456
```

3. resultado pwscore:

```bash
0
```

4. Ejemplo contraseña 2:

```bash
passwd abcd1234
```

5. resultado pwscore:

```bash
26
```

## Política contraseñas Media

 1. Restricciones
 
 ```bash
# /etc/security/pwquality.conf

minlen = 8  # Longitud mínima de 8 caracteres
dcredit = -1 # Requiere al menos 1 número
ucredit = -1 # Requiere al menos 1 letra mayúscula
lcredit = -1 # Requiere al menos 1 letra minúscula
ocredit = 0  # No se requiere ningún carácter especial

```

2. Ejemplo de contraseña:

Mínimo 8 caracteres, Tiene una letra mayúscula al inicio y el resto son minúsculas, Incluye al menos un número.

```bash
passwd A1b2C3d4E5
```

3. resultado pwscore:

```bash
69
```

4. Ejemplo de contraseña 2:


```bash
passwd Morning123
```

5. resultado pwscore:

```bash
78
```



## Política contraseñas Extrema


 1. Restricciones
 
 ```bash
# /etc/security/pwquality.conf

minlen = 12   # Longitud mínima de 12 caracteres
dcredit = -1  # Requiere al menos 1 número
ucredit = -1  # Requiere al menos 1 letra mayúscula
lcredit = -1  # Requiere al menos 1 letra minúscula
ocredit = -1  # Requiere al menos 1 carácter especial
maxrepeat = 3 # Máximo de 3 caracteres repetidos consecutivamente
maxclassrepeat = 3 # Máximo de 3 repeticiones de la misma clase de caracteres

```

2. Ejemplo de contraseña:

```bash
7XyZ12#qW@9kL8
```

3. resultado pwscore:

```bash
100
```

4. Ejemplo de contraseña 2:


```bash
passwd R2b!nE4&kT7m
```

5. resultado pwscore:

```bash
100
```















