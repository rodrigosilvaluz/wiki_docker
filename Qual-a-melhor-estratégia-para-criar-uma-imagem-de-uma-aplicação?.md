Crie imagens base para solucionar o problema de tempo de build da imagem. Faça tudo o que puder na imagem base, para que sua imagem final (a que você irá adicionar sua aplicação) tenha o tempo de build menor possível.

1. Parta de uma imagem que te atenda minimamente. 
2. Crie uma imagem intermediária com todas as modificações, tudo o que você faria para a aplicação rodar exceto colocar a aplicação.
3) Sua imagem final deve somente adicionar a aplicação em questão. Assim o build tende a ser o menor possível.