# Superglobals de PHP

## 1. Què són

Les _superglobals_ en PHP són variables predefinides que es poden accedir des de qualsevol _scope_ (àmbit) del codi, independentment d'on es trobin. PHP proporciona diverses superglobals, cadascuna amb una funcionalitat específica:

- `$GLOBALS`
- `$_SERVER`
- `$_REQUEST`
- `$_POST`
- `$_GET`
- `$_FILES`
- `$_ENV`
- `$_COOKIE`
- `$_SESSION`

### `$GLOBALS`

`$GLOBALS` és un array associatiu que conté totes les variables globals. Es pot fer servir per accedir a variables fora de l’àmbit local d’una funció.

```php
$x = 75;

function myFunction() {
    echo $GLOBALS['x'];
}

myFunction();
```

També podem utilitzar la _keyword_ `global` per accedir-hi:

```php
$x = 75;

function myFunction() {
    global $x;
    echo $x;
}

myFunction();
```

> Les variables creades fora de qualsevol funció són globals, tant si les accedim amb `$GLOBALS` com directament.

```php
$x = 100;

echo $GLOBALS["x"];
echo $x;
```

També es poden crear variables globals dins d’una funció:

```php
function myFunction() {
    $GLOBALS["x"] = 100;
}

myFunction();

echo $GLOBALS["x"];
echo $x;
```

---

### `$_SERVER`

`$_SERVER` és una superglobal que conté informació sobre headers, rutes, ubicació dels scripts i molt més.

Exemples d'ús:

```php
echo $_SERVER['PHP_SELF'];
echo $_SERVER['SERVER_NAME'];
echo $_SERVER['HTTP_HOST'];
echo $_SERVER['HTTP_REFERER'];
echo $_SERVER['HTTP_USER_AGENT'];
echo $_SERVER['SCRIPT_NAME'];
```

#### Elements més importants de `$_SERVER`

| Clau                  | Descripció                             |
| --------------------- | -------------------------------------- |
| `PHP_SELF`            | Nom del fitxer executat                |
| `GATEWAY_INTERFACE`   | Versió de CGI                          |
| `SERVER_ADDR`         | IP del servidor                        |
| `SERVER_NAME`         | Nom del servidor                       |
| `SERVER_SOFTWARE`     | Informació del servidor web            |
| `SERVER_PROTOCOL`     | Protocol utilitzat                     |
| `REQUEST_METHOD`      | Mètode de la petició (GET/POST)        |
| `REQUEST_TIME`        | Timestamp de la petició                |
| `QUERY_STRING`        | Query string de la URL                 |
| `HTTP_ACCEPT`         | Valor de la capçalera Accept           |
| `HTTP_ACCEPT_CHARSET` | Charset acceptat                       |
| `HTTP_HOST`           | Host actual                            |
| `HTTP_REFERER`        | URL referent (pot no estar disponible) |
| `HTTPS`               | Indica si s’utilitza HTTPS             |
| `REMOTE_ADDR`         | IP del client                          |
| `REMOTE_HOST`         | Host del client                        |
| `REMOTE_PORT`         | Port del client                        |
| `SCRIPT_FILENAME`     | Ruta absoluta de l’script executat     |
| `SERVER_ADMIN`        | Correu de l’administrador del servidor |
| `SERVER_PORT`         | Port utilitzat pel servidor            |
| `SERVER_SIGNATURE`    | Signatura del servidor                 |
| `PATH_TRANSLATED`     | Ruta del fitxer interpretat            |
| `SCRIPT_URI`          | URI completa de l’script               |

---

### `$_REQUEST`

`$_REQUEST` conté dades subministrades via formularis HTML, tant si són enviades amb `POST`, `GET` com mitjançant cookies. Unifica `$_GET`, `$_POST` i `$_COOKIE`.

Per accedir a la informació d’un formulari o d’una cookie:

```php
$_REQUEST['nom_del_input'];
```

#### Exemple amb formulari `POST`

```html
<form method="post" action="demo_request.php">
  Name: <input type="text" name="fname" />
  <input type="submit" />
</form>
```

Codi PHP:

```php
$name = $_REQUEST['fname'];
echo $name;
```

#### Exemple complet amb validació

```php
<form method="post" action="<?php echo $_SERVER['PHP_SELF']; ?>">
  Name: <input type="text" name="fname">
  <input type="submit">
</form>

<?php
if ($_SERVER["REQUEST_METHOD"] == "POST") {
  $name = htmlspecialchars($_REQUEST['fname']);
  if (empty($name)) {
    echo "Name is empty";
  } else {
    echo $name;
  }
}
?>
```

---

### Exemple amb `GET` via query string

```html
<a href="demo_phpfile.php?subject=PHP&web=W3schools.com">Test $GET</a>
```

Codi PHP:

```php
<?php
echo "Study " . $_REQUEST['subject'] . " at " . $_REQUEST['web'];
?>
```
