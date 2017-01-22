Crie imagens base para solucionar o problema de tempo de build da imagem. Faça tudo o que puder na imagem base, para que sua imagem final (a que você irá adicionar sua aplicação) tenha o tempo de build menor possível.

1. Parta de uma imagem que te atenda minimamente. 
2. Crie uma imagem intermediária com todas as modificações, tudo o que você faria para a aplicação rodar exceto colocar a aplicação.
3. Sua imagem final deve somente adicionar a aplicação em questão. Assim o build tende a ser o menor possível.

Exemplo:

## NodeJS
1. Use uma imagem do node (escolha a que melhor te atenda) https://hub.docker.com/_/node/
1. Faça pull da imagem (exemplo _node:7.4.0_)
1. Crie um dockerfile que com base na imagem **node:7.4.0** e instale todas as dependências, como bibliotecas do SO e  instale as dependências exclusivas da sua aplicação, como libs NPM, BOWER, etc. Faça o build dessa imagem gerando a imagem **APP-XPTO-PREREQS**.
1. Crie um dockerfile que com base na imagem **APP-XPTO-PREREQS** e copie sua aplicação. Faça o build dessa imagem gerando a imagem **APP-XPTO**.

Teoricamente o passo 3 será executado numa proporção muito menor do que o passo 4, assim você ganha muito tempo de build.