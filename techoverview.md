O protocolo funciona em 4 etapas, todas executadas por cada eleitor de forma independente, transparente e distribuída, através de aplicativos de código aberto instalados em seus respectivos celulares e/ou computadores, sem a existencia de um servidor central com qualquer tipo de informação sigilosa.

1. Emissão de título

  Todo eleitor interessado em participar de um referendo desconecta o seu celular/computador da internet e emite, através de um algoritmo definido por antecedência incluso em seu aplicativo, um título de eleitor (público) e uma senha (privada). O eleitor anota essa informação, que é completamente apagada da memória do aparelho. Como esta senha jamais é exposta à internet, torna-se [matematicamente inviável](http://i.imgur.com/vCkuFAY.jpeg) "hackeá-la".

2. Criação de um referendo

  Para criar um referendo, todas as partes envolvidas concordam em um tópico, uma lista de opções e uma data de término. Cada eleitor interessado utiliza um canal de comunicação comum para divulgar, a todas as partes envolvidas, sua intenção de participar deste referendum. Os participantes, finalmente, entram em acordo com relação ao grupo de títulos autorizados a votar neste referendum.
  
  Exemplo: no caso de uma eleição, a lista de títulos poderia seria divulgada pelo governo. Os eleitores apenas verificariam que seu nome está nessa lista, e que ela não contém títulos associados a cidadãos inexistentes ou mortos.

3. Votação

  Cada eleitor assina, utilizando um algoritmo previamente concordado, uma mensagem declarando sua intenção de votar em determinada opção. Essa mensagem é distribuída pela rede e criptografada de tal maneira que as demais partes não tenham o poder de revelar seu autor, mas, ainda assim, possam verificar que 1. aquele que o emitiu faz parte do corpo eleitoral; 2. esse foi o único voto publicado por aquele indivíduo.

4. Contagem

  Passado um tempo após o término do referendo, cada eleitor realiza uma contagem de votos independente, utilizando um algoritmo previamente concordado. Para isso, exclui-se, da lista de votos publicados, aqueles inválidos (que não foram gerados por um título/senha válidos, ou cujo autor publicou mais de um voto), e realiza-se uma contagem simples. Cada eleitor pode, portanto, confiar que a sua contagem de votos produz o verdadeiro resultado daquele referendum.

---

Neste trabalho, [Linkable Ring Signatures](http://link.springer.com/chapter/10.1007%2F11424826_65), conforme proposto no follow-up paper de 2005, são utilizados como primitivos criptográficos a garantir os requisitos acima. Futuras melhorias deste algoritmo, e similares, podem ser utilizadas em versões posteriores.
