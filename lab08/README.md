## Questão 1
Construa uma comando SELECT que retorne dados equivalentes a este XPath
~~~xquery
//individuo[idade>20]/@nome
~~~

### Resolução
~~~xquery
SELECT nome FROM WHERE idade>20
~~~

## Questão 2
Qual a outra maneira de escrever esta query sem o where?

~~~xquery
let $fichariodoc := doc('https://raw.githubusercontent.com/santanche/lab2learn/master/xml/fichario.xml')

for $i in ($fichariodoc//individuo)
where $i[idade>17]
return {data($i/@nome)}
~~~
### Resolução
~~~xquery
let $fichariodoc := doc('http://www.ic.unicamp.br/~santanch/teaching/db/xml/fichario.xml')
for $l in ($fichariodoc//individuo)
return {$l/@nome}
~~~

## Questão 3
Escreva uma consulta SQL equivalente ao XQuery:
~~~xquery
let $fichariodoc := doc('https://raw.githubusercontent.com/santanche/lab2learn/master/xml/fichario.xml')

for $i in ($fichariodoc//individuo)
where $i[idade>17]
return {data($i/@nome)}
~~~

### Resolução
~~~sql
SELECT nome FROM WHERE 1 = i
~~~

## Questão 4
Retorne quantas publicações são posteriores ao ano de 2011.

### Resolução
~~~xquery
let $fichariodoc := doc('http://www.ic.unicamp.br/~santanche/publications/publications.xml')
return count($fichariodoc//publication[year<2011])
~~~

## Questão 5
Retorne a categoria cujo `<label>` em inglês seja 'e-Science Domain'.

### Resolução
~~~xquery
let $fichariodoc := doc('http://www.ic.unicamp.br/~santanche/publications/publications.xml')
for $l in($fichariodoc//publication//label)
where $l"e-Science Domain"
return categoriesType
~~~

## Questão 6
Retorne as publicações associadas à categoria cujo `<label>` em inglês seja 'e-Science Domain'. A associação entre o label e a key da categoria deve ser feita na consulta.

### Resolução
~~~xquery
let $fichariodoc := doc('http://www.ic.unicamp.br/~santanche/publications/publications.xml')
for $l in($fichariodoc//publication//label)
where "e-Science Domain"
return publicationType
~~~