# Gabarito dos exercícios
A seguir encontra-se uma sugestão de solução para os exercícios propostos.

## Exercícios de fixação

## INNER JOIN
**Exercício 1:** Crie uma *query* utilizando o **INNER JOIN** para retornar duas colunas nomeadas por “Título” e “Língua”, respectivamente, com registros sobre os títulos dos filmes e os nomes de suas línguas. Use as tabelas **film** e **language**.

### Solução
```
SELECT 
    fil.title AS `Título`, lan.name AS Língua
FROM
    sakila.film AS fil
        INNER JOIN
    sakila.language AS lan ON fil.film_id = lan.language_id;
```

**Exercício 2:** Crie uma *query* utilizando o **INNER JOIN** para retornar duas colunas nomeadas por “Título” e “Categoria”, respectivamente, com registros sobre os títulos dos filmes e os nomes de suas categorias. Use as tabelas **film_category**, **film** e **category**.

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

**Exercício 3:** Crie uma query que gere o histórico de aluguéis de filmes utilizando o INNER JOIN para retornar quatro colunas nomeadas por "Aluguel_Id", "Filme", "Cliente" e “Funcionário”. As colunas devem possuir, respectivamente, registros sobre os *ids* dos aluguéis, nomes dos filmes, nome completo dos clientes e funcionários. Utilize as tabelas **rental**, **inventory**, **film**, **staff**: 

### Solução
```
SELECT 
    ren.rental_id AS `Aluguel_Id`,
    fil.title AS `Filme`,
    CONCAT(cus.first_name, ' ', cus.last_name) AS `Cliente`,
    CONCAT(sta.first_name, ' ', sta.last_name) AS Funcionário
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
