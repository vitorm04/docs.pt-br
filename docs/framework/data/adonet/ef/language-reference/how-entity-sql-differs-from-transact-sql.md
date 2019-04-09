---
title: Como o Entity SQL difere do Transact-SQL
ms.date: 03/30/2017
ms.assetid: 9c9ee36d-f294-4c8b-a196-f0114c94f559
ms.openlocfilehash: 75ce0b00962526b76ea9f4b9fdfb0d1e1e564cdc
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59162731"
---
# <a name="how-entity-sql-differs-from-transact-sql"></a>Como o Entity SQL difere do Transact-SQL
Este tópico descreve as diferenças entre [!INCLUDE[esql](../../../../../../includes/esql-md.md)] e [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)].  
  
## <a name="inheritance-and-relationships-support"></a>Suporte a herança e relações  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] trabalha diretamente com esquemas conceituais de entidade e dá suporte a recursos de modelo conceitual, como herança e relações.  
  
 Ao trabalhar com herança, geralmente é útil selecionar instâncias de um subtipo de uma coleção de instâncias de supertipo. O [oftype](../../../../../../docs/framework/data/adonet/ef/language-reference/oftype-entity-sql.md) operador na [!INCLUDE[esql](../../../../../../includes/esql-md.md)] (semelhante à `oftype` em C# sequências) fornece esse recurso.  
  
## <a name="support-for-collections"></a>Suporte para coleções  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] trata coleções como entidades de primeira classe. Por exemplo:  
  
-   As expressões de coleção são válidas em uma cláusula `from`.  
  
-   `in` e `exists` subconsultas foram generalizadas para permitir quaisquer coleções.  
  
     Um subconsulta é um tipo de coleção. `e1 in e2` e `exists(e)` são o [!INCLUDE[esql](../../../../../../includes/esql-md.md)] construções para executar essas operações.  
  
-   A operações de conjunto, como `union`, `intersect` e `except`, agora funcionam em coleções.  
  
-   As junções funcionam em coleções.  
  
## <a name="support-for-expressions"></a>Suporte para expressões  
 [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] tem subconsultas (tabelas) e expressões (linhas e colunas).  
  
 Para dar suporte a coleções e coleções aninhadas, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] transforma tudo em uma expressão. [!INCLUDE[esql](../../../../../../includes/esql-md.md)] é mais Combinável do que [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]— cada expressão pode ser usada em qualquer lugar. As expressões de consulta sempre resultam em coleções dos tipos projetados e podem ser usadas em qualquer lugar em que uma expressão de coleção seja permitida. Para obter informações sobre [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] expressões que não têm suporte no [!INCLUDE[esql](../../../../../../includes/esql-md.md)], consulte [expressões sem suporte](../../../../../../docs/framework/data/adonet/ef/language-reference/unsupported-expressions-entity-sql.md).  
  
 Os itens a seguir são todos consultas [!INCLUDE[esql](../../../../../../includes/esql-md.md)] válidas:  
  
```  
1+2 *3  
"abc"  
row(1 as a, 2 as b)  
{ 1, 3, 5}   
e1 union all e2  
set(e1)  
```  
  
## <a name="uniform-treatment-of-subqueries"></a>Tratamento uniforme de subconsultas  
 Dada a sua ênfase em tabelas, [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] realiza a interpretação contextual de subconsultas. Por exemplo, uma subconsulta no `from` cláusula é considerada um multiset (tabela). Mas a mesma subconsulta usada na cláusula `select` é considerada uma subconsulta escalar. Da mesma forma, uma subconsulta usada no lado esquerdo de uma `in` operador é considerado uma subconsulta escalar, enquanto o lado direito deve ser uma subconsulta multiset.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] elimina essas diferenças. Uma expressão tem uma interpretação uniforme que não depende do contexto no qual é usada. [!INCLUDE[esql](../../../../../../includes/esql-md.md)] considera todas as subconsultas multiset subconsultas. Se desejar um valor escalar da subconsulta, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] fornece o `anyelement` operador que opera em uma coleção (neste caso, a subconsulta) e extrai um valor singleton da coleção.  
  
### <a name="avoiding-implicit-coercions-for-subqueries"></a>Evitando coerções implícitas para subconsultas  
 Um efeito colateral relacionado ao tratamento uniforme de subconsultas é a conversão implícita de subconsultas em valores escalares. Especificamente, no [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)], um multiset de linhas (com um único campo) é convertido implicitamente em um valor escalar cujo tipo de dados é o do campo.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] não oferece suporte a essa coerção implícita. [!INCLUDE[esql](../../../../../../includes/esql-md.md)] fornece o operador de ANYELEMENT para extrair um valor singleton de uma coleção e um `select value` cláusula para evitar a criação de um wrapper de linha durante uma expressão de consulta.  
  
