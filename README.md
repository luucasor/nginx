# nginx

## Estrutura
```

localhost:80
    |
    |
    |                                         - - - - localhost:8001
    |                                        |
      - - localhost:8080 (reverse proxy) - - |
                                             | 
                                              - - - - localhost:8002
```

## Diretórios
  ###### /usr/local/etc/nginx: Caminho dos arquivos principais (bases) de configuração do nginx
  ###### /usr/local/etc/nginx/servers: Caminho dos arquivos de configuração dos servidores criados
  ###### /Users/lucasortigarareis/Dev/nginx: Caminho dos arquivos html e diretórios de log
  
## Conceitos
 ### Reverse Proxy: em construção
 ### API Gateway:  em construção
 
## Configuração
### server - Bloco responsável pela configuração do servidor
  ###### listen: Número da porta que o servidor deve ouvir.
  ###### server_name: Nome do servidor.
  ###### exemplo:
``` 
server {
  listen 80;
  server_name localhost;
}
```
  
### location - Bloco responsável pela configuração das rotas
  ###### root: Caminho que a requisição deve ser direcionada, deve procurar o index dentro do diretório configurado aqui.
  ###### index: Nome+Extensão do arquivo index
  ###### exemplo 1:
``` 
location / {
  root /Users/lucasortigarareis/Dev/nginx;
  index index.html
}
```
  ###### proxy_pass: Caso seja utilizado, direciona a requisição para um outro serviço.
  ###### exemplo 2:
``` 
location ~ \.php$ {
  proxy_pass http://localhost:8000  
}
```

### error_page - Parâmetro responsável pela configuração do direcionamento para casos de erro
  ###### formato: error_page [lista de códigos de erro html] /caminho_da_página_de_erro 
  ###### exemplo:
``` 
  error_page 404 400 401 /erro.html  
```
