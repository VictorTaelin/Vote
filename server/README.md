### TODO: servidor expondo API REST (qualquer linguagem)

---

#### 1. Criar referendo

Cria um novo referendo com um corpo votante. Retorna a ID do referendo criado.

    POST /v1/pools 

##### Parâmetros

    Nome | Tipo | Descrição
    --- | --- | --- 
    description | Strings | Descrição/proposta do referendo
    voters | Array de Strings | Chaves públicas de cada votante válido.
    options | Array de Strings | Opções do referendo.

##### Exemplo

    Requisição: 
      /v1/referendums
        ?description="Quem deve ser o diretor?"
        &voters=["F01A50","DE1C5A90","51C5A90"]
        &options=["sim","não"]
        (devidamente codificado)
    Retorno: 0

---

#### 2. Visualizar referendo

Solicita toda a informação pública associada a um referendo. Retorna um objeto JSON-codificado.

    GET /v1/referendums/:referendum_id

##### Exemplo

    Requisição: example.com/v1/referendums/0

    Retorno: 
      {"description": "Quem deve ser o diretor?",
        "voters": ["F01A50","DE1C5A90","51C5A90"],
        "options": ["sim", "não"],
        "votes": [["opcao0","assinatura0"]", ["opcao1","assinatura1"]]}

---

#### 3. Votar

Adiciona voto a um referendo. Um voto é apenas uma string contendo informações criptográficas. O servidor não fará nenhuma validação do voto além de testar se a opção escolhida é válida. Ele irá, portanto, apenas armazená-lo e retorná-lo a qualquer um que as solicite, exercendo papel exclusivo de repositório de informações. Cada cliente é responsável pela validação e contagem dos votos.

    POST /v1/referendums/:referendum_id/vote

##### Parâmetros

Nome | Tipo | Descrição
--- | --- | ---
vote | String | String contendo informação referente ao voto


##### Exemplo

    Requisição: example.com/v1/referendums/vote&vote="rzuYw0PzkR420RBgJqZ3cjIGt"

    Retorno: -
