---
title: Como o Entity SQL difere do Transact-SQL
ms.date: 03/30/2017
ms.assetid: 9c9ee36d-f294-4c8b-a196-f0114c94f559
ms.openlocfilehash: e0af0a415d812337d6abf449e9ee170526c3df0c
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/03/2019
ms.locfileid: "71833718"
---
# <a name="how-entity-sql-differs-from-transact-sql"></a>Como o Entity SQL difere do Transact-SQL
Este tópico descreve as diferenças entre [!INCLUDE[esql](../../../../../../includes/esql-md.md)] o e o Transact-SQL.  
  
## <a name="inheritance-and-relationships-support"></a>Suporte a herança e relações  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]funciona diretamente com esquemas de entidade conceitual e oferece suporte a recursos de modelo conceitual, como herança e relações.  
  
 Ao trabalhar com herança, geralmente é útil selecionar instâncias de um subtipo de uma coleção de instâncias de supertipo. O operador [OfType](oftype-entity-sql.md) em [!INCLUDE[esql](../../../../../../includes/esql-md.md)] (semelhante a `oftype` em C# sequences) fornece esse recurso.  
  
## <a name="support-for-collections"></a>Suporte para coleções  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]Trata as coleções como entidades de primeira classe. Por exemplo:  
  
- As expressões de coleção são válidas em uma cláusula `from`.  
  
- As subconsultas `in` e `exists` foram generalizadas para permitir quaisquer coleções.  
  
     Um subconsulta é um tipo de coleção. `e1 in e2` e `exists(e)` são as construções [!INCLUDE[esql](../../../../../../includes/esql-md.md)] para executar essas operações.  
  
- A operações de conjunto, como `union`, `intersect` e `except`, agora funcionam em coleções.  
  
- As junções funcionam em coleções.  
  
## <a name="support-for-expressions"></a>Suporte para expressões  
 O Transact-SQL tem subconsultas (tabelas) e expressões (linhas e colunas).  
  
 Para dar suporte a coleções e coleções [!INCLUDE[esql](../../../../../../includes/esql-md.md)] aninhadas, o transforma tudo em uma expressão. [!INCLUDE[esql](../../../../../../includes/esql-md.md)]é mais combinável do que o Transact-SQL – cada expressão pode ser usada em qualquer lugar. As expressões de consulta sempre resultam em coleções dos tipos projetados e podem ser usadas em qualquer lugar em que uma expressão de coleção seja permitida. Para obter informações sobre expressões Transact-SQL que não têm suporte [!INCLUDE[esql](../../../../../../includes/esql-md.md)]no, consulte [expressões sem suporte](unsupported-expressions-entity-sql.md).  
  
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
 Considerando sua ênfase em tabelas, o Transact-SQL executa a interpretação contextual de subconsultas. Por exemplo, uma subconsulta na `from` cláusula é considerada uma multiconjunto (tabela). Mas a mesma subconsulta usada na cláusula `select` é considerada uma subconsulta escalar. Da mesma forma, uma subconsulta usada no lado esquerdo de `in` um operador é considerada uma subconsulta escalar, enquanto o lado direito deve ser uma subconsulta multiconjunto.  
  
 O [!INCLUDE[esql](../../../../../../includes/esql-md.md)] elimina essas diferenças. Uma expressão tem uma interpretação uniforme que não depende do contexto no qual é usada. [!INCLUDE[esql](../../../../../../includes/esql-md.md)]considera que todas as subconsultas sejam subconsultas multiconjunto. Se for desejado um valor escalar da subconsulta, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] o fornecerá o `anyelement` operador que opera em uma coleção (nesse caso, a subconsulta) e extrairá um valor singleton da coleção.  
  
### <a name="avoiding-implicit-coercions-for-subqueries"></a>Evitando coerções implícitas para subconsultas  
 Um efeito colateral relacionado ao tratamento uniforme de subconsultas é a conversão implícita de subconsultas em valores escalares. Especificamente, no Transact-SQL, um multiconjunto de linhas (com um único campo) é implicitamente convertido em um valor escalar cujo tipo de dados é o do campo.  
  
 O [!INCLUDE[esql](../../../../../../includes/esql-md.md)] não oferece suporte a essa coerção implícita. O [!INCLUDE[esql](../../../../../../includes/esql-md.md)] fornece o operador de ANYELEMENT para extrair um valor singleton de uma coleção, e uma cláusula `select value` para evitar criar um wrapper de linha durante uma expressão de consulta.  
  
