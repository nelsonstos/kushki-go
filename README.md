# Kushki Go


[![license](https://img.shields.io/github/license/mashape/apistatus.svg)](https://github.com/nelsonstos/kushki-go)
[![Code Climate](https://codeclimate.com/github/culqi/culqi-go/badges/gpa.svg)](https://codeclimate.com/github/nelsonstos/kushki-go)

![](http://i.imgur.com/Djajj50.png)


Biblioteca de KUSHKI para el lenguaje Go (golang), pagos simples en tu sitio web. Consume el Kushki API.

| Versión actual| Kushki API|
|----|----|
| 0.1.0 (09-01-2017) |v2 (ir a referencia)|



## Requisitos

- Go 1.6+
- Credenciales de comercio en Kushki (1).

## Instalación


### Vía "go get"


```bash
go get github.com/nelsonstos/kushki-go
```


### Manualmente

Clonar el repositorio o descargarse el código fuente.

```bash
$ git clone git@github.com:nelsonstos/kushki-go.git
```

## Inicio rápido

Importando kushki-go:

```go
import (    
    kushki "github.com/nelsonstos/kushki-go"
)
```

Configurar credenciales.
```go
func main() {

  // 1. llaves
  kushki.Key("pk_test_xxx", "sk_test_xxx")
}
```
### Crear un *token*


```go
  // 2. Crear una instancia de token
  tk := kushki.Token{
    CardNumber:      "4111111111111111",
    Cvv:             "123",
    ExpirationMonth: "09",
    ExpirationYear:  "2020",
    Email:           "test@aj.rdrgz",
    Metadata:        map[string]string{"user_id": "777"},
  }

  // 3. Crear Token
  resp, err := tk.Create()
  if err != nil {
      panic(err)
  }
```

### Crear un *cargo* (charge)

```go
  // 2. Crear una instancia de Cargo
  c := kushki.Charge{
    Amount:       10100, // Monto del cargo. Sin punto decimal Ejemplo: 100.00 serían 10000
    Capture:      true,
    CurrencyCode: "PEN",
    Email:        "test@aj.rdrgz",
    SourceID:     "tkn_test_WIouDPBhQH9OcKE8",
    Description:  "Curso GO desde Cero",
    Metadata:     map[string]string{"user_id": "777"},
  }

  // 3. Crear Cargo
  res, err := c.Create()
  if err != nil {
      panic(err)
  }
```


### Crear un Cliente (customer)

```go
  // 2. Crear una instancia de Cliente
  c := kushki.Customer{
    FirstName:   "Alejandro",
    LastName:    "Rodriguez",
    Email:       "test@aj.rdrgz",
    Address:     "Bogotá, Colombia",
    AddressCity: "Bogotá",
    CountryCode: "CO",
    PhoneNumber: "3207777777",
    Metadata:    map[string]string{"nid": "123456789"},
  }

  // 3. Crear un Cliente
  res, err := c.Create()
  if err != nil {
      panic(err)
  }
```


### Crear una *tarjeta* (card)

```go
  // 2. Crear una instancia de Tarjeta
  c := kuhski.Card{
    CustomerID: "cus_test_XBpeiZRN49fZRofA",
    TokenID:    "tkn_test_m5YOT23kaGf8vCQy",
    Validate:   true,
    Metadata:   map[string]string{"pais": "Colombia"},
  }

  // 3. Crear una tarjeta
  res, err := c.Create()
  if err != nil {
      panic(err)
  }
```


### Crear un *plan*

```go
  // 2. Crear una instancia de un Plan
  p := kushki.Plan{
    Name:          "Suscripción Premium",
    Amount:        3000, // Monto del plan a cobrar recurrentemente. Sin punto decimal Ejemplo: 30.00 serían 3000
    CurrencyCode:  "USD",
    Interval:      "meses",
    IntervalCount: 1,
    Metadata:      map[string]string{"descripción": "Plan premium black friday"},
}

  // 3. Crear un plan
  res, err := p.Create()
  if err != nil {
      panic(err)
  }
```


### Crear una *suscripción* (suscription)  

```go
  // 2. Crear una instancia de una Suscripción
  s := culqi.Subscription{
    CardID:   "crd_test_Qe0HG7VTfmTdFvgr",
    PlanID:   "pln_test_oFvWoKSAZOAH1weu",
    Metadata: map[string]string{"user_id": "723"},
  }

  // 3. Crear una suscripción
  res, err := s.Create()
  if err != nil {
      panic(err)
  }
```


### Devolver un cargo (refund)

```
Code

```


## Tests

```bash
$ go test -v ./test/ -public_key=pk_test_xxx -secret_key=sk_test_xxx
```

---

## Documentación

¿Necesitas más información para integrar `kushki-go`? La documentación completa se encuentra en https://www.kushkipagos.com/docs/#/


## Licencia

El código fuente de `kushki-go` está distribuido bajo MIT License, revisar el archivo [LICENSE](LICENSE).


## Contribuir

TO-DO


## Changelog

Todos los cambios en las versiones de esta biblioteca están listados en [CHANGELOG](CHANGELOG).   


## Autor

Tenantz100 (**gitlab**: [@nelsonstos](https://gitlab.com/nelsonstos), **github**: [@nelsonstos](https://github.com/nelsonstos))
 
