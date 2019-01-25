---
title: Referência rápida de Entity SQL
ms.date: 03/30/2017
ms.assetid: e53dad9e-5e83-426e-abb4-be3e78e3d6dc
ms.openlocfilehash: 20d8d1cb1e4b5cbf37dffcce6a7e79c2a4c265d3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54539397"
---
# <a name="entity-sql-quick-reference"></a>Referência rápida de Entity SQL
Este tópico fornece uma referência rápida às consultas de [!INCLUDE[esql](../../../../../../includes/esql-md.md)]. As consultas neste tópico baseiam-se no modelo de vendas AdventureWorks.  
  
## <a name="literals"></a>Literais  
  
### <a name="string"></a>Cadeia de Caracteres  
 Há literais de cadeia de caracteres Unicode e não Unicode. Cadeias de caracteres Unicode são pré-demarcadas com N. Por exemplo, `N'hello'`.  
  
 Este é um exemplo de um literal de cadeia de caracteres não Unicode:  
  
```  
'hello'  
--same as  
"hello"  
```  
  
 Saída:  
  
|Valor|  
|-----------|  
|hello|  
  
### <a name="datetime"></a>DateTime  
 Em literais DateTime, as partes de data e hora são obrigatórias. Não há valor padrão.  
  
 Exemplo:  
  
```  
DATETIME '2006-12-25 01:01:00.000'   
--same as  
DATETIME '2006-12-25 01:01'  
```  
  
 Saída:  
  
|Valor|  
|-----------|  
|12/25/2006 1:01:00 AM|  
  
### <a name="integer"></a>Inteiro  
 Literais inteiros podem ser do tipo Int32 (123), UInt32 (123U), Int64 (123L) e UInt64 (123UL).  
  
 Exemplo:  
  
```  
--a collection of integers  
{1, 2, 3}  
```  
  
 Saída:  
  
|Valor|  
|-----------|  
|1|  
|2|  
|3|  
  
### <a name="other"></a>Outros  
 Outros literais com suporte do [!INCLUDE[esql](../../../../../../includes/esql-md.md)] são Guid, Binary, Float/Double, Decimal e `null`. Literais nulos em [!INCLUDE[esql](../../../../../../includes/esql-md.md)] são considerados compatíveis com cada outro tipo no modelo conceitual.  
  
## <a name="type-constructors"></a>Construtores de tipo  
  
### <a name="row"></a>ROW  
 [LINHA](../../../../../../docs/framework/data/adonet/ef/language-reference/row-entity-sql.md) constrói um valor (registro) anônimo, tipado estruturalmente como em: `ROW(1 AS myNumber, ‘Name’ AS myName).`  
  
 Exemplo:  
  
```  
SELECT VALUE row (product.ProductID as ProductID, product.Name   
    as ProductName) FROM AdventureWorksEntities.Product AS product  
```  
  
 Saída:  
  
|ProductID|Nome|  
|---------------|----------|  
|1|Adjustable Race|  
|879|All-Purpose Bike Stand|  
|712|AWC Logo Cap|  
|...|...|  
  
### <a name="multiset"></a>MULTISET  
 [MULTISET](../../../../../../docs/framework/data/adonet/ef/language-reference/multiset-entity-sql.md) constrói coleções, tais como:  
  
 `MULTISET(1,2,2,3)` `--same as`-`{1,2,2,3}.`  
  
 Exemplo:  
  
```  
SELECT VALUE product FROM AdventureWorksEntities.Product AS product WHERE product.ListPrice IN MultiSet (125, 300)  
```  
  
 Saída:  
  
|ProductID|Nome|ProductNumber|…|  
|---------------|----------|-------------------|-------|  
|842|Touring-Panniers, Large|PA-T100|…|  
  
### <a name="object"></a>Objeto  
 [Chamada de construtor do tipo](../../../../../../docs/framework/data/adonet/ef/language-reference/named-type-constructor-entity-sql.md) constrói objetos definidos pelo usuário (nomeados), como `person("abc", 12)`.  
  
 Exemplo:  
  
```  
SELECT VALUE AdventureWorksModel.SalesOrderDetail (o.SalesOrderDetailID, o.CarrierTrackingNumber, o.OrderQty,   
o.ProductID, o.SpecialOfferID, o.UnitPrice, o.UnitPriceDiscount,   
o.rowguid, o.ModifiedDate) FROM AdventureWorksEntities.SalesOrderDetail   
AS o  
```  
  
 Saída:  
  
