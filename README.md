# SUMÁRIO

- [O que vamos aprender?](#o-que-vamos-aprender)

  - [Você será capaz de:](#você-será-capaz-de)
 
- [Por que isso é importante?](#por-que-isso-é-importante)

- [Conteúdos](#conteúdos)

  - [O que é um JOIN?](#o-que-é-um-join)
  - [INNER JOIN](#inner-join)
  - [LEFT JOIN e RIGHT JOIN](#left-join-e-right-join)
  - [FULL JOIN](#full-join)
  - [SELF JOIN](#self-join)

- [Vamos Praticar](#vamos-praticar)

- [Exercícios](#exercícios)
  
  - [Agora a prática](#agora-a-prática)
  - [Bônus](#bônus)
  
- [Recursos adicionais (opcional)](#recursos-adicionais-opcional)

# O que vamos aprender?

Hey Tryber! Hoje você continuará aprofundando seu conhecimento no incrível mundo do SQL ao aprender como juntar dados de tabelas relacionadas por meio dos diferentes tipos de **JOIN** para tornar suas *queries* mais completas e poderosas.

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

Em algum momento na sua carreira como desenvolvedor de software é provável que, ao manipular um banco de dados relacional, você precise relacionar dados de diferentes tabelas e gerar informações mais detalhadas e completas para seus relatórios e consultas. Sendo assim, entender as diferenças e em qual contexto utilizar cada tipo de **JOIN** é extremamente importante para seu sucesso profissional.

# Conteúdos

## O que é um JOIN?

Até agora, você aprendeu a manipular uma tabela para diversos fins, executando operações simples de inserção, seleção, alteração e/ou exclusão ([CRUD](https://developer.mozilla.org/pt-BR/docs/Glossary/CRUD)), até operações mais específicas como selecionar, classificar e/ou agrupar os dados para melhorar a visualização em seus relatórios. Porém, há situações em que uma única tabela não possui todos os dados necessários para gerar as informações que você precisa. É nesse momento em que o conceito de **JOIN** entra em jogo.

O **JOIN** é um recurso do SQL para **combinar** os registros de duas ou mais tabelas em uma única consulta, com base em uma coluna relacionada entre elas.

A partir de agora você será capaz de **juntar** os dados de duas ou mais tabelas por meio do **JOIN**. Essa **junção** pode ser feita de várias formas, veremos mais sobre os tipos de **JOIN** ainda hoje!

![Dragon JOIN Ball](https://c.tenor.com/1wJU51jgwSQAAAAC/dbz-dragonball.gif)

## INNER JOIN

O INNER JOIN seleciona os dados correspondentes entre duas ou 
mais tabelas conectadas por uma coluna em comum. Confira sua sintaxe básica:
```
SELECT
  t1.coluna,
  t2.coluna
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

1. Utilize INNER JOIN para gerar duas colunas. As colunas devem buscar, respectivamente, os nomes das cidades (**city**) e o país referente a cada cidade (**country**).

```
SELECT 
    cit.city, cou.country
FROM
    sakila.city AS cit
        INNER JOIN
    sakila.country AS cou ON cit.country_id = cou.country_id;

```

O resultado da consulta acima será parecido com o seguinte formato:

![consulta-inner-join-exemplo-1](https://i.ibb.co/GF3wyJ3/Captura-de-tela-de-2021-10-13-01-54-41.png)

Também é possível utilizar o INNER JOIN mais de uma vez na mesma **query**, segue o exemplo:

2. Utilize INNER JOIN para gerar três colunas. As colunas devem buscar, respectivamente, o nome completo das pessoas clientes (**customer**), o endereço referente a cada cliente (**address**) e a cidade (**city**) referente a cada endereço encontrado. Os nomes das colunas devem ser: "Nome_Completo", "Endereço", "Cidade".

```
SELECT 
    CONCAT(cus.first_name, ' ', cus.last_name) AS `Nome_Completo`,
    adr.address AS Endereço,
    cit.city AS Cidade
FROM
    sakila.customer AS cus
        INNER JOIN
    sakila.address AS adr ON cus.address_id = adr.address_id
        INNER JOIN
    sakila.city AS cit ON adr.city_id = cit.city_id;

```

O resultado da consulta acima será parecido com o seguinte formato:

![consulta-inner-join-exemplo-2](https://i.ibb.co/wzfwshW/Captura-de-tela-de-2021-10-13-02-04-22.png)

### Desafios

Para os desafios a seguir, também será utilizado o banco de dados público [sakila](https://s3.us-east-2.amazonaws.com/assets.app.betrybe.com/back-end/sakila-1ae15ae82697888c35bf1f1c8acbf755.sql).
Implemente *queries* utilizando o **INNER JOIN** para:

1. Gerar duas colunas nomeadas por “Título” e “Língua”, respectivamente, com registros sobre os títulos dos filmes e os nomes de suas línguas. 
<br/>Dica: Use as tabelas **film** e **language**.

2. Gerar duas colunas nomeadas por “Título” e “Categoria”, respectivamente, com registros sobre os títulos dos filmes e os nomes de suas categorias. 
<br/>Dica: Use as tabelas **film_category**, **film** e **category**.
<br/>Dica: Use mais de um **INNER JOIN**.

3. Gerar duas colunas nomeadas por "Loja_Id", e "Gerente", respectivamente, com registros sobre os *ids* das lojas, e os nomes completos das pessoas gerentes. 
<br/>Dica: Use as tabelas **store**, e **staff**.

4. Gerar três colunas nomeadas por "Cliente_Id", "Cliente", e "Endereço_Loja", respectivamente, com registros sobre os *ids* das pessoas clientes, seus nomes completos e os endereços das lojas que estão cadastradas.
<br/>Dica: Use as tabelas **customer**, **store** e **address**.
<br/>Dica: Use mais de um **INNER JOIN**.

5. Gerar quatro colunas nomeadas por "Alugel_Id", "Filme", "Data_Aluguel" e "Data_Retorno", respectivamente, com registros sobre os *ids* dos aluguéis, os nomes dos filmes alugados e suas datas de aluguéis e devoluções.
<br/>Dica: Use as tabelas **rental**, **inventory** e **film**.
<br/>Dica: Use mais de um **INNER JOIN**.

## LEFT JOIN e RIGHT JOIN

Para entender o conceito de **LEFT JOIN** e **RIGHT JOIN** de forma simplificada imagine a seguinte situação: Você precisa gerar um relatório com registros comuns entre colunas de tabelas diferentes, mas não pode omitir os registros que não possuem relação com os registros da(s) outra(s) coluna(s). Para isso podemos usar o **LEFT JOIN** ou **RIGHT JOIN**.

Para visualizar melhor a situação acima, veja o exemplo abaixo:

Usaremos duas tabelas do banco de dados público [sakila](https://s3.us-east-2.amazonaws.com/assets.app.betrybe.com/back-end/sakila-1ae15ae82697888c35bf1f1c8acbf755.sql): **actor** e **customer**.
Nosso objetivo é gerar um relatório com todos os *ids* e últimos nomes das pessoas Atrizes (**colunas da esquerda**) e os *ids* das pessoas Clientes que possuem os últimos nomes iguais aos das pessoas Atrizes (**coluna da direita**).
Nesse caso, precisamos que todos os registros das colunas da **esquerda** sejam preservados, então usaremos o **LEFT JOIN**:
```
SELECT 
    act.actor_id AS `Atriz_Id`,
    act.last_name AS Último_Nome,
    cus.customer_id AS Cliente_Id
FROM
    sakila.actor AS act
        LEFT JOIN
    sakila.customer AS cus ON act.last_name = cus.last_name;

```

O resultado da consulta acima será parecido com o seguinte formato:

![consulta-left-join-exemplo-1](https://i.ibb.co/M2XXhg0/Captura-de-tela-de-2021-10-13-02-18-47.png)

Observação: Note que ao usar o **LEFT JOIN** os campos que não possuem dados relacionados a sua coluna de referência são preenchidos automaticamente com valor **null**. É possível observar um comportamento semelhante ao usar o **RIGHT JOIN**.

Se o nosso objetivo fosse manter todos os registros das colunas da **direita**, então precisaríamos apenas trocar **LEFT JOIN** por **RIGHT JOIN**:

```
SELECT 
    act.actor_id AS `Ator_Id`,
    act.last_name AS Último_Nome,
    cus.customer_id AS Cliente_Id
FROM
    sakila.actor AS act
        RIGHT JOIN
    sakila.customer AS cus ON act.last_name = cus.last_name;

```

O resultado da consulta acima será parecido com o seguinte formato:

![consulta-left-join-exemplo-2](https://i.ibb.co/MsDs9Rb/Captura-de-tela-de-2021-10-13-02-25-05.png)

E se nosso objetivo mudasse novamente e agora precisaremos manter apenas os registros que possuem relação entre as colunas da esquerda e direita? Para isso usamos o já conhecido **INNER JOIN**:
```
SELECT 
    act.actor_id AS `Ator_Id`,
    act.last_name AS Último_Nome,
    cus.customer_id AS Cliente_Id
FROM
    sakila.actor AS act
        INNER JOIN
    sakila.customer AS cus ON act.last_name = cus.last_name;

```

O resultado da consulta acima será parecido com o seguinte formato:

![consulta-left-join-exemplo-3](https://i.ibb.co/9g9Zzhj/Captura-de-tela-de-2021-10-13-02-27-20.png)

É possível utilizar a [teoría dos conjuntos](https://www.todamateria.com.br/teoria-dos-conjuntos/) novamente para abstrair o conceito dos **JOIN** e representar a diferença entre o **LEFT JOIN**, **RIGHT JOIN** e **INNER JOIN**.

**LEFT JOIN**: Sempre retornará todos os registros da(s) coluna(s) da **esquerda** e os registros correspondentes da direita. 

![representação-left-join](https://www.w3schools.com/sql/img_leftjoin.gif)

**RIGHT JOIN**: Sempre retornará todos os registros da(s) coluna(s) da **direita** e os registros correspondentes da esquerda. 

![representação-right-join](https://www.w3schools.com/sql/img_rightjoin.gif)

**INNER JOIN**: Sempre retornará apenas os registros correspondentes, ignorando os demais registros.

![imagem-inner-join](https://www.w3schools.com/sql/img_innerjoin.gif)

Os diferentes tipos de **JOIN** podem parecer confusos no início do aprendizado. Sinta-se à vontade para ler quantas vezes forem necessárias, reflita um pouco sobre os conceitos aprendidos até o momento e sempre pratique para complementar e consolidar sua leitura.

Dica: Pesquise e baixe bases de dados com informações relevantes para você (filmes, jogos, criptomoedas, etc.) e aplique os conceitos que vem aprendendo nesses bancos de dados. Personalize seus estudos para torná-los mais interessantes!

## FULL JOIN

## SELF JOIN

# Vamos praticar!

# Exercícios

1. Gerar o histórico de aluguéis de filmes utilizando o INNER JOIN para retornar quatro colunas nomeadas por "Aluguel_Id", "Filme", "Cliente" e “Funcionário”. As colunas devem possuir, respectivamente, registros sobre os *ids* dos aluguéis, nomes dos filmes, nome completo dos clientes e funcionários. Utilize as tabelas **rental**, **inventory**, **film**, **staff**: 

### Agora a prática

### Bônus

2. Utilize o INNER JOIN para retornar o resultado de uma *query* que mostre três colunas nomeadas por "Nome_Completo", "Atriz_Id", "Cliente_Id". As colunas devem possuir, respectivamente, registros sobre o nome completo das pessoas Atrizes que possuam o mesmo nome completo dos clientes, e os *ids* das pessoas Atrizes e Clientes.
Dica: Use as tabelas **actor** e **customer**.

# Recursos adicionais (opcional)

