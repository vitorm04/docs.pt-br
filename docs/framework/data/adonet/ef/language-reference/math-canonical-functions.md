---
title: Funções canônicas matemáticas
ms.date: 03/30/2017
ms.assetid: 6f6cddc6-b561-4ebe-84b6-841ef5b4113b
ms.openlocfilehash: f575785bb198251ef50ba3563e736946253c9526
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59228764"
---
# <a name="math-canonical-functions"></a>Funções canônicas matemáticas

Entity SQL inclui as seguintes funções canônicas de matemáticas:
  
## <a name="absvalue"></a>Abs (valor)

Retorna o valor absoluto de `value`.

**Arguments**

Uma `Int16`, `Int32`, `Int64`, `Byte`, `Single`, `Double`, e `Decimal`.

**Valor de retorno**

O tipo de `value`.

**Exemplo**

`Abs(-2)`

## <a name="ceilingvalue"></a>Teto (valor)

Retorna o número inteiro o menor que não é menor que `value`.

**Arguments**

Um `Single`, `Double`, e `Decimal`.

**Valor de retorno**

O tipo de `value`.

**Exemplo**

[!code-csharp[DP EntityServices Concepts#EDM_CEILING](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_ceiling)]
[!code-sql[DP EntityServices Concepts#EDM_CEILING](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_ceiling)]

## <a name="floorvalue"></a>Andar (valor)

Retorna o número inteiro maior que não é maior do que `value`.

**Arguments**

Um `Single`, `Double`, e `Decimal`.

**Valor de retorno**

O tipo de `value`.

**Exemplo**

[!code-csharp[DP EntityServices Concepts#EDM_FLOOR](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_floor)]
[!code-sql[DP EntityServices Concepts#EDM_FLOOR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_floor)]

## <a name="powervalue-exponent"></a>Põe (valor, expoente)

Retorna o resultado de `value` especificado a `exponent`especificado.

**Arguments**

|  |  |
|--|--|
|`value` | Um `Int32, Int64, Double` ou `Decimal`. |
|`exponent` | Uma `Int64`, `Double`, ou `Decimal`. |

**Valor de retorno**

O tipo de `value`.

**Exemplo**

`Power(748.58,2)`

## <a name="roundvalue"></a>Redondo (valor)

Retorna a parte inteira de `value`, arredondada para o inteiro mais próximo.

**Arguments**

Um `Single`, `Double`, e `Decimal`.

**Valor de retorno**

O tipo de `value`.

**Exemplo**

`Round(748.58)`

## <a name="roundvalue-digits"></a>Redondo (valor, dígitos)

Retorna `value`, arredondado a `digits`especificado o mais próximo.

**Arguments**

|  |  |
|--|--|
|`value`|`Double` ou `Decimal`.|
|`digits`|`Int16` ou `Int32`.|

**Valor de retorno**

O tipo de `value`.

**Exemplo**

`Round(748.58,1)`

## <a name="truncatevalue-digits"></a>Truncar (valor, dígitos)

Retorna `value`, truncado a `digits`especificado o mais próximo.

**Arguments**

|  |  |
|--|--|
|`value`|`Double` ou `Decimal`.|
|`digits`|`Int16` ou `Int32`.|

**Valor de retorno**

O tipo de `value`.

**Exemplo**

`Truncate(748.58,1)`  
  
 Essas funções retornará `null` se entrada dada de `null` .  
  
 Funcionalidade equivalente está disponível no provedor gerenciado cliente do Microsoft SQL. Para obter mais informações, consulte [SqlClient para funções de Entity Framework](../../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md).  
  
## <a name="see-also"></a>Consulte também

- [Funções canônicas](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md)