## <a name="select-value-avoiding-the-implicit-row-wrapper"></a>Selecione valor: Evitando o Wrapper de linha implícito  
 A cláusula select em uma [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] subconsulta cria implicitamente um wrapper de linha ao redor dos itens na cláusula. Isso indica que não podemos criar coleções de escalares ou objetos. [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] permite uma coerção implícita entre um rowtype com um campo e um valor singleton do mesmo tipo de dados.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] fornece o `select value` cláusula para ignorar a construção de linha implícita. Somente um item pode ser especificado em uma cláusula `select value`. Quando tal cláusula é usada, nenhum wrapper de linha é construído ao redor dos itens na cláusula `select`, e uma coleção da forma desejada pode ser gerada, por exemplo: `select value a`.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] também fornece o construtor de linhas para construir linhas arbitrárias. `select` utiliza um ou mais elementos na projeção e resulta em um registro de dados com campos, da seguinte maneira:  
  
 `select a, b, c`  
  
## <a name="left-correlation-and-aliasing"></a>Correlação à esquerda e aliases  
 No [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)], as expressões em um determinado escopo (uma cláusula única, como `select` ou `from`) não podem referenciar expressões definidas anteriormente no mesmo escopo. Alguns dialetos do SQL (incluindo [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]) oferecem suporte a formas limitadas delas na cláusula `from`.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] generaliza as correlações à esquerda no `from` cláusula e trata-as uniformemente. As expressões na cláusula `from` podem referenciar as definições anteriores (definições à esquerda) na mesma cláusula sem a necessidade de sintaxe adicional.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] também impõe restrições adicionais em consultas que envolvem `group by` cláusulas. Expressões na `select` cláusula e `having` só pode se referir a cláusula de tais consultas para o `group by` chaves através de seus aliases. A construção a seguir é válida em [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] , mas não em [!INCLUDE[esql](../../../../../../includes/esql-md.md)]:  
  
```  
select t.x + t.y from T as t group by t.x + t.y  
```  
  
 Para fazer isso em [!INCLUDE[esql](../../../../../../includes/esql-md.md)]:  
  
```  
select k from T as t group by (t.x + t.y) as k  
```  
  
## <a name="referencing-columns-properties-of-tables-collections"></a>Referenciando colunas (propriedades) de tabelas (coleções)  
 Todas as referências a colunas em [!INCLUDE[esql](../../../../../../includes/esql-md.md)] devem ser qualificadas com o alias de tabela. A construção a seguir (supondo que `a` é uma coluna válida da tabela `T`) é válida em [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] , mas não no [!INCLUDE[esql](../../../../../../includes/esql-md.md)].  
  
```  
select a from T  
```  
  
 A forma em [!INCLUDE[esql](../../../../../../includes/esql-md.md)] é  
  
```  
select t.a as A from T as t  
```  
  
 Os aliases de tabela são opcionais na cláusula `from`. O nome da tabela é usado como o alias implícito. [!INCLUDE[esql](../../../../../../includes/esql-md.md)] permite que o seguinte formato:  
  
```  
select Tab.a from Tab  
```  
  
## <a name="navigation-through-objects"></a>Navegação por objetos  
 [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] usa o "." notação para referenciar colunas de (uma linha de) uma tabela. [!INCLUDE[esql](../../../../../../includes/esql-md.md)] amplia essa notação (emprestada de linguagens de programação) para dar suporte à navegação por meio das propriedades de um objeto.  
  
 Por exemplo, se `p` for uma expressão do tipo Pessoa, a sintaxe [!INCLUDE[esql](../../../../../../includes/esql-md.md)] a seguir fará referência à cidade do endereço dessa pessoa.  
  
```  
p.Address.City   
```  
  
## <a name="no-support-for-"></a>Nenhum suporte para *  
 [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] dá suporte a não qualificada * sintaxe como um alias para a linha inteira e o qualificado \* sintaxe (t.\*) como um atalho para os campos dessa tabela. Além disso, [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] permite que uma conta especial (\*) agregação, que inclui valores nulos.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] não oferece suporte a * constructo. [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] consultas do formulário `select * from T` e `select T1.* from T1, T2...` pode ser expresso em [!INCLUDE[esql](../../../../../../includes/esql-md.md)] como `select value t from T as t` e `select value t1 from T1 as t1, T2 as t2...`, respectivamente. Além disso, essas construções manipulam a herança (substituibilidade do valor), embora as variantes `select *` sejam restritas a propriedades de nível superior do tipo declarado.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] não oferece suporte a `count(*)` agregada. Use `count(0)` em seu lugar.  
  