## <a name="select-value-avoiding-the-implicit-row-wrapper"></a>Selecione o valor: Evitando o wrapper de linha implícito  
 A cláusula SELECT em uma subconsulta Transact-SQL cria implicitamente um wrapper de linha em volta dos itens na cláusula. Isso indica que não podemos criar coleções de escalares ou objetos. O Transact-SQL permite uma coerção implícita entre um RowType com um campo e um valor singleton do mesmo tipo de dados.  
  
 O [!INCLUDE[esql](../../../../../../includes/esql-md.md)] fornece a cláusula `select value` para ignorar a construção de linha implícita. Somente um item pode ser especificado em uma cláusula `select value`. Quando tal cláusula é usada, nenhum wrapper de linha é construído ao redor dos itens na cláusula `select`, e uma coleção da forma desejada pode ser gerada, por exemplo: `select value a`.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] também fornece o construtor de linha para construir linhas arbitrárias. `select` utiliza um ou mais elementos da projeção e resulta em um registro de dados com campos, como a seguir:  
  
 `select a, b, c`  
  
## <a name="left-correlation-and-aliasing"></a>Correlação à esquerda e aliases  
 No Transact-SQL, as expressões em um determinado escopo (uma única cláusula `select` como `from`ou) não podem referenciar expressões definidas anteriormente no mesmo escopo. Alguns dialetos do SQL (incluindo Transact-SQL) dão suporte a `from` formas limitadas deles na cláusula.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]generaliza correlações à esquerda na `from` cláusula e as trata uniformemente. As expressões na cláusula `from` podem referenciar as definições anteriores (definições à esquerda) na mesma cláusula sem a necessidade de sintaxe adicional.  
  
 O [!INCLUDE[esql](../../../../../../includes/esql-md.md)] também impõe restrições adicionais em consultas que envolvem cláusulas `group by`. As expressões na `select` cláusula and `having` da cláusula dessas consultas só `group by` podem fazer referência às chaves por meio de seus aliases. A construção a seguir é válida no Transact-SQL, mas não [!INCLUDE[esql](../../../../../../includes/esql-md.md)]está em:  
  
```sql  
SELECT t.x + t.y FROM T AS t group BY t.x + t.y
```  
  
 Para fazer isso em [!INCLUDE[esql](../../../../../../includes/esql-md.md)]:  
  
```sql  
SELET k FROM T AS t GROUP BY (t.x + t.y) AS k
```  
  
## <a name="referencing-columns-properties-of-tables-collections"></a>Referenciando colunas (propriedades) de tabelas (coleções)  
 Todas as referências a colunas em [!INCLUDE[esql](../../../../../../includes/esql-md.md)] devem ser qualificadas com o alias de tabela. A construção a seguir (supondo que `a` seja uma coluna de tabela `T`válida) é válida no Transact-SQL, [!INCLUDE[esql](../../../../../../includes/esql-md.md)]mas não no.  
  
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
 O Transact-SQL usa a notação "." para fazer referência a colunas de (uma linha de) uma tabela. O [!INCLUDE[esql](../../../../../../includes/esql-md.md)] amplia essa notação (emprestada de linguagens de programação) para oferecer suporte à navegação pelas propriedades de um objeto.  
  
 Por exemplo, se `p` for uma expressão do tipo Pessoa, a sintaxe [!INCLUDE[esql](../../../../../../includes/esql-md.md)] a seguir fará referência à cidade do endereço dessa pessoa.  
  
```sql  
p.Address.City   
```  
  
## <a name="no-support-for-"></a>Nenhum suporte para *  
 O Transact-SQL dá suporte à sintaxe * não qualificada como um alias para a linha inteira e \* a sintaxe qualificada\*(t.) como um atalho para os campos dessa tabela. Além disso, o Transact-SQL permite uma agregação de\*contagem especial (), que inclui nulos.  
  
 O [!INCLUDE[esql](../../../../../../includes/esql-md.md)] não oferece suporte à construção *. Consultas Transact-SQL do formulário `select * from T` e `select T1.* from T1, T2...` podem ser expressas em [!INCLUDE[esql](../../../../../../includes/esql-md.md)] como `select value t from T as t` e `select value t1 from T1 as t1, T2 as t2...`, respectivamente. Além disso, essas construções manipulam a herança (substituibilidade do valor), embora as variantes `select *` sejam restritas a propriedades de nível superior do tipo declarado.  
  
 O [!INCLUDE[esql](../../../../../../includes/esql-md.md)] não oferece suporte à agregação `count(*)`. Use `count(0)` em seu lugar.  
  
## <a name="changes-to-group-by"></a>Alterações em group by  
 O [!INCLUDE[esql](../../../../../../includes/esql-md.md)] oferece suporte a aliases de chaves `group by`. As expressões na `select` cláusula e `having` `group by` cláusula devem se referir às chaves por meio desses aliases. Por exemplo, esta [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sintaxe:  
  
```sql  
SELECT k1, count(t.a), sum(t.a)
FROM T AS t
GROUP BY t.b + t.c AS k1
```  
  
 ... é equivalente ao Transact-SQL a seguir:  
  
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
O Transact-SQL permite que as cláusulas `ORDER BY` sejam especificadas somente no bloco de `SELECT .. FROM .. WHERE` superior. No [!INCLUDE[esql](../../../../../../includes/esql-md.md)], você pode usar uma expressão `ORDER BY` aninhada e ela pode ser colocada em qualquer lugar na consulta, mas a ordenação em uma consulta aninhada não é preservada.  
  
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
 No Transact-SQL, a comparação de identificador é baseada no agrupamento do banco de dados atual. No [!INCLUDE[esql](../../../../../../includes/esql-md.md)], os identificadores sempre diferenciam maiúsculas de minúsculas e diferenciam [!INCLUDE[esql](../../../../../../includes/esql-md.md)] acentos (ou seja, distingue entre caracteres acentuados e não acentuados; por exemplo, ' a ' não é igual a ' ã '). [!INCLUDE[esql](../../../../../../includes/esql-md.md)] trata versões de letras que aparecem o mesmo mas é páginas diferentes de código como caracteres diferentes. Para obter mais informações, consulte [conjunto de caracteres de entrada](input-character-set-entity-sql.md).  
  
## <a name="transact-sql-functionality-not-available-in-entity-sql"></a>Funcionalidade Transact-SQL não disponível em Entity SQL  
 A seguinte funcionalidade Transact-SQL não está disponível no [!INCLUDE[esql](../../../../../../includes/esql-md.md)].  
  
 DML  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]Atualmente, não fornece suporte para instruções DML (INSERT, Update e Delete).  
  
 DDL  
 O [!INCLUDE[esql](../../../../../../includes/esql-md.md)] não oferece suporte para DDL na versão atual.  
  
 Programação imperativa  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]não fornece suporte para programação imperativa, ao contrário do Transact-SQL. Use, em vez disso, uma linguagem de programação.  
  
 Funções de agrupamento  
 O [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ainda não oferece suporte para funções de agrupamento (por exemplo, CUBE, ROLLUP e GROUPING_SET).  
  
 Funções analíticas  
 O [!INCLUDE[esql](../../../../../../includes/esql-md.md)] (ainda) não oferece suporte para funções analíticas.  
  
 Funções internas, operadores  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]dá suporte a um subconjunto de funções e operadores internos do Transact-SQL. Esses operadores e funções provavelmente têm suporte com os principais provedores de repositório. [!INCLUDE[esql](../../../../../../includes/esql-md.md)]usa funções específicas do repositório declaradas em um manifesto do provedor. Além disso, o Entity Framework permite que você declare funções de armazenamento existentes internas e definidas pelo usuário para [!INCLUDE[esql](../../../../../../includes/esql-md.md)] usar o.  
  
 Dicas  
 O [!INCLUDE[esql](../../../../../../includes/esql-md.md)] não oferece mecanismos para dicas de consulta.  
  
 Processando resultados de consulta em lotes  
 O [!INCLUDE[esql](../../../../../../includes/esql-md.md)] não oferece suporte a resultados de consulta em lotes. Por exemplo, o seguinte é um Transact-SQL válido (envio como um lote):  
  
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
  
## <a name="see-also"></a>Consulte também

- [Visão geral do Entity SQL](entity-sql-overview.md)
- [Expressões sem suporte](unsupported-expressions-entity-sql.md)
