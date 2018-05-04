---
title: Funções canônicas matemáticas
ms.date: 03/30/2017
ms.assetid: 6f6cddc6-b561-4ebe-84b6-841ef5b4113b
ms.openlocfilehash: 9d823eb45babca4b8f5dd717b4fb92c1984d1c8c
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="math-canonical-functions"></a>Funções canônicas matemáticas
[!INCLUDE[esql](../../../../../../includes/esql-md.md)] canônicas inclui funções matemáticas.  
  
 A seguinte tabela mostra a [!INCLUDE[esql](../../../../../../includes/esql-md.md)] funções matemáticas canônicas.  
  
|Função|Descrição|  
|--------------|-----------------|  
|`Abs(``value``)`|Retorna o valor absoluto de `value`.<br /><br /> **Argumentos**<br /><br /> Um `Int16`, `Int32`, `Int64`, `Byte`, `Single`, `Double`, e `Decimal`.<br /><br /> **Valor retornado**<br /><br /> O tipo de `value`.<br /><br /> **Exemplo**<br /><br /> `Abs(-2)`|  
|`Ceiling(``value``)`|Retorna o número inteiro o menor que não é menor que `value`.<br /><br /> **Argumentos**<br /><br /> Um `Single`, `Double`, e `Decimal`.<br /><br /> **Valor retornado**<br /><br /> O tipo de `value`.<br /><br /> **Exemplo**<br /><br /> [!code-csharp[DP EntityServices Concepts#EDM_CEILING](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_ceiling)]
 [!code-sql[DP EntityServices Concepts#EDM_CEILING](../../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_ceiling)]|  
|`Floor(``value``)`|Retorna o número inteiro maior que não é maior do que `value`.<br /><br /> **Argumentos**<br /><br /> Um `Single`, `Double`, e `Decimal`.<br /><br /> **Valor retornado**<br /><br /> O tipo de `value`.<br /><br /> **Exemplo**<br /><br /> [!code-csharp[DP EntityServices Concepts#EDM_FLOOR](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_floor)]
 [!code-sql[DP EntityServices Concepts#EDM_FLOOR](../../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_floor)]|  
|`Power(` `value`, `exponent``)`|Retorna o resultado de `value` especificado a `exponent`especificado.<br /><br /> **Argumentos**<br /><br /> `value`: Uma `Int32, Int64, Double`, ou `Decimal`.<br /><br /> `exponent`: Uma `Int64``, Double`, ou `Decimal`.<br /><br /> **Valor retornado**<br /><br /> O tipo de `value`.<br /><br /> **Exemplo**<br /><br /> `Power(748.58,2)`|  
|`Round(``value``)`|Retorna a parte inteira de `value`, arredondada para o inteiro mais próximo.<br /><br /> **Argumentos**<br /><br /> Um `Single`, `Double`, e `Decimal`.<br /><br /> **Valor retornado**<br /><br /> O tipo de `value`.<br /><br /> **Exemplo**<br /><br /> `Round(748.58)`|  
|`Round(` `value`, `digits``)`|Retorna `value`, arredondado a `digits`especificado o mais próximo.<br /><br /> **Argumentos**<br /><br /> `value`: `Double` ou `Decimal`.<br /><br /> `digits`: `Int16` ou `Int32`.<br /><br /> **Valor retornado**<br /><br /> O tipo de `value`.<br /><br /> **Exemplo**<br /><br /> `Round(748.58,1)`|  
|`Truncate(` `value`, `digits``)`|Retorna `value`, truncado a `digits`especificado o mais próximo.<br /><br /> **Argumentos**<br /><br /> `value`: `Double` ou `Decimal`.<br /><br /> `digits`: `Int16` ou `Int32`.<br /><br /> **Valor retornado**<br /><br /> O tipo de `value`.<br /><br /> **Exemplo**<br /><br /> `Truncate(748.58,1)`|  
  
 Essas funções retornará `null` se entrada dada de `null` .  
  
 Funcionalidade equivalente está disponível no provedor gerenciado cliente do Microsoft SQL. Para obter mais informações, consulte [SqlClient para funções de Entity Framework](../../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md).  
  
## <a name="see-also"></a>Consulte também  
 [Canonical Functions](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md) (Funções canônicas)
