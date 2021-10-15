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

Hey Tryber! Hoje você continuará aprofundando seu conhecimento no incrível mundo do SQL ao aprender como juntar dados de tabelas relacionadas por meio dos diferentes tipos de **JOIN** para tornar suas *queries* mais completas e poderosas.

## Você será capaz de

- Utilizar `INNER JOIN` para selecionar registros comuns 
entre tabelas; 

- Utilizar `LEFT JOIN` para selecionar todos registros de uma
tabela (esquerda) e os registros correspondentes de outra 
tabela (direita);

- Utilizar `RIGHT JOIN` para selecionar todos registros de uma
tabela (direita) e os registros correspondentes de outra 
tabela (esquerda);

- Utilizar `SELF JOIN` para juntar uma tabela com 
ela própria (auto-junção)

# Por que isso é importante?

Em algum momento na sua carreira como pessoa desenvolvedora de software é provável que, ao manipular um banco de dados relacional, você precise relacionar dados de diferentes tabelas e gerar informações mais detalhadas e completas para seus relatórios e consultas. Sendo assim, entender as diferenças e em qual contexto utilizar cada tipo de `JOIN` é extremamente importante para seu sucesso profissional.

# Conteúdos

## O que é um JOIN?

Até agora, você aprendeu a manipular uma tabela para diversos fins, executando operações simples de inserção, seleção, alteração e/ou exclusão ([CRUD](https://developer.mozilla.org/pt-BR/docs/Glossary/CRUD)), até operações mais específicas como selecionar, classificar e/ou agrupar os dados para melhorar a visualização em seus relatórios. Porém, há situações em que uma única tabela não possui todos os dados necessários para gerar as informações que você precisa. É nesse momento em que o conceito de `JOIN` entra em jogo.

O `JOIN` é um recurso do SQL para **combinar** os registros de duas ou mais tabelas em uma única consulta, com base em uma coluna relacionada entre elas.

A partir de agora você será capaz de **juntar** os dados de duas ou mais tabelas por meio do `JOIN`. Essa **junção** pode ser feita de várias formas, veremos mais sobre os tipos de `JOIN` ainda hoje!

<div align="center">
  <img src="https://c.tenor.com/1wJU51jgwSQAAAAC/dbz-dragonball.gif" alt="Dragon JOIN Ball" width="500"/>
</div>

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

Note que na sintaxe acima é usado o *alias* (`AS`) para nomear temporariamente as tabelas. O *alias* não é necessário para o sucesso da *query*, mas usá-lo é uma
boa prática, pois torna o nome das colunas mais legíveis e facilita usá-las em outras partes do código. Clique [nesse link](https://www.w3schools.com/sql/sql_alias.asp) para saber mais sobre *alias*.

É possível representar o efeito do INNER JOIN por meio da [teoria dos conjuntos](https://www.todamateria.com.br/teoria-dos-conjuntos/) da seguinte forma:

<div align="center">
  <img src="https://s3.us-east-2.amazonaws.com/assets.app.betrybe.com/back-end/sql/images/innerjoin-dcdd0d7b81d1843386871875fc408dd4.png" alt="imagem-inner-join" width="250"/>
</div>

### Exemplos

Para os exemplos a seguir, será utilizado o banco de dados público [sakila](https://s3.us-east-2.amazonaws.com/assets.app.betrybe.com/back-end/sakila-1ae15ae82697888c35bf1f1c8acbf755.sql).

Dica: | Para restaurar o banco de dados baixe o arquivo *sql* acima e siga [este tutorial](https://dev.mysql.com/doc/workbench/en/wb-admin-export-import-management.html) ou consulte o conteúdo 19.1 aqui no Course.
------|-----------------------------------------------------

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

<div align="center">
  <img src="https://i.ibb.co/GF3wyJ3/Captura-de-tela-de-2021-10-13-01-54-41.png" alt="consulta-inner-join-exemplo-1" width="400"/>
</div>

Também é possível utilizar o INNER JOIN mais de uma vez na mesma *query*, segue o exemplo:

2. Utilize INNER JOIN para gerar três colunas. As colunas devem buscar, respectivamente, o nome completo das pessoas clientes (**customer**), o endereço referente a cada pessoa cliente (**address**) e a cidade (**city**) referente a cada endereço encontrado. Os nomes das colunas devem ser: "Nome_Completo", "Endereço", "Cidade".

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

O resultado da consulta acima será parecido com o seguinte formato:

<div align="center">
  <img src="https://i.ibb.co/D4MXcGg/Captura-de-tela-de-2021-10-13-20-38-12.png" alt="consulta-inner-join-exemplo-2" width="400"/>
</div>

### Desafios

Para os desafios a seguir, também será utilizado o banco de dados público [sakila](https://s3.us-east-2.amazonaws.com/assets.app.betrybe.com/back-end/sakila-1ae15ae82697888c35bf1f1c8acbf755.sql).
Implemente *queries* utilizando o `INNER JOIN` para:

1. Gerar duas colunas nomeadas por “Título” e “Língua”, respectivamente, com registros sobre os títulos dos filmes e os nomes de suas línguas. 

Dica: | Use as tabelas "film" e "language".
------|-----------------------------------------------------------

2. Gerar duas colunas nomeadas por “Título” e “Categoria”, respectivamente, com registros sobre os títulos dos filmes e os nomes de suas categorias. 

Dica: | Use as tabelas "film_category", "film" e "category" e use mais de um `INNER JOIN`.
------|-----------------------------------------------------------

3. Gerar duas colunas nomeadas por "Loja_Id", e "Gerente", respectivamente, com registros sobre os *ids* das lojas e os nomes completos das pessoas gerentes. 

Dica: | Use as tabelas "store", e "staff".
------|-----------------------------------------------------------

4. Gerar três colunas nomeadas por "Cliente_Id", "Cliente", e "Endereço_Loja", respectivamente, com registros sobre os *ids* das pessoas clientes, seus nomes completos e os endereços das lojas que estão cadastradas.

Dica: | Use as tabelas "customer", "store" e "address" e use mais de um `INNER JOIN`.
------|-----------------------------------------------------------

5. Gerar quatro colunas nomeadas por "Alugel_Id", "Filme", "Data_Aluguel" e "Data_Retorno", respectivamente, com registros sobre os *ids* dos aluguéis, os nomes dos filmes alugados e suas datas de aluguéis e devoluções.

Dica: | Use as tabelas "rental", "inventory" e "film" e use mais de um `INNER JOIN`.
------|-----------------------------------------------------------

## `LEFT JOIN` e `RIGHT JOIN`

Para entender o conceito de `LEFT JOIN` e `RIGHT JOIN` de forma simplificada imagine a seguinte situação: Você precisa gerar um relatório com registros comuns entre colunas de tabelas diferentes, mas não pode omitir os registros que não possuem relação com os registros da(s) outra(s) coluna(s). Para isso podemos usar o `LEFT JOIN` ou `RIGHT JOIN`.

A sintaxe do `LEFT JOIN` e `RIGHT JOIN` continuam seguindo o mesmo padrão:

Sintaxe `LEFT JOIN`:
```
SELECT
    column_name(s)
FROM
    table1
        LEFT JOIN
    table2 ON table1.column_name = table2.column_name;
```
Sintaxe `RIGHT JOIN`:
```
SELECT
    column_name(s)
FROM
    table1
        RIGHT JOIN
    table2 ON table1.column_name = table2.column_name;
```

### Exemplos

Usaremos duas tabelas do banco de dados público [sakila](https://s3.us-east-2.amazonaws.com/assets.app.betrybe.com/back-end/sakila-1ae15ae82697888c35bf1f1c8acbf755.sql): **actor** e **customer**.
Nosso objetivo é gerar um relatório com todos os *ids* e últimos nomes das pessoas Atrizes (**colunas da esquerda**) e os *ids* das pessoas Clientes que possuem os últimos nomes iguais aos das pessoas Atrizes (**coluna da direita**).
Nesse caso, precisamos que todos os registros das colunas da **esquerda** sejam preservados, então usaremos o **LEFT JOIN**:
```
SELECT 
    act.actor_id AS `Atriz_Id`,
    act.last_name AS `Último_Nome`,
    cus.customer_id AS `Cliente_Id`
FROM
    sakila.actor AS act
        LEFT JOIN
    sakila.customer AS cus ON act.last_name = cus.last_name;

```

O resultado da consulta acima será parecido com o seguinte formato:

<div align="center">
  <img src="https://i.ibb.co/M2XXhg0/Captura-de-tela-de-2021-10-13-02-18-47.png" alt="consulta-left-join-exemplo-1" width="400"/>
</div>

Observação: Note que ao usar o `LEFT JOIN` os campos que não possuem dados relacionados à sua coluna de referência são preenchidos automaticamente com valor **null**. É possível observar um comportamento semelhante ao usar o `RIGHT JOIN`.

Se o nosso objetivo fosse manter todos os registros das colunas da **direita**, então precisaríamos apenas trocar `LEFT JOIN` por `RIGHT JOIN`:

```
SELECT 
    act.actor_id AS `Ator_Id`,
    act.last_name AS `Último_Nome`,
    cus.customer_id AS `Cliente_Id`
FROM
    sakila.actor AS act
        RIGHT JOIN
    sakila.customer AS cus ON act.last_name = cus.last_name;

```

O resultado da consulta acima será parecido com o seguinte formato:

<div align="center">
  <img src="https://i.ibb.co/MsDs9Rb/Captura-de-tela-de-2021-10-13-02-25-05.png" alt="consulta-left-join-exemplo-2" width="400"/>
</div>

E se nosso objetivo mudasse novamente e agora precisaremos manter apenas os registros que possuem relação entre as colunas da esquerda e direita? Para isso usamos o já conhecido `INNER JOIN`:
```
SELECT 
    act.actor_id AS `Ator_Id`,
    act.last_name AS `Último_Nome`,
    cus.customer_id AS `Cliente_Id`
FROM
    sakila.actor AS act
        INNER JOIN
    sakila.customer AS cus ON act.last_name = cus.last_name;

```

O resultado da consulta acima será parecido com o seguinte formato:

<div align="center">
  <img src="https://i.ibb.co/9g9Zzhj/Captura-de-tela-de-2021-10-13-02-27-20.png" alt="consulta-left-join-exemplo-3" width="400"/>
</div>

É possível utilizar a [teoria dos conjuntos](https://www.todamateria.com.br/teoria-dos-conjuntos/) novamente para abstrair o conceito dos `JOIN` e representar a diferença entre o `LEFT JOIN`, `RIGHT JOIN` e `INNER JOIN`.

**LEFT JOIN**: Sempre retornará todos os registros da(s) coluna(s) da **esquerda** e os registros correspondentes da direita. 

<div align="center">
  <img src="https://s3.us-east-2.amazonaws.com/assets.app.betrybe.com/back-end/sql/images/leftjoin-3bd116be2c7d08ac759c74353260cfea.png" alt="representação-left-join" width="250"/>
</div>

**RIGHT JOIN**: Sempre retornará todos os registros da(s) coluna(s) da **direita** e os registros correspondentes da esquerda. 

<div align="center">
  <img src="https://s3.us-east-2.amazonaws.com/assets.app.betrybe.com/back-end/sql/images/rightjoin-f8109b9bb4ea1ed927109d1e19a1a262.png" alt="representação-right-join" width="250"/>
</div>

**INNER JOIN**: Sempre retornará apenas os registros correspondentes, ignorando os demais registros.

<div align="center">
  <img src="https://s3.us-east-2.amazonaws.com/assets.app.betrybe.com/back-end/sql/images/innerjoin-dcdd0d7b81d1843386871875fc408dd4.png" alt="imagem-inner-join" width="250"/>
</div>

Os diferentes tipos de **JOIN** podem parecer confusos no início do aprendizado. Sinta-se à vontade para ler quantas vezes forem necessárias, reflita um pouco sobre os conceitos aprendidos até o momento e sempre pratique para complementar e consolidar sua leitura.

Dica: | Pesquise e baixe bases de dados com informações relevantes para você (filmes, jogos, criptomoedas, etc.) e aplique os conceitos que vem aprendendo nesses bancos de dados. Personalize seus estudos para torná-los mais interessantes!
------|-----------------------------------------------------------

## SELF JOIN

Até o momento, aprendemos sobre os tipos de **JOIN** que usam mais de uma tabela para comparar registros e gerar relatórios mais detalhados. Porém, há situações em que precisamos comparar registros da mesma tabela. Por causa disso foi criado o conceito de **SELF JOIN**, que tem como objetivo criar um **JOIN** com a própria tabela. Essa ação também é conhecida como **auto-junção**.

A sintaxe <s>diferentona</s> básica do **SELF JOIN**:

```
SELECT
  t1.coluna,
  t2.coluna
FROM
  table1 AS T1,
  table1 AS T2
WHERE
  condition;
```

Na sintaxe acima o **FROM** referencia a mesma tabela duas vezes com diferentes *alias*, tratando-as como tabelas diferentes para depois aplicar uma junção por meio da condição do **WHERE**.

### Exemplos
  
Para entender melhor esse conceito, observe os exemplos a seguir:

Continuaremos utilizando o banco de dados [sakila](https://s3.us-east-2.amazonaws.com/assets.app.betrybe.com/back-end/sakila-1ae15ae82697888c35bf1f1c8acbf755.sql).

1. A tabela **actor** possui registros com o nome de todas as pessoas atrizes do banco de dados. Como podemos criar uma *query* que nos retorne um relatório que exiba duas colunas relacionando os registros que possuem o mesmo sobrenome?
Note que para criarmos essa *query* precisamos relacionar os registros da tabela **actor** com ela mesma para comparar os sobrenomes das pessoas atrizes.

```
SELECT 
    CONCAT(t1.first_name, ' ', t1.last_name) AS `T1`,
    CONCAT(t2.first_name, ' ', t2.last_name) AS `T2`
FROM
    sakila.actor AS t1,
    sakila.actor AS t2
WHERE
    t1.actor_id <> t2.actor_id
        AND t1.last_name = t2.last_name;

```
O resultado da consulta acima será parecido com o seguinte formato:

<div align="center">
  <img src="https://i.ibb.co/ZYFsnRS/Captura-de-tela-de-2021-10-13-21-13-15.png" alt="consulta-self-join-exemplo-1" width="400"/>
</div>
  
2. A tabela **film** possui registros com as informações de todos os filmes do banco de dados. Como podemos criar uma *query* que nos retorne um relatório que exiba três colunas: A primeira exibindo o tamanho dos filmes, e a segunda e terceira coluna relacionando os filmes que possuem o tamanho igual ao informado na primeira coluna? 

```
SELECT 
    t1.length AS `Tamanho`,
    t1.title AS `T1_Título`,
    t2.title AS `T2_Título`
FROM
    sakila.film AS t1,
    sakila.film AS t2
WHERE
    t1.film_id <> t2.film_id
        AND t1.length = t2.length;

```
O resultado da consulta acima será parecido com o seguinte formato:

<div align="center">
  <img src="https://i.ibb.co/BcCxB75/Captura-de-tela-de-2021-10-13-23-12-50.png" alt="consulta-self-join-exemplo-2" width="400"/>
</div>

### Desafios

Para os desafios a seguir, também será utilizado o banco de dados público [sakila](https://s3.us-east-2.amazonaws.com/assets.app.betrybe.com/back-end/sakila-1ae15ae82697888c35bf1f1c8acbf755.sql).
Implemente *queries* utilizando o **SELF JOIN* para:

1. Gerar três colunas nomeadas por "Primeiro_Nome", "T1_Sobrenome" e "T2_Sobrenome", respectivamente, 
com registros sobre os primeiros nomes das pessoas atrizes e os sobrenomes que estão relacionados aos
registros da coluna "Primeiro_Nome". Certifique-se que não haverá sobrenomes com o mesmo *id*.

# Vamos praticar!

Chegou o momento de acompanhar a aula ao vivo! Acesse o link disponível no canal da sua turma, no Slack.

# Exercícios

## Antes de começar: versionando seu código

Para versionar seu código, utilize o seu repositório de exercícios. 😉

Abaixo você vai ver exemplos de como organizar os exercícios do dia em uma **branch**, com arquivos e **commits** específicos para cada exercício. Você deve seguir este padrão para realizar os exercícios a seguir.

1. Abra a pasta de exercícios:

```
$ cd ~/trybe-exercicios
```

2. Certifique-se de que está na branch main e ela está sincronizada com a remota. Caso você tenha arquivos modificados e não comitados, deverá fazer um commit ou checkout dos arquivos antes deste passo.

```
$ git checkout main
$ git pull
```

3. A partir da main, crie uma branch com o nome exercicios/20.2 (bloco 20, dia 2)

```
$ git checkout -b exercicios/20.2
```

4. Caso seja o primeiro dia deste módulo, crie um diretório para ele e o acesse na sequência:

```
$ mkdir back-end
$ cd back-end
```

5. Caso seja o primeiro dia do bloco, crie um diretório para ele e o acesse na sequência:

```
$ mkdir bloco-20-funcoes-sql-joins-e-subqueries
$ cd bloco-20-funcoes-sql-joins-e-subqueries
```

6. Crie um diretório para o dia e o acesse na sequência:

```
$ mkdir dia-2-descomplicando-joins-unions-e-subqueries
$ cd dia-2-descomplicando-joins-unions-e-subqueries
```

7. Os arquivos referentes aos exercícios deste dia deverão ficar dentro do diretório **~/trybe-exercicios/back-end/block-20-funcoes-sql-joins-e-subqueries/dia-2-descomplicando-joins-unions-e-subqueries**. Lembre-se de fazer commits pequenos e com mensagens bem descritivas, preferencialmente a cada exercício resolvido.

**Verifique os arquivos alterados/adicionados:**

```
$ git status
On branch exercicios/20.2
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

  modified:   exercicio-1
```

**Adicione os arquivos que farão parte daquele commit:**

```
# Se quiser adicionar os arquivos individualmente
$ git add caminhoParaArquivo

# Se quiser adicionar todos os arquivos de uma vez, porém, atente-se
para não adicionar arquivos indesejados acidentalmente
$ git add --all
```

**Faça o commit com uma mensagem descritiva das alterações:**

```
$ git commit -m "Mensagem descrevendo alterações"
```

Você pode visualizar o log de todos os commits já feitos naquela branch com **git log.**

```
$ git log
commit 100c5ca0d64e2b8649f48edf3be13588a77b8fa4 (HEAD -> exercicios/20.2)
Author: Tryber Bot <tryberbot@betrybe.com>
Date:   Fry Sep 27 17:48:01 2019 -0300

    Exercicio 2 - mudando o evento de click para mouseover, tirei o alert e coloquei pra quando clicar aparecer uma imagem do lado direito da tela

commit c0701d91274c2ac8a29b9a7fbe4302accacf3c78
Author: Tryber Bot <tryberbot@betrybe.com>
Date:   Fry Sep 27 16:47:21 2019 -0300

    Exercicio 2 - adicionando um alert, usando função e o evento click

commit 6835287c44e9ac9cdd459003a7a6b1b1a7700157
Author: Tryber Bot <tryberbot@betrybe.com>
Date:   Fry Sep 27 15:46:32 2019 -0300

    Resolvendo o exercício 1 usando eventListener
```

9. Agora que temos as alterações salvas no **repositório local** precisamos enviá-las para o repositório remoto. **No primeiro envio**, a branch **exercicios/20.2** não vai existir no **repositório remoto**, então precisamos configurar o **remote** utilizando a opção **--set-upstream** (ou **-u**, que é a forma abreviada).

```
$ git push -u origin exercicios/20.2
```

10. Após realizar o passo 9, podemos abrir a Pull Request a partir do link que aparecerá na mensagem do push no terminal, ou na página do seu repositório de exercícios no GitHub através de um botão que aparecerá na interface. Escolha a forma que preferir e abra a Pull Request. De agora em diante, você repetirá o fluxo a partir do passo 7 para cada exercício adicionado, porém como já definimos a branch remota com -u anteriormente, agora podemos simplificar os comandos para:

```
# Quando quiser enviar para o repositório remoto
$ git push
# Caso você queria sincronizar com o remoto, poderá utilizar apenas
$ git pull
```

11. Quando terminar os exercícios, seus códigos devem estar todos commitados na branch **exercicios/20.2**, e disponíveis no repositório remoto do **GitHub**. Pra finalizar, compartilhe o link da **Pull Request** no canal de **Code Review** para a monitoria e/ou colegas revisarem. Faça review você também, lembre-se que **é muito importante para o seu desenvolvimento ler o código de outras pessoas.** 🤜🏼🤛🏼

### Agora a prática

Implemente a resolução dos exercícios propostos utilizando o banco de dados [hr](https://s3.us-east-2.amazonaws.com/assets.app.betrybe.com/back-end/sql/hr-cebf8bc2a5bb252bc470ae28943604c6.sql).

1. Imagine a seguinte situação: Você está desenvolvendo uma aplicação que precisa buscar informações sobre os nomes dos países presentes em um banco de dados relacional e suas respectivas regiões. Mas essas informações estão em tabelas diferentes. Como você criaria uma *query* resolver essa situação?

Observações: | Nomeie as tabelas com "País" e "Região" e certifique-se de ordenar a query pelo **país** de forma ascendente.
------|-----------------------------------------------------------

Dica: | Use as tabelas "countries" e "regions".
------|-----------------------------------------------------------


2. Imagine agora que você faz parte do time de Recursos Humanos de uma grande empresa. Seu objetivo para hoje é gerar um relatório com o quatro colunas nomeadas por "Funcionário_Id", "Funcionário", "Função", e "Departamento". Essas colunas devem gerar, respectivamente, os *ids* das pessoas funcionárias, seus nomes completos, os nomes de suas funções e seus departamentos.

Obeservação: | Ordene o resultado da sua *query* pela coluna "Funcionário" em ordem alfabética.
------|-----------------------------------------------------------

Dica: | Use as tabelas "employees", "departments" e "jobs".
------|-----------------------------------------------------------

3. Ainda no contexto do exercício anterior, você recebeu um novo objetivo: gerar um relatório 
sobre a relação entre as funções das pessoas funcionárias e seus salários. Seu relatório deve conter 
três colunas nomeadas por "Funcionário", "Função" e "Salário". Essas colunas devem fornecer, respectivamente, 
o nome completo das pessoas funcionárias, suas funções na empresa e seus salários.
<br/>Observações: Gere seu relatório apenas pessoas funcionárias com salário acima ou igual a 10000. Ordene
o resultado da *query* com a coluna "Salário" em ordem decrescente.

Dica: | Use as tabelas "employees" e "jobs".
------|-----------------------------------------------------------

### Bônus

6. Gerar o histórico de aluguéis de filmes utilizando o INNER JOIN para retornar quatro colunas nomeadas por "Aluguel_Id", "Filme", "Cliente" e “Funcionário”. As colunas devem possuir, respectivamente, registros sobre os *ids* dos aluguéis, nomes dos filmes, nome completo das pessoas funcionárias e clientes. Utilize as tabelas **rental**, **inventory**, **film**, **staff**: 

7. Utilize o INNER JOIN para retornar o resultado de uma *query* que mostre três colunas nomeadas por "Nome_Completo", "Atriz_Id", "Cliente_Id". As colunas devem possuir, respectivamente, registros o mesmo nome completo entre as colunas, e os *ids* das pessoas Atrizes e Clientes.

Dica: | Use as tabelas "actor" e "customer".
------|-----------------------------------------------------------

# Recursos adicionais (opcional)

1. Tenha outra perspectiva sobre JOIN com [w3schools](https://www.w3schools.com/sql/sql_join.asp).
2. 

