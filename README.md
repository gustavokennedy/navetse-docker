# Navetse com Docker
Repositório para deploy do ambiente Navetse com Docker.

### Requisitos

  - Docker e Docker-Compose

### Aplicações

	mysql:3306
	phpmyadmin:9090
	webserver:80
	frontend:3000
	app:9000

## Instalação ⚙️

A estrutura das pastas deve ser:

```shell
   - api-navetse/
   - navetse/
   - docker-compose.yml
```

Lembre-se de alterar as branchs dos repositórios (navetse e api-navetse) para 'dev'.

Depois com as pastas organizadas e com os arquivos .env feitos, execute:

```shell
docker-compose up
```

## Possíveis erros ❌

#### Aplicação Frontend não logar:

```shell
docker exec -it app bash
php artisan key:generate
```

#### Erro 400 em reports

Falta do usuário 'fsconsultoria' no mySQL:

```shell
docker exec -it db bash
mysql-uroot -proot
CREATE USER 'fsconsultoria'@'%' IDENTIFIED BY 'sua_senha';
GRANT ALL PRIVILEGES ON navetse.* TO 'fsconsultoria'@'%';
FLUSH PRIVILEGES;
```

Tabela 'navetse.vw_homepage' não existe:

