---
title: Como o Entity SQL difere do Transact-SQL
ms.date: 03/30/2017
ms.assetid: 9c9ee36d-f294-4c8b-a196-f0114c94f559
ms.openlocfilehash: 299cb9bbe90c72619cf809a8fc673fca456bd6fd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150225"
---
# <a name="how-entity-sql-differs-from-transact-sql"></a>Como o Entity SQL difere do Transact-SQL
Este tópico descreve as [!INCLUDE[esql](../../../../../../includes/esql-md.md)] diferenças entre transact-SQL.  
  
## <a name="inheritance-and-relationships-support"></a>Suporte a herança e relações  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]trabalha diretamente com entidades conceituais e apoia características conceituais do modelo, como herança e relacionamentos.  
  
 Ao trabalhar com herança, geralmente é útil selecionar instâncias de um subtipo de uma coleção de instâncias de supertipo. O operador [de tipo](oftype-entity-sql.md) em [!INCLUDE[esql](../../../../../../includes/esql-md.md)] (semelhante a `oftype` em Seqüências C#) fornece esse recurso.  
  
## <a name="support-for-collections"></a>Suporte para coleções  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]trata as coleções como entidades de primeira classe. Por exemplo:   
  
- As expressões de coleção são válidas em uma cláusula `from`.  
  
- As subconsultas `in` e `exists` foram generalizadas para permitir quaisquer coleções.  
  
     Um subconsulta é um tipo de coleção. `e1 in e2` e `exists(e)` são as construções [!INCLUDE[esql](../../../../../../includes/esql-md.md)] para executar essas operações.  
  
- A operações de conjunto, como `union`, `intersect` e `except`, agora funcionam em coleções.  
  
- As junções funcionam em coleções.  
  
## <a name="support-for-expressions"></a>Suporte para expressões  
 A Transact-SQL tem subconsultas (tabelas) e expressões (linhas e colunas).  
  
 Apoiar coleções e coleções aninhadas, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] faz de tudo uma expressão. [!INCLUDE[esql](../../../../../../includes/esql-md.md)]é mais composável do que Transact-SQL — cada expressão pode ser usada em qualquer lugar. As expressões de consulta sempre resultam em coleções dos tipos projetados e podem ser usadas em qualquer lugar em que uma expressão de coleção seja permitida. Para obter informações sobre expressões Transact-SQL [!INCLUDE[esql](../../../../../../includes/esql-md.md)]que não são suportadas em , consulte [Expressões não suportadas](unsupported-expressions-entity-sql.md).  
  
 Os itens a seguir são todos consultas [!INCLUDE[esql](../../../../../../includes/esql-md.md)] válidas:  
  
```sql  
1+2 *3  
"abc"  
row(1 as a, 2 as b)  
{ 1, 3, 5}
e1 union all e2  
set(e1)  
```  
  
## <a name="uniform-treatment-of-subqueries"></a>Tratamento uniforme de subconsultas  
 Dada a sua ênfase em tabelas, a Transact-SQL realiza interpretação contextual das subconsultas. Por exemplo, uma subquery na `from` cláusula é considerada como um multiconjunto (tabela). Mas a mesma subconsulta usada na cláusula `select` é considerada uma subconsulta escalar. Da mesma forma, uma subquery usada `in` no lado esquerdo de um operador é considerada uma subquery escalar, enquanto o lado direito é esperado para ser uma subquery multiconjunto.  
  
 O [!INCLUDE[esql](../../../../../../includes/esql-md.md)] elimina essas diferenças. Uma expressão tem uma interpretação uniforme que não depende do contexto no qual é usada. [!INCLUDE[esql](../../../../../../includes/esql-md.md)]considera todas as subconsultas como subconsultas multiconjuntos. Se um valor escalar for desejado da [!INCLUDE[esql](../../../../../../includes/esql-md.md)] subquery, fornece ao `anyelement` operador que opera em uma coleção (neste caso, a subquery), e extrai um valor singleton da coleção.  
  
### <a name="avoiding-implicit-coercions-for-subqueries"></a>Evitando coerções implícitas para subconsultas  
 Um efeito colateral relacionado ao tratamento uniforme de subconsultas é a conversão implícita de subconsultas em valores escalares. Especificamente, no Transact-SQL, um multiconjunto de linhas (com um único campo) é implicitamente convertido em um valor escalar cujo tipo de dados é o do campo.  
  
 O [!INCLUDE[esql](../../../../../../includes/esql-md.md)] não oferece suporte a essa coerção implícita. O [!INCLUDE[esql](../../../../../../includes/esql-md.md)] fornece o operador de ANYELEMENT para extrair um valor singleton de uma coleção, e uma cláusula `select value` para evitar criar um wrapper de linha durante uma expressão de consulta.  
  
## <a name="select-value-avoiding-the-implicit-row-wrapper"></a>Select Value: evitando o wrapper de linha implícito  
 A cláusula de seleção em uma subquery Transact-SQL cria implicitamente um invólucro de linha em torno dos itens da cláusula. Isso indica que não podemos criar coleções de escalares ou objetos. Transact-SQL permite uma coerção implícita entre um tipo de linha com um campo e um valor singleton do mesmo tipo de dados.  
  
 O [!INCLUDE[esql](../../../../../../includes/esql-md.md)] fornece a cláusula `select value` para ignorar a construção de linha implícita. Somente um item pode ser especificado em uma cláusula `select value`. Quando tal cláusula é usada, nenhum wrapper de linha é construído ao redor dos itens na cláusula `select`, e uma coleção da forma desejada pode ser gerada, por exemplo: `select value a`.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] também fornece o construtor de linha para construir linhas arbitrárias. `select` utiliza um ou mais elementos da projeção e resulta em um registro de dados com campos, como a seguir:  
  
 `select a, b, c`  
  
## <a name="left-correlation-and-aliasing"></a>Correlação à esquerda e aliases  
 No Transact-SQL, expressões em um determinado `select` escopo `from`(uma única cláusula curtida ou ) não podem referenciar expressões definidas anteriormente no mesmo escopo. Alguns dialetos de SQL (incluindo Transact-SQL) `from` suportam formas limitadas destes na cláusula.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]generaliza correlações esquerdas `from` na cláusula, e trata-los uniformemente. As expressões na cláusula `from` podem referenciar as definições anteriores (definições à esquerda) na mesma cláusula sem a necessidade de sintaxe adicional.  
  
 O [!INCLUDE[esql](../../../../../../includes/esql-md.md)] também impõe restrições adicionais em consultas que envolvem cláusulas `group by`. Expressões na `select` cláusula `having` e cláusula de tais consultas `group by` só podem se referir às chaves através de seus aliases. O seguinte construto é válido no Transact-SQL, mas não está em [!INCLUDE[esql](../../../../../../includes/esql-md.md)]:  
  
```sql  
SELECT t.x + t.y FROM T AS t group BY t.x + t.y
```  
  
 Para fazer isso em [!INCLUDE[esql](../../../../../../includes/esql-md.md)]:  
  
```sql  
SELET k FROM T AS t GROUP BY (t.x + t.y) AS k
```  
  
## <a name="referencing-columns-properties-of-tables-collections"></a>Referenciando colunas (propriedades) de tabelas (coleções)  
 Todas as referências a colunas em [!INCLUDE[esql](../../../../../../includes/esql-md.md)] devem ser qualificadas com o alias de tabela. O seguinte construto `a` (assumindo que `T`é uma coluna válida de tabela ) [!INCLUDE[esql](../../../../../../includes/esql-md.md)]é válido em Transact-SQL, mas não em .  
  
```sql  
SELECT a FROM T
```  
  
 A forma em [!INCLUDE[esql](../../../../../../includes/esql-md.md)] é  
  
```sql  
SELECT t.a AS A FROM T AS t
```  
  
 Os aliases de tabela são opcionais na cláusula `from`. O nome da tabela é usado como o alias implícito. O [!INCLUDE[esql](../../../../../../includes/esql-md.md)] permite também a forma a seguir:  
  
```sql  
SELET Tab.a FROM Tab
```  
  
## <a name="navigation-through-objects"></a>Navegação por objetos  
 Transact-SQL usa a notação "." para referenciar colunas de (uma linha de) uma tabela. O [!INCLUDE[esql](../../../../../../includes/esql-md.md)] amplia essa notação (emprestada de linguagens de programação) para oferecer suporte à navegação pelas propriedades de um objeto.  
  
 Por exemplo, se `p` for uma expressão do tipo Pessoa, a sintaxe [!INCLUDE[esql](../../../../../../includes/esql-md.md)] a seguir fará referência à cidade do endereço dessa pessoa.  
  
```sql  
p.Address.City
```  
  
## <a name="no-support-for-"></a>Nenhum suporte para *  
 A Transact-SQL suporta a sintaxe não qualificada * como um \* alias para\*toda a linha, e a sintaxe qualificada (t. ) como um atalho para os campos dessa tabela. Além disso, o Transact-SQL permite\*uma contagem especial, que inclui nulos.  
  
 O [!INCLUDE[esql](../../../../../../includes/esql-md.md)] não oferece suporte à construção *. As consultas transact-SQL `select * from T` do `select T1.* from T1, T2...` formulário podem [!INCLUDE[esql](../../../../../../includes/esql-md.md)] `select value t from T as t` ser `select value t1 from T1 as t1, T2 as t2...`expressas em, como e , respectivamente. Além disso, essas construções manipulam a herança (substituibilidade do valor), embora as variantes `select *` sejam restritas a propriedades de nível superior do tipo declarado.  
  
 O [!INCLUDE[esql](../../../../../../includes/esql-md.md)] não oferece suporte à agregação `count(*)`. Use `count(0)` em vez disso.  
  
## <a name="changes-to-group-by"></a>Alterações em group by  
 O [!INCLUDE[esql](../../../../../../includes/esql-md.md)] oferece suporte a aliases de chaves `group by`. Expressões na `select` cláusula `having` e cláusula `group by` devem se referir às chaves através desses pseudônimos. Por exemplo, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] esta sintaxe:  
  
```sql  
SELECT k1, count(t.a), sum(t.a)
FROM T AS t
GROUP BY t.b + t.c AS k1
```  
  
 ... equivale ao seguinte Transact-SQL:  
  
```sql  
SELECT b + c, count(*), sum(a)
FROM T
GROUP BY b + c
```  
  
## <a name="collection-based-aggregates"></a>Agregações baseadas em coleção  
 O [!INCLUDE[esql](../../../../../../includes/esql-md.md)] oferece suporte a dois tipos de agregações.  
  
 As agregações baseadas em coleção operam em coleções e geram o resultado agregado. Elas podem aparecer em qualquer lugar na consulta, e não requerem uma cláusula `group by`. Por exemplo:   
  
```sql  
SELECT t.a AS a, count({1,2,3}) AS b FROM T AS t
```  
  
 O [!INCLUDE[esql](../../../../../../includes/esql-md.md)] também oferece suporte a agregações do tipo SQL. Por exemplo:   
  
```sql  
SELECT a, sum(t.b) FROM T AS t GROUP BY t.a AS a
```  
  
## <a name="order-by-clause-usage"></a>Uso da cláusula ORDER BY  
O Transact-SQL permite que `ORDER BY` as cláusulas `SELECT .. FROM .. WHERE` sejam especificadas apenas no bloco superior. Você [!INCLUDE[esql](../../../../../../includes/esql-md.md)] pode usar uma `ORDER BY` expressão aninhada e ela pode ser colocada em qualquer lugar da consulta, mas o pedido em uma consulta aninhada não é preservado.  
  
