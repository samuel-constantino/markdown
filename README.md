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
SELECT t1.coluna, t2.coluna
FROM tabela1 AS t1
INNER JOIN tabela2 AS t2
ON t1.coluna_em_comum = t2.coluna_em_comum;
```

Note que na sintaxe acima é usado o *alias* (**AS**) para nomear temporariamente as tabelas. O alias não é necessário para o sucesso da *query*, mas usá-lo é uma
boa prática, pois torna o nome das colunas mais legíveis e facilita usá-las em outras partes do código. Clique [nesse link](https://www.w3schools.com/sql/sql_alias.asp) para saber mais sobre *alias*.

É possível representar o efeito do INNER JOIN por meio da [teoría dos conjuntos](https://www.todamateria.com.br/teoria-dos-conjuntos/), da seguinte forma:

![imagem-inner-join](https://www.w3schools.com/sql/img_innerjoin.gif)

No exemplo acima, o resultado do INNER JOIN é a interseção entre as duas tabelas.



## LEFT JOIN e RIGHT JOIN

## SELF JOIN

# Vamos praticar!

# Exercícios

### Agora a prática

### Bônus

# Recursos adicionais (opcional)

