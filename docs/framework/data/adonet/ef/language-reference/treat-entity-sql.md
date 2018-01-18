---
title: TRATAR (Entity SQL)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5b77f156-55de-4cb4-8154-87f707d4c635
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 65b5a67ffa910841d825adc729990d365ac50357
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/17/2018
---
# <a name="treat-entity-sql"></a>TRATAR (Entity SQL)
Trata um objeto de um tipo base específico como um objeto do tipo derivado especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
TREAT ( expression as type)  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Qualquer expressão de consulta válida que retorna uma entidade.  
  
> [!NOTE]
>  O tipo da expressão especificada deve ser um subtipo do tipo de dados especificado, ou o tipo de dados deve ser um subtipo do tipo da expressão.  
  
 `type`  
 Um tipo de objeto. O tipo deve ser qualificado por um namespace.  
  
> [!NOTE]
>  A expressão especificada deve ser um subtipo do tipo de dados especificado, ou o tipo de dados deve ser um subtipo da expressão.  
  
## <a name="return-value"></a>Valor de retorno  
 Um valor de tipo de dados especificado.  
  
## <a name="remarks"></a>Comentários  
 O DELEITE é usado para executar upcasting entre classes relacionadas. Por exemplo, se `Employee` deriva de `Person` e p é do tipo `Person`, upcasts de `TREAT(p AS NamespaceName.Employee)` uma instância genérica de `Person` a `Employee`; isto é, permite que você trate p como `Employee`.  
  
 O DELEITE é usado em cenários de herança onde você pode fazer uma consulta como o seguinte:  
  
```  
SELECT TREAT(p AS NamespaceName.Employee)  
FROM ContainerName.Person AS p  
WHERE p IS OF (NamespaceName.Employee)   
```  
  
 As entidades de `Person` de upcasts desta consulta a `Employee` tipo. Se o valor de p verdade não é do tipo `Employee`, a expressão produz o valor `null`.  
  
> [!NOTE]
>  A expressão especificada `Employee` deve ser um subtipo do tipo de dados especificado `Person`, ou o tipo de dados deve ser um subtipo da expressão. Caso contrário, a expressão resultará em um erro em tempo de compilação.  
  
 A tabela a seguir mostra o comportamento de tratam sobre alguns padrões típicos e alguns padrões menos comuns. Todas as exceções são geradas do lado do cliente antes que o provedor obtenha chamado:  
  
|Padrão|Comportamento|  
|-------------|--------------|  
|`TREAT (null AS EntityType)`|Retorna `DbNull`.|  
|`TREAT (null AS ComplexType)`|Gerencie uma exceção.|  
|`TREAT (null AS RowType)`|Gerencie uma exceção|  
|`TREAT (EntityType AS EntityType)`|Retorna `EntityType` ou `null`.|  
|`TREAT (ComplexType AS ComplexType)`|Gerencie uma exceção.|  
|`TREAT (RowType AS RowType)`|Gerencie uma exceção.|  
  
## <a name="example"></a>Exemplo  
 A seguinte consulta de [!INCLUDE[esql](../../../../../../includes/esql-md.md)] usa o operador de DELEITE para converter um objeto do traço de tipo a uma coleção de objetos do tipo OnsiteCourse. A consulta se baseia o [modelo School](http://msdn.microsoft.com/en-us/859a9587-81ea-4a45-9bc0-f8d330e1adac).  
  
 [!code-csharp[DP EntityServices Concepts 2#TREAT_ISOF](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#treat_isof)]  
  
## <a name="see-also"></a>Consulte também  
 [Referência de Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [Tipos estruturados anulável](../../../../../../docs/framework/data/adonet/ef/language-reference/nullable-structured-types-entity-sql.md)
