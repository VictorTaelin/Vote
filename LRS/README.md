### TODO: Linkable Ring Signatures (em PureScript)

Este módulo deve conter as seguintes primitivas criptográficas:

```haskell
-- Gera um par aleatório de chaves públicas/privadas.
gen :: RandomSeed -> (PublicKey, PrivateKey)

-- Assina uma mensagem em nome de um grupo.
sign :: [PublicKey] -> (PublicKey,PrivateKey) -> String -> Signature 

-- Verifica se determinada mensagem foi assinada em nome de um grupo.
verify :: [PublicKey] -> (String,Signature) -> Boolean

-- Verifica se uma mesma chave pública assinou duas mensagens diferentes
-- em nome de um grupo de chaves públicas.
link :: [PublicKey] -> (String,Signature) -> (String,Signature) -> Boolean
```

De modo a transcrever a primeira implementação proposta em [Linkable Ring Signatures: Security Models and New Schemes](http://link.springer.com/chapter/10.1007%2F11424826_65). (Criar um wrapper em JavaScript para acessar estas funções.)
