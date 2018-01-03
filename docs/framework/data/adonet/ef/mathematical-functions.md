---
title: "Funções matemáticas"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b040c7cb-156d-40f2-9152-61065b18148c
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: ea933d1e6c0245f3bc6cc2a0767b593957b0598a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="mathematical-functions"></a>Funções matemáticas
O provedor de dados. NET Framework para SQL Server (SqlClient) fornece as funções matemáticas que executam cálculos nos valores de entrada que são fornecidos como argumentos, e retorna um resultado de valor numérico. Essas funções estão no namespace SqlServer, que está disponível quando você usa o SqlClient. A propriedade de namespace de um provedor permite que Entity Framework descobrir que prefixo é usado por esse provedor para compilações específicas, como tipos e funções. A tabela a seguir descreve as funções matemáticas SqlClient.  
  
|Função|Descrição|  
|--------------|-----------------|  
|`ABS(``expression``)`|Executa a função de valor absoluto.<br /><br /> **Argumentos**<br /><br /> `expression`: Uma `Int32`, `Int64`, `Double`, ou `Decimal`.<br /><br /> **Valor retornado**<br /><br /> O valor absoluto de expressão especificada.<br /><br /> **Exemplo**<br /><br /> `SqlServer.ABS(-2)`|  
|`ACOS(``expression``)`|Retorna o valor de arccosine de expressão especificada.<br /><br /> **Argumentos**<br /><br /> `expression`: `Double`.<br /><br /> **Valor retornado**<br /><br /> Um `Double`.<br /><br /> **Exemplo**<br /><br /> `SqlServer.ACOS(.9)`|  
|`ASIN(``expression``)`|Retorna o valor de arcsine de expressão especificada.<br /><br /> **Argumentos**<br /><br /> `expression`: `Double`.<br /><br /> **Valor retornado**<br /><br /> Um `Double`.<br /><br /> **Exemplo**<br /><br /> `SqlServer.ASIN(.9)`|  
|`ATAN(``expression``)`|Retorna o valor de arctangent de expressão numérica especificada.<br /><br /> **Argumentos**<br /><br /> `expression`: `Double`.<br /><br /> **Valor retornado**<br /><br /> Um `Double`.<br /><br /> **Exemplo**<br /><br /> `SqlServer.ATAN(9)`|  
|`ATN2(` `expression`, `expression``)`|Retorna o ângulo, em radianos, cuja tangente é entre as duas expressões numéricas especificadas.<br /><br /> **Argumentos**<br /><br /> `expression`: `Double`.<br /><br /> **Valor retornado**<br /><br /> Um `Double`.<br /><br /> **Exemplo**<br /><br /> `SqlServer.ATN2(9, 8)`|  
|`CEILING(``expression``)`|Converte a expressão especificada para o inteiro menor que é maior ou igual a ele.<br /><br /> **Argumentos**<br /><br /> `expression`: Uma `Int32`, `Int64`, `Double`, ou `Decimal`.<br /><br /> **Valor retornado**<br /><br /> Um `Int32`, `Int64`, `Double`, ou `Decimal`.<br /><br /> **Exemplo**<br /><br /> [!code-csharp[DP EntityServices Concepts#SQLSERVER_CEILING](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_ceiling)]
 [!code-sql[DP EntityServices Concepts#SQLSERVER_CEILING](../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_ceiling)]|  
|`COS(``expression``)`|Calcula o cosseno trigonométricas do ângulo especificado em radianos.<br /><br /> **Argumentos**<br /><br /> `expression`: `Double`.<br /><br /> **Valor retornado**<br /><br /> Um `Double`.<br /><br /> **Exemplo**<br /><br /> `SqlServer.COS(45)`|  
|`COT(``expression``)`|Calcula o cotangente trigonométricas do ângulo especificado em radianos.<br /><br /> **Argumentos**<br /><br /> `expression`: `Double`.<br /><br /> **Valor retornado**<br /><br /> Um `Double`.<br /><br /> **Exemplo**<br /><br /> `SqlServer.COT(60)`|  
|`DEGREES(``radians``)`|Retorna o ângulo correspondente em graus.<br /><br /> **Argumentos**<br /><br /> `expression`: Uma `Int32`, `Int64`, `Double`, ou `Decimal`.<br /><br /> **Valor retornado**<br /><br /> Um `Int32`, `Int64`, `Double`, ou `Decimal`.<br /><br /> **Exemplo**<br /><br /> `SqlServer.DEGREES(3.1)`|  
|`EXP(``expression``)`|Calcula o valor exponencialmente de uma expressão numérica especificada.<br /><br /> **Argumentos**<br /><br /> `expression`: `Double`.<br /><br /> **Valor retornado**<br /><br /> Um `Double`.<br /><br /> **Exemplo**<br /><br /> `SqlServer.EXP(1)`|  
|`FLOOR(``expression``)`|Converte a expressão especificada para o inteiro maior menor ou igual a ele.<br /><br /> **Argumentos**<br /><br /> `expression`: `Double`.<br /><br /> **Valor retornado**<br /><br /> Um `Double`.<br /><br /> **Exemplo**<br /><br /> [!code-csharp[DP EntityServices Concepts#SQLSERVER_FLOOR](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_floor)]
 [!code-sql[DP EntityServices Concepts#SQLSERVER_FLOOR](../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_floor)]|  
|`LOG(``expression``)`|Calcula o logaritmo natural da expressão especificada de `float` .<br /><br /> **Argumentos**<br /><br /> `expression`: `Double`.<br /><br /> **Valor retornado**<br /><br /> Um `Double`.<br /><br /> **Exemplo**<br /><br /> `SqlServer.LOG(100)`|  
|`LOG10(``expression``)`|Retorna o logaritmo base-10 de expressão especificada de `Double` .<br /><br /> **Argumentos**<br /><br /> `expression`: `Double`.<br /><br /> **Valor retornado**<br /><br /> Um `Double`.<br /><br /> **Exemplo**<br /><br /> `SqlServer.LOG10(100)`|  
|`PI()`|Retorna o valor constante de pi como `Double`.<br /><br /> **Valor retornado**<br /><br /> Um `Double`.<br /><br /> **Exemplo**<br /><br /> `SqlServer.PI()`|  
|`POWER(``numeric_expression, power_expression``)`|Calcula o valor de uma expressão especificada em uma potência especificada.<br /><br /> **Argumentos**<br /><br /> `numeric_expression`: Uma `Int32`, `Int64`, `Double`, ou `Decimal`.<br /><br /> `power_expression`: `Double` que representa a potência para aumentar `numeric_expression`.<br /><br /> **Valor retornado**<br /><br /> O valor de `numeric_expression` especificado a `power_expression`especificado.<br /><br /> **Exemplo**<br /><br /> `SqlServer.POWER(2,7)`|  
|`RADIANS(``expression``)`|Converte graus a radianos.<br /><br /> **Argumentos**<br /><br /> `expression`: Uma `Int32`, `Int64`, `Double`, ou `Decimal`.<br /><br /> **Valor retornado**<br /><br /> Um `Int32`, `Int64`,<br /><br /> `Double`, ou<br /><br /> `Decimal`.<br /><br /> **Exemplo**<br /><br /> `SqlServer.RADIANS(360.0)`|  
|`RAND(`[semente]`)`|Retorna um valor aleatório de 0 a 1.<br /><br /> **Argumentos**<br /><br /> Retruns o valor semente como `Int32`. Se a semente não for especificada, o mecanismo de base de dados SQL Server atribui um valor semente aleatoriamente. Para um valor semente especificado, o resultado retornado é sempre o mesmo.<br /><br /> **Valor retornado**<br /><br /> Um valor aleatório de 0 a 1. de `Double` .<br /><br /> **Exemplo**<br /><br /> `SqlServer.RAND()`|  
|`ROUND(` `numeric_expression, length` [ ,`function` ]`)`|Retorna uma expressão numérica, arredondada para o comprimento ou a precisão especificada.<br /><br /> **Argumentos**<br /><br /> `numeric_expression`: Uma `Int32`, `Int64`, `Double`, ou `Decimal`.<br /><br /> `length`: `Int32` que representa a precisão que a `numeric_expression` deve ser arredondado. Quando `length` é um número positivo, `numeric_expression` ele é arredondado para o número de posições decimais especificadas por `length`. Quando `length` é um número negativo, `numeric_expression` é arredondado no lado esquerdo do ponto decimal, como especificado por `length`.<br /><br /> `function`: (opcional) um `Int32` que representa o tipo de operação a ser executada. Quando a função for omitida ou tem um valor de 0 (padrão), `numeric_expression` é arredondado. Quando um valor diferente de 0 for especificado, `numeric_expression` será truncado.<br /><br /> **Valor retornado**<br /><br /> O valor de `numeric_expression` especificado a `power_expression`especificado.<br /><br /> **Exemplo**<br /><br /> `SqlServer.ROUND(748.58, -3)`|  
|`SIGN(``expression``)`|Retorna o positivo (+1), 0 (zero), ou (- o sinal de subtração de 1) da expressão especificada.<br /><br /> **Argumentos**<br /><br /> `expression`: `Int32`, `Int64`, `Double` ou `Decimal`<br /><br /> **Valor retornado**<br /><br /> Um `Int32`, `Int64`, `Double`, ou `Decimal`.<br /><br /> **Exemplo**<br /><br /> `SqlServer.SIGN(-10)`|  
|`SIN(``expression``)`|Calcula o seno trigonométricas do ângulo especificado em radianos, e retorna uma expressão de `Double` .<br /><br /> **Argumentos**<br /><br /> `expression`: `Double`.<br /><br /> **Valor retornado**<br /><br /> Um `Double`.<br /><br /> **Exemplo**<br /><br /> `SqlServer.SIN(20)`|  
|`SQRT(``expression``)`|Retorna a raiz quadrada de expressão especificada.<br /><br /> **Argumentos**<br /><br /> `expression`: `Double`.<br /><br /> **Valor retornado**<br /><br /> Um `Double`.<br /><br /> **Exemplo**<br /><br /> `SqlServer.SQRT(3600)`|  
|`SQUARE(``expression``)`|Retorna o quadrado de expressão especificada.<br /><br /> **Argumentos**<br /><br /> `expression`: `Double`.<br /><br /> **Valor retornado**<br /><br /> Um `Double`.<br /><br /> **Exemplo**<br /><br /> `SqlServer.SQUARE(25)`|  
|`TAN(``expression``)`|Calcula a tangente de uma expressão especificada.<br /><br /> **Argumentos**<br /><br /> `expression`: `Double`<br /><br /> **Valor retornado**<br /><br /> `Double`<br /><br /> **Exemplo**<br /><br /> `SqlServer.TAN(45.0)`|  
  
 Para obter mais informações sobre as funções matemáticas que suporta SqlClient, consulte a documentação para a versão do SQL Server que você especificou no manifesto do provedor SqlClient:  
  
|SQL Server 2000|SQL Server 2005|SQL Server 2008|  
|---------------------|---------------------|---------------------|  
|[Funções matemáticas (Transact-SQL)](http://go.microsoft.com/fwlink/?LinkId=115913)|[Funções matemáticas (Transact-SQL)](http://go.microsoft.com/fwlink/?LinkId=115911)|[Funções matemáticas (Transact-SQL)](http://go.microsoft.com/fwlink/?LinkId=115912)|  
  
## <a name="see-also"></a>Consulte também  
 [SqlClient para funções de Entity Framework](../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md)