|SalesOrderDetailID|CarrierTrackingNumber|OrderQty|ProductID|...|  
|------------------------|---------------------------|--------------|---------------|---------|  
|1|4911-403C-98|1|776|...|  
|2|4911-403C-98|3|777|...|  
|...|...|...|...|...|  
  
## <a name="references"></a>Referências  
  
### <a name="ref"></a>REF  
 [REF](../../../../../../docs/framework/data/adonet/ef/language-reference/ref-entity-sql.md) cria uma referência a uma instância do tipo de entidade. Por exemplo, a seguinte consulta retorna referências para cada entidade Order no conjunto de entidades Orders:  
  
```  
SELECT REF(o) AS OrderID FROM Orders AS o  
```  
  
 Saída:  
  
|Valor|  
|-----------|  
|1|  
|2|  
|3|  
|...|  
  
 O exemplo a seguir usa o operador de extração de propriedade (.) para acessar uma propriedade de uma entidade. Quando o operador de extração de propriedade é usado, a referência é cancelada automaticamente.  
  
 Exemplo:  
  
```  
SELECT VALUE REF(p).Name FROM   
    AdventureWorksEntities.Product as p  
```  
  
 Saída:  
  
|Valor|  
|-----------|  
|Adjustable Race|  
|All-Purpose Bike Stand|  
|AWC Logo Cap|  
|...|  
  
### <a name="deref"></a>DEREF  
 [DEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/deref-entity-sql.md) desreferencia um valor de referência e gera o resultado dessa desreferência. Por exemplo, a seguinte consulta gera as entidades Order para cada Order no conjunto de entidades Orders: `SELECT DEREF(o2.r) FROM (SELECT REF(o) AS r FROM LOB.Orders AS o) AS o2`.  
  
 Exemplo:  
  
```  
SELECT VALUE DEREF(REF(p)).Name FROM   
    AdventureWorksEntities.Product as p  
```  
  
 Saída:  
  
|Valor|  
|-----------|  
|Adjustable Race|  
|All-Purpose Bike Stand|  
|AWC Logo Cap|  
|...|  
  
### <a name="createref-and-key"></a>CREATEREF AND KEY  
 [CREATEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/createref-entity-sql.md) cria uma referência passando uma chave. [CHAVE](../../../../../../docs/framework/data/adonet/ef/language-reference/key-entity-sql.md) extrai a parte da chave de uma expressão com referência de tipo.  
  
 Exemplo:  
  
```  
SELECT VALUE Key(CreateRef(AdventureWorksEntities.Product, row(p.ProductID)))   
    FROM AdventureWorksEntities.Product as p  
```  
  
 Saída:  
  
|ProductID|  
|---------------|  
|980|  
|365|  
|771|  
|...|  
  
## <a name="functions"></a>Funções  
  
### <a name="canonical"></a>Canônica  
 O namespace [funções canônicas](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md) é o Edm, como em `Edm.Length("string")`. Você não precisa especificar o namespace, a menos que outro namespace seja importado e contenha uma função com o mesmo nome de uma função canônica. Se dois namespaces têm a mesma função, o usuário deve especificar o nome completo.  
  
 Exemplo:  
  
```  
SELECT Length(c. FirstName) As NameLen FROM   
    AdventureWorksEntities.Contact AS c   
    WHERE c.ContactID BETWEEN 10 AND 12  
```  
  
 Saída:  
  
|NameLen|  
|-------------|  
|6|  
|6|  
|5|  
  
### <a name="microsoft-provider-specific"></a>Específico do provedor da Microsoft  
 [Funções específicas do provedor da Microsoft](../../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md) estão no `SqlServer` namespace.  
  
 Exemplo:  
  
```  
SELECT SqlServer.LEN(c.EmailAddress) As EmailLen FROM   
    AdventureWorksEntities.Contact AS c WHERE   
    c.ContactID BETWEEN 10 AND 12  
```  
  
 Saída:  
  
|EmailLen|  
|--------------|  
|27|  
|27|  
|26|  
  
## <a name="namespaces"></a>Namespaces  
 [USANDO](../../../../../../docs/framework/data/adonet/ef/language-reference/using-entity-sql.md) Especifica namespaces usados em uma expressão de consulta.  
  
 Exemplo:  
  