## <a name="changes-to-group-by"></a>Alterações em group by  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] oferece suporte a aliases de `group by` chaves. Expressões na `select` cláusula e `having` cláusula deve se referir ao `group by` as chaves por meio desses aliases. Por exemplo, isso [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sintaxe:  
  
```  
select k1, count(t.a), sum(t.a)  
from T as t  
group by t.b + t.c as k1  
```  
  
 ...é equivalente à seguinte sintaxe [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]:  
  
```  
select b + c, count(*), sum(a)   
from T  
group by b + c  
```  
  
## <a name="collection-based-aggregates"></a>Agregações baseadas em coleção  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] dá suporte a dois tipos de agregações.  
  
 As agregações baseadas em coleção operam em coleções e geram o resultado agregado. Elas podem aparecer em qualquer lugar na consulta, e não requerem uma cláusula `group by`. Por exemplo:  
  
```  
select t.a as a, count({1,2,3}) as b from T as t     
```  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] também dá suporte a agregações do tipo SQL. Por exemplo:  
  
```  
select a, sum(t.b) from T as t group by t.a as a  
```  
  
## <a name="order-by-clause-usage"></a>Uso da cláusula ORDER BY  
 [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] permite que cláusulas ORDER BY seja especificada somente no nível mais alto, selecione... DE.. WHERE mais alto. No [!INCLUDE[esql](../../../../../../includes/esql-md.md)], você pode usar uma expressão ORDER BY aninhada e ela pode ser colocada em qualquer lugar na consulta, mas a ordenação em uma consulta aninhada não é preservada.  
  
```  
-- The following query will order the results by the last name  
SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorks.Contact as C1  
        ORDER BY C1.LastName  
```  
  
```  
-- In the following query ordering of the nested query is ignored.  
SELECT C2.FirstName, C2.LastName  
    FROM (SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorks.Contact as C1  
        ORDER BY C1.LastName) as C2  
```  
  
## <a name="identifiers"></a>Identificadores  
 No [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)], a comparação de identificadores é baseada na ordenação do banco de dados atual. Na [!INCLUDE[esql](../../../../../../includes/esql-md.md)], identificadores sempre diferenciam maiusculas de minúsculas e diferencia acento (ou seja, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] faz distinção entre caracteres acentuados e não acentuados; 'por exemplo, a' não é igual a 'ã'). [!INCLUDE[esql](../../../../../../includes/esql-md.md)] trata versões de letras que aparecem o mesmo, mas são diferentes das páginas de código como caracteres diferentes. Para obter mais informações, consulte [conjunto de caracteres de entrada](../../../../../../docs/framework/data/adonet/ef/language-reference/input-character-set-entity-sql.md).  
  
## <a name="transact-sql-functionality-not-available-in-entity-sql"></a>Funcionalidade Transact-SQL não disponível em Entity SQL  
 A funcionalidade [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] a seguir não está disponível em [!INCLUDE[esql](../../../../../../includes/esql-md.md)].  
  
 DML  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] no momento não oferece suporte para instruções DML (Inserir, atualizar e excluir).  
  
 DDL  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] não oferece suporte para DDL na versão atual.  
  
 Programação imperativa  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] não oferece suporte para programação imperativa, ao contrário de [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]. Use, em vez disso, uma linguagem de programação.  
  
 Funções de agrupamento  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ainda não fornece suporte para o agrupamento de funções (por exemplo, CUBE, ROLLUP e GROUPING_SET).  
  
 Funções analíticas  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] não (ainda) fornecem suporte para funções analíticas.  
  
 Funções internas, operadores  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] dá suporte a um subconjunto de [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]for compilado em funções e operadores. Esses operadores e funções provavelmente têm suporte com os principais provedores de repositório. [!INCLUDE[esql](../../../../../../includes/esql-md.md)] usa as funções de store específicas declaradas em um manifesto do provedor. Além disso, o [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] permite que você declare internas e funções definidas pelo usuário existente de repositório para [!INCLUDE[esql](../../../../../../includes/esql-md.md)] usar.  
  
 Dicas  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] não fornece mecanismos para dicas de consulta.  
  
 Processando resultados de consulta em lotes  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] não dá suporte a envio em lote os resultados da consulta. Por exemplo, o seguinte é válido [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] (enviando como um lote):  
  
```  
select * from products;  
select * from catagories;  
```  
  
 No entanto, a sintaxe [!INCLUDE[esql](../../../../../../includes/esql-md.md)] equivalente não tem suporte:  
  
```  
Select value p from Products as p;  
Select value c from Categories as c;  
```  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] dá suporte apenas a uma instrução de consulta gera resultado por comando.  
  
## <a name="see-also"></a>Consulte também

- [Visão geral da Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
- [Expressões sem suporte](../../../../../../docs/framework/data/adonet/ef/language-reference/unsupported-expressions-entity-sql.md)
