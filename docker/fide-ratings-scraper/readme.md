Implementa o [xRuiAlves/fide-ratings-scraper](https://github.com/xRuiAlves/fide-ratings-scraper) e libera como uma API.

##Uso
Ao executar a imagem em um container, ele expõe a porta 80, mas muitas vezes você necessita criar o mapeamento da porta para tal
Caso necessite executar em sua máquina diretamente, utilize o seguinte comando:
`docker run -p 80:80 jppcel/fide-ratings-scraper`

Este comando pega a última versão publicada por mim no Docker Hub.