```  
using SqlServer; LOWER('AA');  
```  
  
 Saída:  
  
|Valor|  
|-----------|  
|aa|  
  
## <a name="paging"></a>Paginação  
 Paginação pode ser expressa declarando uma [SKIP](../../../../../../docs/framework/data/adonet/ef/language-reference/skip-entity-sql.md) e [limite](../../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md) subcláusulas para o [ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md) cláusula.  
  
 Exemplo:  
  
```  
SELECT c.ContactID as ID, c.LastName as Name FROM   
    AdventureWorks.Contact AS c ORDER BY c.ContactID SKIP 9 LIMIT 3;  
```  
  
 Saída:  
  
|ID|Nome|  
|--------|----------|  
|10|Adina|  
|11|Agcaoili|  
|12|Aguilar|  
  
## <a name="grouping"></a>Agrupamento  
 [Agrupar por](../../../../../../docs/framework/data/adonet/ef/language-reference/group-by-entity-sql.md) Especifica os grupos nos quais os objetos retornados por uma consulta ([selecione](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md)) expressão devem ser colocados.  
  
 Exemplo:  
  
```  
SELECT VALUE name FROM AdventureWorksEntities.Product as P   
    GROUP BY P.Name HAVING MAX(P.ListPrice) > 5  
```  
  
 Saída:  
  
|name|  
|----------|  
|LL Mountain Seat Assembly|  
|ML Mountain Seat Assembly|  
|HL Mountain Seat Assembly|  
|...|  
  
## <a name="navigation"></a>Navegação  
 O operador de navegação de relação permite que você navegue na relação de uma entidade (from end) para outra (to end). [NAVIGATE](../../../../../../docs/framework/data/adonet/ef/language-reference/navigate-entity-sql.md) usa o tipo de relação qualificado como \<namespace >.\< nome do tipo de relação >. Navegue retorna Ref\<T > se a cardinalidade de to end é 1. Se a cardinalidade de to end for n, a coleção < Ref\<T >> será retornado.  
  
 Exemplo:  
  
```  
SELECT a.AddressID, (SELECT VALUE DEREF(v) FROM   
    NAVIGATE(a, AdventureWorksModel.FK_SalesOrderHeader_Address_BillToAddressID) AS v)   
    FROM AdventureWorksEntities.Address AS a  
```  
  
 Saída:  
  
|AddressID|  
|---------------|  
|1|  
|2|  
|3|  
|...|  
  
## <a name="select-value-and-select"></a>SELECT VALUE AND SELECT  
  
### <a name="select-value"></a>SELECT VALUE  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] fornece a cláusula SELECT VALUE para ignorar a construção de linha implícita. Somente um item pode ser especificado em uma cláusula SELECT VALUE. Quando tal cláusula é usada, nenhum wrapper de linha é construído ao redor dos itens na cláusula SELECT e pode de uma coleção da forma desejada ser gerada, por exemplo: `SELECT VALUE a`.  
  
 Exemplo:  
  
```  
SELECT VALUE p.Name FROM AdventureWorksEntities.Product as p  
```  
  
 Saída:  
  
|Nome|  
|----------|  
|Adjustable Race|  
|All-Purpose Bike Stand|  
|AWC Logo Cap|  
|...|  
  
### <a name="select"></a>SELECT  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] também fornece o construtor de linha para construir linhas arbitrárias. SELECT utiliza um ou mais elementos na projeção e resulta em um registro de dados com campos; por exemplo: `SELECT a, b, c`.  
  
 Exemplo:  
  
 SELECT p.Name, p.ProductID FROM AdventureWorksEntities.Product as p Output:  
  
|Nome|ProductID|  
|----------|---------------|  
|Adjustable Race|1|  
|All-Purpose Bike Stand|879|  
|AWC Logo Cap|712|  
|...|...|  
  
## <a name="case-expression"></a>CASE EXPRESSION  
 O [caso a expressão](../../../../../../docs/framework/data/adonet/ef/language-reference/case-entity-sql.md) avalia um conjunto de expressões Boolianas para determinar o resultado.  
  
 Exemplo:  
  
```  
CASE WHEN AVG({25,12,11}) < 100 THEN TRUE ELSE FALSE END  
```  
  
 Saída:  
  
|Valor|  
|-----------|  
|TRUE|  
  
## <a name="see-also"></a>Consulte também
- [Referência de Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [Visão geral do Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
