# Geral

## Estrutura dos servidores: Em construção
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

## Estrutura dos arquivos de configuração: Em construção
```

localhost:80 (reverse proxy)
    |
    |
    |                                         - - - - localhost:8001
    |                                        |
      - - localhost:8000 (load balancer) - - |
                                             | 
                                              - - - - localhost:8002
```
<br>

## Comandos nginx
  ###### Valida a sintaxe dos arquivos de configuração
``` nginx
    nginx -t
```
  ###### Recarrega os arquivos de configuração
``` nginx
    nginx -s reload
```
  ###### Chama o help do nginx, apresentando alguns dados versão | caminho de instalação | caminho dos arquivos de configuração e etc
``` nginx
    nginx -h
```
<br>

## Diretórios
  - **/usr/local/etc/nginx**: Caminho dos arquivos principais (bases) de configuração do nginx
  - **/usr/local/etc/nginx/servers**: Caminho dos arquivos de configuração dos servidores criados
  - **/Users/lucasortigarareis/Dev/nginx**: Caminho dos arquivos html e diretórios de log
<br>

## Conceitos
 ### Reverse Proxy: em construção
 ### API Gateway: em construção
 ### Load Balancer: em construção
<br>
 
## Configuração
### server - Bloco responsável pela configuração do servidor
  - **listen**: Número da porta que o servidor deve ouvir.
  - **server_name**: Nome do servidor.

exemplo:
``` 
server {
  listen 80;
  server_name localhost;
}
```
  
### location - Bloco responsável pela configuração das rotas
  - **root**: Caminho que a requisição deve ser direcionada, deve procurar o index dentro do diretório configurado aqui.
  - **index**: Nome+Extensão do arquivo index

exemplo 1:
``` 
location / {
  root /Users/lucasortigarareis/Dev/nginx;
  index index.html
}
```
  - **proxy_pass**: Caso seja utilizado, direciona a requisição para um outro serviço.
  - **proxy_set_header**: Parâmetro usado para inserir informações no header da requisição.

exemplo 2:
``` 
location ~ \.php$ {
  proxy_pass http://localhost:8000  
  proxy_set_header X-Real-IP $remote_addr;
}
```

### error_page - Parâmetro responsável pela configuração do direcionamento para casos de erro
  - **formato**: error_page [lista de códigos de erro html] /caminho_da_página_de_erro 

exemplo:
``` 
  error_page 404 400 401 /erro.html  
```

### upstream - Parâmetro responsável pela configuração do load balancer
  - **formato**: em construção

exemplo:
``` 
  em construção
```

