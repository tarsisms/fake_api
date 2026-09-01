# **Programação Móvel**

Projeto das aulas da disciplina de Programação Móvel do curso Técnico Integrado - IFAL - campus Arapiraca.

Este repositório contém a **API fake** (`db.json`) utilizada nos exemplos e exercícios em Flutter desenvolvidos durante as aulas. Para facilitar o acesso aos dados utilizados em cada aula, teremos um novo `commit` para cada alteração relevante. Assim, vocês podem navegar entre eles e acompanhar as mudanças realizadas.
</br>


## **Sobre o `db.json`**

O arquivo [`db.json`](./db.json) contém os dados fake utilizados como backend nos apps Flutter das aulas, com duas coleções principais:

- **`propriedades`**: lista de imóveis (valor, avaliação, datas, localização, tipo de host e URL da imagem), usada em exemplos de listagem estilo Airbnb.
- **`users`**: usuários fake para exemplos de autenticação (login/senha).
</br>

## **Como usar a API fake**

Este repositório está publicado no GitHub justamente para ser consumido através do [**My JSON Server**](https://my-json-server.typicode.com/), um serviço gratuito que transforma **qualquer repositório público do GitHub contendo um `db.json`** em uma API REST completa, sem precisar instalar nada ou rodar servidor local.

### Como funciona

O My JSON Server lê o `db.json` do repositório e expõe cada chave de nível superior como um endpoint REST. A URL base segue o padrão:

```
https://my-json-server.typicode.com/<usuario>/<repositorio>
```

Como este repositório é `tarsisms/fake_api`, a URL base é:

```
https://my-json-server.typicode.com/tarsisms/fake_api
```

E, como o `db.json` possui as chaves `propriedades` e `users`, os endpoints disponíveis são:

| Método | Endpoint | Descrição |
|---|---|---|
| `GET` | `/propriedades` | Lista todas as propriedades |
| `GET` | `/propriedades/1` | Retorna a propriedade com `id` 1 |
| `GET` | `/users` | Lista todos os usuários |
| `GET` | `/users/1` | Retorna o usuário com `id` 1 |

### Exemplos

A forma mais simples de testar é colar o link direto no navegador. Abaixo, cada link e o JSON que ele retorna:

**Lista todas as propriedades:**
https://my-json-server.typicode.com/tarsisms/fake_api/propriedades

```json
[
  {
    "id": 1,
    "valor": 2225.0,
    "avaliacao": 4.8,
    "datas": "10-31 Dec",
    "local": "Harlingen, Netherlands",
    "tipoDeHost": "Professional Host",
    "urlImage": "https://..."
  },
  {
    "id": 2,
    "valor": 1850.0,
    "avaliacao": 4.92,
    "datas": "20-28 Jul",
    "local": "Campos do Jordão, Brazil",
    "tipoDeHost": "Superhost",
    "urlImage": "https://..."
  },
  {
    "id": 3,
    "valor": 980.0,
    "avaliacao": 4.75,
    "datas": "05-15 Sep",
    "local": "Lisbon, Portugal",
    "tipoDeHost": "Professional Host",
    "urlImage": "https://..."
  },
  {
    "id": 4,
    "valor": 3200.0,
    "avaliacao": 4.98,
    "datas": "28 Dec - 05 Jan",
    "local": "Florianópolis, Brazil",
    "tipoDeHost": "Superhost",
    "urlImage": "https://..."
  }
]
```

**Retorna apenas a propriedade de `id` 2:**
https://my-json-server.typicode.com/tarsisms/fake_api/propriedades/2

```json
{
  "id": 2,
  "valor": 1850.0,
  "avaliacao": 4.92,
  "datas": "20-28 Jul",
  "local": "Campos do Jordão, Brazil",
  "tipoDeHost": "Superhost",
  "urlImage": "https://..."
}
```

**Lista todos os usuários:**
https://my-json-server.typicode.com/tarsisms/fake_api/users

```json
[
  {
    "id": 1,
    "username": "joao@gmail.com",
    "password": "123456"
  }
]
```

### Observações importantes

- Como o serviço é público e apenas lê o repositório, funciona igualmente em navegador, emulador Android, emulador iOS ou dispositivo físico — sem os problemas de `localhost` que existem ao rodar uma API localmente.
- Requisições `POST`, `PUT`, `PATCH` e `DELETE` **não alteram o `db.json` no GitHub** — o My JSON Server apenas simula a resposta esperada, mas os dados voltam ao estado original a cada nova consulta. Ou seja, é ótimo para praticar consumo de API, mas não persiste alterações de verdade.
- Sempre que o `db.json` deste repositório for atualizado (novo commit em `main`), a API refletirá os dados mais recentes automaticamente.
