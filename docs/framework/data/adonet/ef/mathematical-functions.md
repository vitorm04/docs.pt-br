---
title: Funções matemáticas
ms.date: 03/30/2017
ms.assetid: b040c7cb-156d-40f2-9152-61065b18148c
ms.openlocfilehash: e6c58d781d7138f8295f2d0a2f0db110ad4b1dd6
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2018
ms.locfileid: "46697874"
---
# <a name="mathematical-functions"></a>Funções matemáticas

O provedor de dados. NET Framework para SQL Server (SqlClient) fornece as funções matemáticas que executam cálculos nos valores de entrada que são fornecidos como argumentos, e retorna um resultado de valor numérico. Essas funções estão no namespace SqlServer, que está disponível quando você usa o SqlClient. A propriedade de namespace de um provedor permite que Entity Framework descobrir que prefixo é usado por esse provedor para compilações específicas, como tipos e funções. A tabela a seguir descreve as funções matemáticas SqlClient.  
  
## <a name="absexpression"></a>Abs(Expression)

Executa a função de valor absoluto.

**Argumentos**

`expression`: Uma `Int32`, `Int64`, `Double`, ou `Decimal`.

**Valor retornado**

O valor absoluto de expressão especificada.

**Exemplo**

`SqlServer.ABS(-2)`

## <a name="acosexpression"></a>ACOS(Expression)

Retorna o valor de arccosine de expressão especificada.

**Argumentos**

`expression`: `Double`.

**Valor retornado**

Um `Double`.

**Exemplo**

`SqlServer.ACOS(.9)`

## <a name="asinexpression"></a>ASIN(Expression)

Retorna o valor de arcsine de expressão especificada.

**Argumentos**

`expression`: `Double`.

**Valor retornado**

Um `Double`.

**Exemplo**

`SqlServer.ASIN(.9)`

## <a name="atanexpression"></a>ATAN(Expression)

Retorna o valor de arctangent de expressão numérica especificada.

**Argumentos**

`expression`: `Double`.

**Valor retornado**

Um `Double`.

**Exemplo**

`SqlServer.ATAN(9)`

## <a name="atn2expression-expression"></a>ATN2(Expression, Expression)

Retorna o ângulo, em radianos, cuja tangente é entre as duas expressões numéricas especificadas.

**Argumentos**

`expression`: `Double`.

**Valor retornado**

Um `Double`.

**Exemplo**

`SqlServer.ATN2(9, 8)`
 
## <a name="ceilingexpression"></a>CEILING(Expression)

Converte a expressão especificada para o inteiro menor que é maior ou igual a ele.

**Argumentos**

`expression`: Uma `Int32`, `Int64`, `Double`, ou `Decimal`.

**Valor retornado**

Uma `Int32`, `Int64`, `Double`, ou `Decimal`.

**Exemplo** 

