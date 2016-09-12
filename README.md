## TdPdT.Vote

Um protocolo de referendos online criptograficamente seguro, onde um grupo de eleitores autorizados emite, secretamente, sua opinião sobre um tópico específico, chegando a um resultado que é matemáticamente infraudável, de forma independentemente verificável.

### Motivação

Em um país que faz da democracia seu pilar fundamental, torna-se necessária a existência de um sistema de eleição impecavelmente seguro. Nosso sistema atual não satisfaz essa condição, pois sua segurança depende da capacidade de nossos governantes de tornar "a urna" inviolável. Grandes empresas como o Google, a Apple, e até mesmo bancos são invadidas frequentemente. Seria, portanto, ingenuidade acreditar que nossas urnas são imunes. De fato, existem numerosas acusações do contrário:

- [Suspeitas de Fraudes em Urnas Eletrônicas](http://tiagoalbuquerque.jusbrasil.com.br/noticias/143481950/suspeitas-de-fraudes-em-urnas-eletronicas?ref=topic_feed)

- [Urna eletrônica pode ser fraudada? Especialistas explicam](http://eleicoes.uol.com.br/2014/noticias/2014/08/29/especialistas-alertam-para-possibilidade-de-fraudes-na-urna-eletronica.htm)

- [VOTO ELETRÔNICO: HACKER REVELA NO RIO COMO FRAUDOU ELEIÇÃO](http://www.pdt.org.br/index.php/voto-eletronico-hacker-revela-no-rio-como-fraudou-eleicao/)

- [Exclusivo: especialista demonstra como as eleições de 2014 podem ter sido fraudadas](http://spotniks.com/exclusivo-especialista-demonstra-como-as-eleicoes-de-2014-podem-ter-sido-fraudadas/)

Indiferente à validez dessas acusações, a lição histórica torna claro que impedir a sabotagem de sistemas eletrônicos é praticamente impossível. No modelo TdPdT.Vote, aqui proposto e baseado em recentes avanços da criptografia, esse problema é cortado pela raiz, pois toda informação envolvida é pública. Cada voto é um documento eletrônico distribuído e armazenado no computador de cada participante, de maneira similar a transações em crypto-currencies como Bitcoin. Técnicas criptográficas são aplicadas para garantir que este seja único e universalmente secreto, de tal maneira que ninguém, nem mesmo os próprios criadores do protocolo, tenham o poder de revelar seu autor. Deste modo, qualquer eleitor pode verificar a validez da eleição, bastando, para isso, realizar uma contagem independente em seu próprio computador. Invasões e fraudes são, logicamente, impossíveis, pela simples inexisência de um sistema central a ser invadido.

[Overview dos detalhes técnicos.](https://github.com/MaiaVictor/Vote/tree/master/techoverview.md)


## Organização dos módulos a serem implementados

1. [Primitivas criptográficas relevantes](https://github.com/MaiaVictor/Vote/tree/master/LRS)

2. [Servidor expondo API REST](https://github.com/MaiaVictor/Vote/tree/master/server)

3. [Client web e mobile](https://github.com/MaiaVictor/Vote/tree/master/client)
