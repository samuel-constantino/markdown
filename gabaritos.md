# Gabarito dos exercícios
A seguir encontra-se uma sugestão de solução para os exercícios propostos.

## Desafios de fixação

Para os desafios a seguir, também será utilizado o banco de dados público [sakila](https://s3.us-east-2.amazonaws.com/assets.app.betrybe.com/back-end/sakila-1ae15ae82697888c35bf1f1c8acbf755.sql).
Implemente *queries* utilizando o **INNER JOIN** para:

## INNER JOIN
**Desafio 1:** Gerar duas colunas nomeadas por “Título” e “Língua”, respectivamente, com registros sobre os títulos dos filmes e os nomes de suas línguas. 
<br/>Dica: Use as tabelas **film** e **language**.

### Solução
```
SELECT 
    fil.title AS `Título`,
    lan.name AS `Língua`
FROM
    sakila.film AS fil
        INNER JOIN
    sakila.language AS lan ON fil.film_id = lan.language_id;

```

**Desafio 2:** Gerar duas colunas nomeadas por “Título” e “Categoria”, respectivamente, com registros sobre os títulos dos filmes e os nomes de suas categorias. 
<br/>Dica: Use as tabelas **film_category**, **film** e **category**.
<br/>Dica: Use dois **INNER JOIN**.

### Solução
```
SELECT 
    fil.title AS `Título`,
    cat.name AS `Categoria`
FROM
    sakila.film_category AS fc
        INNER JOIN
    sakila.film AS fil ON fc.film_id = fil.film_id
        INNER JOIN
    sakila.category AS cat ON fc.category_id = cat.category_id;

```
**Desafio 3:** Gerar duas colunas nomeadas por "Loja_Id", e "Gerente", respectivamente, com registros sobre os *ids* das lojas, e os nomes completos dos gerentes. 
<br/>Dica: Use as tabelas **store**, e **staff**.

### Solução
```
SELECT 
    sto.store_id AS `Loja_Id`,
    CONCAT(sta.first_name, ' ', sta.last_name) AS `Gerente`,
    sta.email AS `Email`
FROM
    sakila.store AS sto
        INNER JOIN
    sakila.staff AS sta ON sto.manager_staff_id = sta.staff_id;

```

**Desafio 4:** Gerar três colunas nomeadas por "Cliente_Id", "Cliente", e "Endereço_Loja", respectivamente, com registros sobre os *ids* dos clientes, seus nomes completos e os endereços das lojas que estão cadastrados.
<br/>Dica: Use as tabelas **customer**, **store** e **address**.
<br/>Dica: Use mais de um **INNER JOIN**.

### Solução
```
SELECT 
    cus.customer_id AS `Cliente_Id`,
    CONCAT(cus.first_name, ' ', cus.last_name) AS `Cliente`,
    adr.address AS `Endereço_Loja`
FROM
    sakila.customer AS cus
        INNER JOIN
    sakila.store AS sto ON cus.store_id = sto.store_id
        INNER JOIN
    sakila.address AS adr ON sto.address_id = adr.address_id;

```

**Desafio 5:** Gerar quatro colunas nomeadas por "Alugel_Id", "Filme", "Data_Aluguel" e "Data_Retorno", respectivamente, com registros sobre os *ids* dos aluguéis, os nomes dos filmes alugados e suas datas de aluguéis e devoluções.
<br/>Dica: Use as tabelas **rental**, **inventory** e **film**.
<br/>Dica: Use mais de um **INNER JOIN**.

### Solução
```
SELECT 
    ren.rental_id AS `Aluguel_Id`,
    fil.title AS `Filme`,
    ren.rental_date AS `Aluguel_Data`,
    ren.return_date AS `Aluguel_Retorno`
FROM
    sakila.rental AS ren
        INNER JOIN
    sakila.inventory AS inv ON ren.inventory_id = inv.inventory_id
        INNER JOIN
    sakila.film AS fil ON inv.film_id = fil.film_id;

```

## SELF JOIN

**Desafio 1:** Gerar três colunas nomeadas por "Primeiro_Nome", "T1_Sobrenome" e "T2_Sobrenome", respectivamente, 
com registros sobre os primeiros nomes das pessoas atrizes e os sobrenomes que estão relacionados aos
registros da coluna "Primeiro_Nome". Certifique-se que não haverá sobrenomes com o mesmo *id*.

```
SELECT 
    t1.first_name AS `Primeiro_Nome`,
    t1.last_name AS `T1_Sobrenome`,
    t2.last_name AS `T2_Sobrenome`
FROM
    sakila.actor AS t1,
    sakila.actor AS t2
WHERE
    t1.actor_id <> t2.actor_id
        AND t1.first_name = t2.first_name;
```

## Exercícios

**Exercício 1:** Crie uma query que gere o histórico de aluguéis de filmes utilizando o INNER JOIN para retornar quatro colunas nomeadas por "Aluguel_Id", "Filme", "Cliente" e “Funcionário”. As colunas devem possuir, respectivamente, registros sobre os *ids* dos aluguéis, nomes dos filmes, nomes completos das pessoas clientes e pessoas funcionárias:
<br/>Dica: Utilize as tabelas **rental**, **inventory**, **film**, **staff**.
<br/>Dica: Utilize mais de um **JOIN**.

### Solução
```
SELECT 
    ren.rental_id AS `Aluguel_Id`,
    fil.title AS `Filme`,
    CONCAT(cus.first_name, ' ', cus.last_name) AS `Cliente`,
    CONCAT(sta.first_name, ' ', sta.last_name) AS `Funcionário`
FROM
    sakila.rental AS ren
        INNER JOIN
    sakila.inventory AS inv ON ren.inventory_id = inv.inventory_id
        INNER JOIN
    sakila.film AS fil ON inv.film_id = fil.film_id
        INNER JOIN
    sakila.customer AS cus ON ren.customer_id = cus.customer_id
        INNER JOIN
    sakila.staff AS sta ON ren.staff_id = sta.staff_id;

```

## Bônus

**Exercício 2:** Utilize o INNER JOIN para retornar o resultado de uma *query* que mostre três colunas nomeadas por "Nome_Completo", "Atriz_Id", "Cliente_Id". As colunas devem possuir, respectivamente, registros sobre o nome completo das pessoas Atrizes que possuam o mesmo nome completo dos clientes, e os *ids* das pessoas Atrizes e Clientes.
Dica: Use as tabelas **actor** e **customer**.

### Solução
```
SELECT 
    CONCAT(act.first_name, ' ', act.last_name) AS `Nome_Completo`,
    act.actor_id AS `Ator_Id`,
    cus.customer_id AS `Cliente_Id`
FROM
    sakila.actor AS act
        INNER JOIN
    sakila.customer AS cus ON CONCAT(act.first_name, ' ', act.last_name) = CONCAT(cus.first_name, ' ', cus.last_name);

```
