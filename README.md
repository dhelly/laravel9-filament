# Controle de Estudo 
## Usando Laravel e Filament 

[Laravel 9](https://laravel.com/)
[Filament](https://filamentphp.com/)

Estou usando o Sail. Por isso os comandos estarão com sail a frente.

Esse projeto será baseado na vídeo [**Destrinchando Filament com Leandro Ferreira| Petiscando #120**](https://www.youtube.com/watch?v=-bnMf-sSbrg)

## Procedimentos

- Instalando o Filament
  ```
  sail composer require filament/filament:"^2.0" 
  ```
- Inserir a linha abaixo no  *composer.json* - **"post-update-cmd"**
  ```
  "@php artisan filament:upgrade"
  ```
- Publicação das configurações
  ```
  sail artisan vendor:publish --tag=filament-config
  ```

Podemos acessar o `/admin`

    Configuração para a tabela user

    1. Atualizar a migration user
    2. Atualizar o Model user - fillabled
    3. Atualizar a Factory
    4. Configurar o DatabaseSeeder

- Rodar a migration
  ```
  sail artisan migrate --seed
  ```

### Criando os Resources
Para o Filament, Resource são usados para criar os CRUD

- Antes de criar os resources, vamos instalar o pacote que cria automaticamente os formulários e tabelas.
  ```
  sail composer require doctrine/dbal --dev
  ```

É possível criar as views do recursos(resources) em uma página só e em uma página para cada recurso.
- Flag `--simple`: Criar apenas uma página, e os recursos usando modal
- Sem flag: Criar uma página para cada recurso

Como escolher? Se houver poucos campos é uma ótima opção usar o simple

- Criando o resource para o Model user
```
sail artisan make:filament-resource User --generate --simple
```
O arquivo `UserResource.php` na pasta `app/Filament/Resource`. Nesse arquivo temos dois métodos: o `form` e o `table`.

