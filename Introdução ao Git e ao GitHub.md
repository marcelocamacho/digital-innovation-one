# Introdução ao GIT e ao GITHUB

## Entnendo como o Git funciona

###  Encriptação SHA1 gera um conjunto de caracteres identificador de 40 dígitos.

```
echo "ola mundo" | openssl sha1
> (stdin)= d9802fa01c4c1dfc4ddaf61f766d8d56ad8a8699

```

### Objetos internos do Git

Objetos do git são estruturas de dados que são criptografadas juntamente com metadados e podem ser divididos assim:

1. Blobs
São estruturas de dados mais simples.
```
echo 'conteudo' | git hash-object --stdin
> fc31e91b26cf85a55e072476de7f263c89260eb1

echo -e 'conteudo' | openssl sha1
> 65b0d0dda479cc03cce59528e28961e498155f5c

echo -e 'blob 9\0conteudo' |openssl --stdin
> fc31e91b26cf85a55e072476de7f263c89260eb1
```

2. Trees
São estruturas de dados que podem apontar para outros objetos (blobs, trees, commits), 
``` 
Tree
\0
blob sa4d8 texto.txt
``` 
3. Commits

É o objeto que consolida tudo.

```Commit
tree s4a5sq1
parent a98acq1
autor marcelocamacho
mensagem "inicia ...."
timestamp 
``
### SSH e Tokens

```
#gerar a chave pública e privada
$ ssh-keygen -t ed25519 -c marcelocamacho.ufpa@gmail.com


#Expor a chave pública lá no gitHub
Navegar até Settings > SSH e and GPG Keys > New SSH Key

# Iniciar o agent ssh
$ eval $(ssh-agent -s)

#Informar a chave para o agente
$ ssh-add /home/marceloc/.ssh/id_es25519

``` 