[!code-csharp[DP EntityServices Concepts#SQLSERVER_CEILING](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_ceiling)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_CEILING](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_ceiling)]

## <a name="cosexpression"></a>CoS(Expression)

Calcula o cosseno trigonométricas do ângulo especificado em radianos. 

**Argumentos** 

`expression`: `Double`. 

**Valor retornado** 

Um `Double`. 

**Exemplo** 

`SqlServer.COS(45)`

## <a name="cotexpression"></a>COT(Expression)

Calcula o cotangente trigonométricas do ângulo especificado em radianos. 

**Argumentos** 

`expression`: `Double`. 

**Valor retornado** 

Um `Double`. 

**Exemplo** 

`SqlServer.COT(60)`
  
## <a name="degreesradians"></a>DEGREES(radians)

Retorna o ângulo correspondente em graus. 

**Argumentos** 

`expression`: Uma `Int32`, `Int64`, `Double`, ou `Decimal`. 

**Valor retornado** 

Uma `Int32`, `Int64`, `Double`, ou `Decimal`. 

**Exemplo** 

`SqlServer.DEGREES(3.1)`

## <a name="expexpression"></a>EXP(Expression)

Calcula o valor exponencialmente de uma expressão numérica especificada. 

**Argumentos** 

`expression`: `Double`. 

**Valor retornado** 

Um `Double`. 

**Exemplo** `SqlServer.EXP(1)`

## <a name="floorexpression"></a>Floor(Expression)

Converte a expressão especificada para o inteiro maior menor ou igual a ele. 

**Argumentos** 

`expression`: `Double`. 

**Valor retornado** 

Um `Double`. 

**Exemplo** 

[!code-csharp[DP EntityServices Concepts#SQLSERVER_FLOOR](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_floor)] 
[!code-sql[DP EntityServices Concepts#SQLSERVER_FLOOR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_floor)]

## <a name="logexpression"></a>LOG(Expression)

Calcula o logaritmo natural da expressão especificada de `float` . 

**Argumentos** 

`expression`: `Double`. 

**Valor retornado** 

Um `Double`. 

**Exemplo** 

`SqlServer.LOG(100)`

## <a name="log10expression"></a>LOG10(Expression)

Retorna o logaritmo base-10 de expressão especificada de `Double` . 

**Argumentos** 

`expression`: `Double`. 

**Valor retornado** 

Um `Double`. 

**Exemplo** 

`SqlServer.LOG10(100)`

## <a name="pi"></a>PI)

Retorna o valor constante de pi como `Double`. 

**Valor retornado** 

Um `Double`. 

**Exemplo** 

`SqlServer.PI()`

## <a name="powernumericexpression-powerexpression"></a>POWER (numeric_expression, power_expression)

Calcula o valor de uma expressão especificada em uma potência especificada.

**Argumentos** 

|  |  |
|--|--|
|`numeric_expression`| Uma `Int32`, `Int64`, `Double`, ou `Decimal`.|
|`power_expression`| Um `Double` que representa a potência à qual elevar o `numeric_expression`.| 

**Valor retornado** 

O valor de `numeric_expression` especificado a `power_expression`especificado. 

**Exemplo** 

`SqlServer.POWER(2,7)`

## <a name="radiansexpression"></a>RADIANS(Expression)

Converte graus a radianos. 

**Argumentos** 

`expression`: Uma `Int32`, `Int64`, `Double`, ou `Decimal`. 

**Valor retornado** 

Uma `Int32`, `Int64`, `Double`, ou `Decimal`. 

**Exemplo** 

`SqlServer.RADIANS(360.0)`

## <a name="randseed"></a>RAND([Seed])

Retorna um valor aleatório de 0 a 1. 

**Argumentos** 

O valor de semente como um `Int32`. Se a semente não for especificada, o mecanismo de base de dados SQL Server atribui um valor semente aleatoriamente. Para um valor semente especificado, o resultado retornado é sempre o mesmo.

**Valor retornado** 

Um valor aleatório de 0 a 1. de `Double` . 

**Exemplo** 

`SqlServer.RAND()`
  
## <a name="roundnumericexpression-lengthfunction"></a>Round(Numeric_Expression, Length[,Function])

Retorna uma expressão numérica, arredondada para o comprimento ou a precisão especificada. 

**Argumentos** 

|  |  |
|--|--|
|`numeric_expression`| Uma `Int32`, `Int64`, `Double`, ou `Decimal`. 
|`length`| Uma `Int32` que representa a precisão para o qual `numeric_expression` deve ser arredondada. Quando `length` é um número positivo, `numeric_expression` ele é arredondado para o número de posições decimais especificadas por `length`. Quando `length` é um número negativo, `numeric_expression` é arredondado no lado esquerdo do ponto decimal, como especificado por `length`.|
|`function` | Opcional. Um `Int32` que representa o tipo de operação a ser executada. Quando a função for omitida ou tem um valor de 0 (padrão), `numeric_expression` é arredondado. Quando um valor diferente de 0 for especificado, `numeric_expression` será truncado. |

**Valor retornado** 

O valor de `numeric_expression` especificado a `power_expression`especificado.

**Exemplo** 

`SqlServer.ROUND(748.58, -3)`

## <a name="signexpression"></a>Sign(Expression) 

Retorna o positivo (+1), 0 (zero), ou (- o sinal de subtração de 1) da expressão especificada. 

**Argumentos** 

`expression`: `Int32`, `Int64`, `Double` ou `Decimal` 

**Valor retornado** 

Uma `Int32`, `Int64`, `Double`, ou `Decimal`. 

**Exemplo** 

`SqlServer.SIGN(-10)`

## <a name="sinexpression"></a>SIN(Expression)

Calcula o seno trigonométricas do ângulo especificado em radianos, e retorna uma expressão de `Double` . 

**Argumentos** 

`expression`: `Double`. 

**Valor retornado** 

Um `Double`. 

**Exemplo** `SqlServer.SIN(20)`

## <a name="sqrtexpression"></a>Sqrt(Expression)

Retorna a raiz quadrada de expressão especificada. 

**Argumentos** 

`expression`: `Double`. 

**Valor retornado** 

Um `Double`. 

**Exemplo** `SqlServer.SQRT(3600)`

## <a name="squareexpression"></a>SQUARE(Expression)

Retorna o quadrado de expressão especificada. 

**Argumentos** 

`expression`: `Double`. 

**Valor retornado** 

Um `Double`. 

**Exemplo** 

`SqlServer.SQUARE(25)`

## <a name="tanexpression"></a>TAN(Expression)

Calcula a tangente de uma expressão especificada.

**Argumentos** 

`expression`: `Double` 

**Valor retornado** 

`Double` 

**Exemplo** 

`SqlServer.TAN(45.0)`
  
## <a name="see-also"></a>Consulte também

Para obter mais informações sobre as funções matemáticas que suporta SqlClient, consulte a documentação para a versão do SQL Server que você especificou no manifesto do provedor SqlClient:  
  
**SQL Server 2005:** [funções matemáticas (Transact-SQL)](https://docs.microsoft.com/previous-versions/sql/sql-server-2005/ms177516(v=sql.90))  
**SQL Server 2008:** [funções matemáticas (Transact-SQL)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/ms177516(v=sql.100))  
**SQL Server 2012 e posterior:** [funções matemáticas (Transact-SQL)](/sql/t-sql/functions/mathematical-functions-transact-sql?view=sql-server-2017)   

 [SqlClient para funções de Entity Framework](sqlclient-for-ef-functions.md)
