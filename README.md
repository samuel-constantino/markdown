# SUMÁRIO

- [O que vamos aprender?](#o-que-vamos-aprender)

  - [Você será capaz de:](#você-será-capaz-de)
 
- [Por que isso é importante?](#por-que-isso-é-importante)

- [Conteúdos](#conteúdos)

  - [O que é um JOIN?](#o-que-é-um-join)
  - [INNER JOIN](#inner-join)
  - [LEFT JOIN e RIGHT JOIN](#left-join-e-right-join)
  - [SELF JOIN](#self-join)

- [Vamos Praticar](#vamos-praticar)

- [Exercícios](#exercícios)
  
  - [Agora a prática](#agora-a-prática)
  - [Bônus](#bônus)
  
- [Recursos adicionais (opcional)](#recursos-adicionais-opcional)

# O que vamos aprender?

Hey Tryber! Hoje você continuará aprofundando seu conhecimento 
no incrível mundo do SQL ao aprender como juntar dados de tabelas 
relacionadas por meio dos diferentes tipos de **JOIN** para tornar suas *queries* mais completas e poderosas.

## Você será capaz de

- Utilizar **INNER JOIN** para selecionar registros comuns 
entre tabelas; 

- Utilizar **LEFT JOIN** para selecionar todos registros de uma
tabela (esquerda) e os registros correspondentes de outra 
tabela (direita);

- Utilizar **RIGHT JOIN** para selecionar todos registros de uma
tabela (direita) e os registros correspondentes de outra 
tabela (esquerda);

- Utilizar **FULL JOIN** para selecionar todos os registros 
quando há correspondência entre as tabelas (esquerda e direita)

- Utilizar **SELF JOIN** para juntar uma tabela com 
ela própria (auto-junção)


# Por que isso é importante?

Em algum momento na sua carreira como desenvolvedor de software, é provável que você precise relacionar dados de diferentes tabelas em um banco de dados relacional  para gerar informações mais detalhadas e completas. Sendo assim, entender as diferenças e em qual contexto utilizar cada tipo de **JOIN** é importante para seu sucesso profissional.


# Conteúdos

## O que é um JOIN?

Até agora, você aprendeu a manipular uma tabela para diversos fins, executando operações simples de inserção, seleção, alteração e exclusão ([CRUD](https://developer.mozilla.org/pt-BR/docs/Glossary/CRUD)), até operações mais específicas como selecionar, classificar e/ou agrupar os dados para melhorar a visualização em seus relatórios. Porém, há situações em que uma única tabela não possui todos os dados necessários para gerar as informações que você precisa. É nesse momento em que o conceito de **JOIN** entra em jogo.

O **JOIN** é um recurso do SQL para **combinar** os registros de duas ou mais tabelas em uma única consulta, com base em uma coluna relacionada entre elas.

A partir de agora você será capaz de **juntar** os dados de duas ou mais tabelas por meio do **JOIN** e aplicar todo conhecimento adquirido anteriormente para gerar relatórios mais completos e detalhados. Essa **junção** pode ser feita de várias formas, veremos mais sobre os tipos de **JOIN** ainda hoje!

![Dragon JOIN Ball](https://c.tenor.com/1wJU51jgwSQAAAAC/dbz-dragonball.gif)

## INNER JOIN

O INNER JOIN seleciona os dados correspondentes entre duas ou 
mais tabelas conectadas por uma coluna em comum. Confira sua sintaxe básica:
```
SELECT 
    t1.coluna, t2.coluna
FROM
    tabela1 AS t1
        INNER JOIN
    tabela2 AS t2 ON t1.coluna_em_comum = t2.coluna_em_comum;

```

Note que na sintaxe acima é usado o *alias* (**AS**) para nomear temporariamente as tabelas. O alias não é necessário para o sucesso da *query*, mas usá-lo é uma
boa prática, pois torna o nome das colunas mais legíveis e facilita usá-las em outras partes do código. Clique [nesse link](https://www.w3schools.com/sql/sql_alias.asp) para saber mais sobre *alias*.

É possível representar o efeito do INNER JOIN por meio da [teoría dos conjuntos](https://www.todamateria.com.br/teoria-dos-conjuntos/) da seguinte forma:

![imagem-inner-join](https://www.w3schools.com/sql/img_innerjoin.gif)

### Exemplos

Para os exemplos a seguir, será utilizado o banco de dados público [sakila](https://s3.us-east-2.amazonaws.com/assets.app.betrybe.com/back-end/sakila-1ae15ae82697888c35bf1f1c8acbf755.sql).

#### 1. Utilize INNER JOIN para gerar duas colunas. As colunas devem buscar, respectivamente: O nome das cidades (**city**) e o país referente a cada cidade (**country**).

```
SELECT 
    cit.city, cou.country
FROM
    sakila.city AS cit
        INNER JOIN
    sakila.country AS cou ON cit.country_id = cou.country_id;

```
Também é possível utilizar o INNER JOIN mais de uma vez na mesma **query**, segue o exemplo:

#### 2. Utilize INNER JOIN para gerar três colunas. As colunas devem buscar, respectivamente: O nome completo dos clientes (**customer**), o endereço referente a cada cliente e o país referente a cada endereço encontrado. Os nomes das colunas devem ser, respectivamente: "Nome_Completo", "Endereço", "Cidade"

```
SELECT 
    CONCAT(cus.first_name, ' ', cus.last_name) AS `Nome_Completo`,
    adr.address AS `Endereço`,
    cit.city AS `Cidade`
FROM
    sakila.customer AS cus
        INNER JOIN
    sakila.address AS adr ON cus.address_id = adr.address_id
        INNER JOIN
    sakila.city AS cit ON adr.city_id = cit.city_id;

```
### Desafios

Para os desafios a seguir, também será utilizado o banco de dados público [sakila](https://s3.us-east-2.amazonaws.com/assets.app.betrybe.com/back-end/sakila-1ae15ae82697888c35bf1f1c8acbf755.sql).

1. Crie uma *query* utilizando o **INNER JOIN** para retornar duas colunas nomeadas por “Título” e “Língua”, respectivamente, com registros sobre os títulos dos filmes e os nomes de suas línguas. Use as tabelas **film** e **language**.

2. Crie uma *query* utilizando o **INNER JOIN** para retornar duas colunas nomeadas por “Título” e “Categoria”, respectivamente, com registros sobre os títulos dos filmes e os nomes de suas categorias. Use as tabelas **film_category**, **film** e **category**

## LEFT JOIN e RIGHT JOIN

## SELF JOIN

# Vamos praticar!

# Exercícios

### Agora a prática

### Bônus

# Recursos adicionais (opcional)

