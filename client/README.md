### TODO: interface web (qualquer linguagem, com interop JavaScript)

Essa interface deve interagir com o servidor, e dispor das seguintes páginas:

#### 1. Seleção de referendum

Mostra a opção de gerar um novo título de eleitor, de criar um novo referendum, e de escolher um referendum para visualizar. Exemplo:

    |'''''''''''''''''''''''''|
    | Visualizar referendum:  |
    | ,____________,          |
    | |____________|          |
    | [VISUALIZAR]            |
    |                         |
    |-------------------------|
    |                         |
    | Gerar novo título:      |
    | [GERAR]                 |
    |                         |
    |-------------------------|
    | Criar referendum:       |
    |                         |
    | Descrição:              |
    | ,_____________________, |
    | |                     | |
    | |_____________________| |
    |                         |
    | Opções:                 |
    | ,_____________________, |
    | | SIM                 | |
    | | NÃO                 | |
    | | ...                 | |
    | |_____________________| |
    |                         |
    | Corpo votante:          |
    | ,_____________________, |
    | | Título 1...         | |
    | | Título 2...         | |
    | | Título 3...         | |
    | | ...                 | |
    | |_____________________| |
    |                         |
    | [CRIAR]                 |
    |_________________________|

Para visualizar um referendum, o usuário digita seu ID, e o aplicativo vai para a tela 2.

Para gerar um novo título, o usuário clica no respectivo botão. O aplicativo deve então chamar a função `gen()` (que já estará implementada, vide 1), que retornará 2 strings. O aplicativo então mostrará na tela a primeira string (chave pública) com o nome "Título de Eleitor", e a segunda string (chave privada) com o nome "Senha". De preferência, reforce o ponto de que o usuário deve manter a senha bem protegida, caso contrário alguém poderá votar por ele nos referendums ativos nos quais ele ainda não votou. Sugira ao usuário, para maior segurança, criar um novo título a cada novo referendum.

Para criar um referendum, o usuário escreve uma descrição, a lista de opções de voto, a lista de títulos com direito de votar, e aperta um botão. O aplicativo deve, então, se comunicar com o servidor, chamando o método `POST /v1/referendums`, com os respectivos parâmetros `description`, `options` e `voters` definidos. O servidor então retornará o ID do referendo criado, que deve ser mostrado para o usuário.

#### 2. Visualização de referendum

Mostra o resultado parcial do respectivo referendum, e a opção de emitir um voto. Exemplo:

    |'''''''''''''''''''''''''''''''''''''';
    | Resultado parcial:                   |
    | - Fulano 15%                         |
    | - Delcrano 25%                       |
    | - Sicrano 0%                         |
    | - Branco 10%                         |
    | - Não votou 40%                      |
    | Total: 36/60 votaram                 |
    |                                      |
    | Votar:                               |
    | - Seu Título:      |_______________| |
    | - Sua senha:       |_______________| |
    | - Opção escolhida: [Fulano |\/|]     |
    | - [VOTAR]                            |
    |______________________________________| 

Para adquirir o resultado parcial, o aplicativo deve:

1. Requisitar as informações públicas do referendo, utilizando o método `GET /v1/referendums/:referendum_id`, que retornará um JSON com o corpo de votantes (`voters`, um array de PubKeys, mostrada na interface como "Título"), as opções do referendo (`options`, um array de strings) e os votos (`votes`, um array de pares `(opção, assinatura) : (String, String)`);

2. Remover de `votes` qualquer voto `v` para o qual `verify(voters, v)` (que já estará implementada, vide 1) retorne `false` (inválido);

3. Remover de `votes` qualquer par de votos `v0, v1` para o qual `link(voters, v0, v1)` (idem) retorne `true` (duplicado);

4. Realizar uma contagem simples do número de vezes que cada opção aparece em `votes`.

Para emitir o voto, o aplicativo deve chamar a função `sign(voters, auth, option)` (idem), onde `voters` é o mesmo definido acima, `auth` é um array de 2 strings onde a primeira é a chave pública (digitada pelo usuário no campo "Título"), a segunda é a chave privada (digitada pelo usuário no campo "Senha"), e `option` é uma string tal que `option ∈ options`. O aplicativo deve, então, se comunicar com o servidor, chamando o método `/v1/referendums/${referendum_id}/${vote}`, onde `referendum_id` é a ID do referendo, e `vote` é o par `(opção, assinatura)` retornado por `sign(voters, auth, option)` e devidamente JSON-encoded.
