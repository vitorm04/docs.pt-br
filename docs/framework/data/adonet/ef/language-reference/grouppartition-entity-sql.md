---
title: PARTIÇÃODOGRUPO (Entity SQL)
ms.date: 03/30/2017
ms.assetid: d0482e9b-086c-451c-9dfa-ccb024a9efb6
ms.openlocfilehash: 9f0f917380e6422da753282216529580f87f1a1a
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32760902"
---
# <a name="grouppartition-entity-sql"></a>PARTIÇÃODOGRUPO (Entity SQL)
Retorna uma coleção de valores de argumento que são projetados fora do partição atual do grupo que a agregação está relacionada. A agregação de `GroupPartition` é uma agregação grupo- base e não tem nenhum formulário coleção com base.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
GROUPPARTITION( [ALL|DISTINCT] expression )  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Qualquer expressão de [!INCLUDE[esql](../../../../../../includes/esql-md.md)] .  
  
## <a name="remarks"></a>Comentários  
 A seguinte consulta gerencia uma lista de produtos e uma coleção de linha quantidades do pedido por cada produto:  
  
```  
select p, GroupPartition(ol.Quantity) from LOB.OrderLines as ol  
  group by ol.Product as p  
```  
  
 As duas consultas são iguais semanticamente:  
  
```  
select p, Sum(GroupPartition(ol.Quantity)) from LOB.OrderLines as ol  
  group by ol.Product as p  
select p, Sum(ol.Quantity) from LOB.OrderLines as ol  
  group by ol.Product as p  
```  
  
 O operador de `GROUPPARTITION` pode ser usado em conjunto com funções agregadas definidas pelo usuário.  
  
 `GROUPPARTITION` é um operador aggregate especial que contém uma referência ao conjunto agrupado de entrada. Essa referência pode ser usada em qualquer lugar na consulta onde o PERTO GRUPO está no escopo. Por exemplo,  
  
```  
select p, GroupPartition(ol.Quantity) from LOB.OrderLines as ol group by ol.Product as p  
```  
  
 Com um GRUPO normal PERTO, os resultados de agrupamento são ocultos. Você pode usar os resultados em uma função agregada. Para ver os resultados de agrupamento, você precisa correlacionar os resultados de agrupamento e de entrada definidos usando um subconsulta. As duas consultas são equivalentes:  
  
```  
select p, (select q from GroupPartition(ol.Quantity) as q) from LOB.OrderLines as ol group by ol.Product as p  
select p, (select ol.Quantity as q from LOB.OrderLines as ol2 where ol2.Product = p) from LOB.OrderLines as ol group by ol.Product as p  
```  
  
 Como mostrado no exemplo, o operador aggregate de GROUPPARTITION facilita obter uma referência a entrada definida após o agrupamento.  
  
 O operador GROUPPARTITION pode especificar qualquer [!INCLUDE[esql](../../../../../../includes/esql-md.md)] expressão no operador de entrada quando você usa o `expression` parâmetro.  
  
 Por exemplo todas as expressões da seguir de entrada a partição de grupo são válidas:  
  
```  
select groupkey, GroupPartition(b) from {1,2,3} as a inner join {4,5,6} as b on true group by a as groupkey  
select groupkey, GroupPartition(1) from {1,2,3} as a inner join {4,5,6} as b on true group by a as groupkey  
select groupkey, GroupPartition(a + b) from {1,2,3} as a inner join {4,5,6} as b on true group by a as groupkey  
select groupkey, GroupPartition({a + b}) from {1,2,3} as a inner join {4,5,6} as b on true group by a as groupkey  
select groupkey, GroupPartition({42}) from {1,2,3} as a inner join {4,5,6} as b on true group by a as groupkey  
select groupkey, GroupPartition(b > a) from {1,2,3} as a inner join {4,5,6} as b on true group by a as groupkey  
```  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como usar a cláusula de GROUPPARTITION com o cláusula GROUP BY. O cláusula GROUP BY agrupa entidades de `SalesOrderHeader` pelo seu `Contact`. A cláusula de GROUPPARTITION projetos na propriedade de `TotalDue` para cada grupo, resultando em uma coleção de decimais.  
  
 [!code-csharp[DP EntityServices Concepts 2#Collection_GroupPartition](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#collection_grouppartition)]