```sql  
-- The following query will order the results by the last name  
SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorks.Contact AS C1
        ORDER BY C1.LastName  
```  
  
```sql  
-- In the following query ordering of the nested query is ignored.  
SELECT C2.FirstName, C2.LastName  
    FROM (SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorks.Contact as C1  
        ORDER BY C1.LastName) as C2  
```  
  
## <a name="identifiers"></a>Identificadores  
 No Transact-SQL, a comparação de identificadores é baseada na colagem do banco de dados atual. Em [!INCLUDE[esql](../../../../../../includes/esql-md.md)], identificadores são sempre insensíveis e [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sensíveis ao sotaque (ou seja, distingue entre personagens acentuados e não acentuados; por exemplo, 'a' não é igual a ''' )."). [!INCLUDE[esql](../../../../../../includes/esql-md.md)] trata versões de letras que aparecem o mesmo mas é páginas diferentes de código como caracteres diferentes. Para obter mais informações, consulte [Input Character Set](input-character-set-entity-sql.md).  
  
## <a name="transact-sql-functionality-not-available-in-entity-sql"></a>Funcionalidade Transact-SQL não disponível em Entity SQL  
 A seguinte funcionalidade Transact-SQL não [!INCLUDE[esql](../../../../../../includes/esql-md.md)]está disponível em .  
  
 DML  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]atualmente, não oferece suporte para instruções DML (inserir, atualizar, excluir).  
  
 DDL  
 O [!INCLUDE[esql](../../../../../../includes/esql-md.md)] não oferece suporte para DDL na versão atual.  
  
 Programação imperativa  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]não fornece suporte para programação imperativa, ao contrário da Transact-SQL. Use, em vez disso, uma linguagem de programação.  
  
 Funções de agrupamento  
 O [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ainda não oferece suporte para funções de agrupamento (por exemplo, CUBE, ROLLUP e GROUPING_SET).  
  
 Funções Analíticas  
 O [!INCLUDE[esql](../../../../../../includes/esql-md.md)] (ainda) não oferece suporte para funções analíticas.  
  
 Funções internas, operadores  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]suporta um subconjunto de funções e operadores incorporados da Transact-SQL. Esses operadores e funções provavelmente têm suporte com os principais provedores de repositório. [!INCLUDE[esql](../../../../../../includes/esql-md.md)]usa as funções específicas da loja declaradas em um manifesto do provedor. Além disso, o Entity Framework permite que você declare funções de [!INCLUDE[esql](../../../../../../includes/esql-md.md)] armazenamento existentes incorporadas e definidas pelo usuário para uso.  
  
 Dicas  
 O [!INCLUDE[esql](../../../../../../includes/esql-md.md)] não oferece mecanismos para dicas de consulta.  
  
 Processando resultados de consulta em lotes  
 O [!INCLUDE[esql](../../../../../../includes/esql-md.md)] não oferece suporte a resultados de consulta em lotes. Por exemplo, o seguinte é transact-SQL válido (envio como um lote):  
  
```sql  
SELECT * FROM products;
SELECT * FROM catagories;
```  
  
 No entanto, a sintaxe [!INCLUDE[esql](../../../../../../includes/esql-md.md)] equivalente não tem suporte:  
  
```sql  
SELECT value p FROM Products AS p;
SELECT value c FROM Categories AS c;
```  
  
 O [!INCLUDE[esql](../../../../../../includes/esql-md.md)] oferece suporte a apenas uma instrução de consulta que gera resultado por comando.  
  
## <a name="see-also"></a>Confira também

- [Visão geral da Entity SQL](entity-sql-overview.md)
- [Expressões sem suporte](unsupported-expressions-entity-sql.md)
