# Burox

This is a wrapper to connect to Buró de Credito 

**What is Buró de Crédito**

[Buró de Crédito](https://www.burodecredito.com.mx/) is a mexican company that is dedicated to integrate and provide information, prior to the granting of a loan. 

Whose main objective is to record the credit history of people and companies that have obtained some type of credit, financing, loan or service

## Installation

If [available in Hex](https://hex.pm/docs/publish), the package can be installed
by adding `burox` to your list of dependencies in `mix.exs`:

```elixir
def deps do
  [
    {:burox, "~> 0.6.0"}
  ]
end
```

## Usage

### Configuration 

Add your keys in your `config.exs` file:

```elixir

config :burox,
  buro_url: "BURO_HOST",
  buro_user: "YPUR-BURO-USER",
  buro_password: "YOUR-BURO-PASSWORD",
  buro_service: Burox.BuroService.Socket

```

If you need to use `prospector`, add these:

```elixir
  buro_url_prospector: "PROSPECTOR-HOST",
  buro_user_prospector: "YOUR-PROSPECTOR-USER",
  buro_password_prospector: "YOUR-PROSPECTOR-PASSWORD"
```

### Request

You need to add your parameter to an structure Burox.Request
It supports Authentication also.

```elixir

%Burox.Request{
    autenticacion: %{
      cuenta_con_tarjeta_de_credito: "V",
      ultimos_cuatro_digitos: "4761",
      ha_ejercido_un_credito_hipotecario: "F",
      ha_ejercido_un_credito_automotriz_en_los_ultimos_24_meses: "F"
    },
    persona: %{
      apellido_paterno: "CABRERA",
      apellido_materno: "RODRIGUEZ",
      primer_nombre: "ADRIANA",
      rfc: "CARA8105144V1"
    },
    direccion: %{
      primera_linea_de_direccion: "CUMBRES MZ 15 28",
      colonia: "PRADERAS DE  SAN MATEO",
      municipio: "NAUCALPAN",
      ciudad: "NAUCALPAN DE Juarez",
      estado: "EM",
      codigo_postal: "53228",
      origen_del_domicilio: "MX"
    }
  }

```

Post your request to Buró. 

THhe second parameter is the code of the product you want, i.e

```elixir
Burox.solicitar(request, "507") 
```

## License 

The MIT License (MIT)

Copyright (c) 2018 [Resuelve](https://github.com/resuelve)
