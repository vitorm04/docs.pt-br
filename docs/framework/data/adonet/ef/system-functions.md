---
title: Funções do sistema
ms.date: 03/30/2017
ms.assetid: b7c71b58-09e6-44ce-a3e5-a0fdb892fb86
ms.openlocfilehash: 0d46429ac958e6f5db4d51947669784303af783b
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91156492"
---
# <a name="system-functions"></a>Funções do sistema

O provedor de dados. NET Framework para SQL Server (SqlClient) fornece as seguintes funções do sistema:  
  
|Função|Descrição|  
|--------------|-----------------|  
|`CHECKSUM (` `value`, [`value`, [`value`]]`)`|Retorna o valor de soma de verificação. `CHECKSUM` destina para uso em índices de hash de compilação.<br /><br /> **Argumentos**<br /><br /> `value`: A,,,, `Boolean` `Byte` `Int16` `Int32` `Int64` , `Single` , `Decimal` , `Double` , `DateTime` , `String` , `Binary` ou `Guid` . Você pode especificar um, dois ou três valores.<br /><br /> **Valor Retornado**<br /><br /> O valor absoluto de expressão especificada.<br /><br /> **Exemplo**<br /><br /> `SqlServer.CHECKSUM(10,100,1000.0)`|  
|`CURRENT_TIMESTAMP ()`|Gerencia a data e hora no formato interno do SQL Server para valores de `DateTime` com uma precisão de 7 no SQL Server 2008 e uma precisão de 3 no SQL Server 2005.<br /><br /> **Valor Retornado**<br /><br /> A data e hora atuais do sistema como `DateTime`.<br /><br /> **Exemplo**<br /><br /> `SqlServer.CURRENT_TIMESTAMP()`|  
|`CURRENT_ USER` `()`|Retorna o nome do usuário atual.<br /><br /> **Valor Retornado**<br /><br /> Um `String` ASCII.<br /><br /> **Exemplo**<br /><br /> `SqlServer.CURRENT_USER()`|  
|`DATALENGTH` `(` `expression` `)`|Retorna o número de bytes usados para representar qualquer expressão.<br /><br /> **Argumentos**<br /><br /> `expression`: A,,,,,, `Boolean` `Byte` `Int16` `Int32` `Int64` `Single` `Decimal` , `Double` , `DateTime` , `Time` , `DateTimeOffset` , `String` , `Binary` ou `Guid` .<br /><br /> **Valor Retornado**<br /><br /> O tamanho das propriedades como `Int32`.<br /><br /> **Exemplo**<br /><br /> `SELECT VALUE SqlServer.DATALENGTH(P.Name)FROM`<br /><br /> `AdventureWorksEntities.Product AS P`|  
|`HOST_NAME()`|Retorna o nome da estação de trabalho.<br /><br /> **Valor Retornado**<br /><br /> Um `String` Unicode.<br /><br /> **Exemplo**<br /><br /> `SqlServer.HOST_NAME()`|  
|`ISDATE(` `expression` `)`|Determina se uma expressão de entrada é uma data válida.<br /><br /> **Argumentos**<br /><br /> `expression`: A,,,,,, `Boolean` `Byte` `Int16` `Int32` `Int64` `Single` `Decimal` , `Double` , `DateTime` , `Time` , `DateTimeOffset` , `String` , `Binary` ou `Guid` .<br /><br /> **Valor Retornado**<br /><br /> Um `Int32`. Um (1) se a expressão de entrada é uma data válida. Zero (0) de outra maneira.<br /><br /> **Exemplo**<br /><br /> `SqlServer.ISDATE('1/1/2006')`|  
|`ISNUMERIC(` `expression` `)`|Determina se uma expressão é um tipo numérico válido.<br /><br /> **Argumentos**<br /><br /> `expression`: A,,,,,, `Boolean` `Byte` `Int16` `Int32` `Int64` `Single` `Decimal` , `Double` , `DateTime` , `Time` , `DateTimeOffset` , `String` , `Binary` ou `Guid` .<br /><br /> **Valor Retornado**<br /><br /> Um `Int32`. Um (1) se a expressão de entrada é uma data válida. Zero (0) de outra maneira.<br /><br /> **Exemplo**<br /><br /> `SqlServer.ISNUMERIC('21')`|  
|`NEWID()`|Cria um valor exclusivo do tipo GUID.<br /><br /> **Valor Retornado**<br /><br /> Um `Guid`.<br /><br /> **Exemplo**<br /><br /> `SqlServer.NEWID()`|  
|`USER_NAME(` `id` `)`|Retorna um nome de usuário de banco de dados de um número de identificação especificado.<br /><br /> **Argumentos**<br /><br /> `expression`: Um número de identificação de `Int32` associada a um usuário de base de dados.<br /><br /> **Valor Retornado**<br /><br /> Um `String` Unicode.<br /><br /> **Exemplo**<br /><br /> `SqlServer.USER_NAME(0)`|  
  
 Para obter mais informações sobre as `String` funções que o SqlClient dá suporte, consulte [funções de cadeia de caracteres (TRANSACT-SQL)](/sql/t-sql/functions/string-functions-transact-sql).
  
## <a name="see-also"></a>Confira também

- [Linguagem Entity SQL](./language-reference/entity-sql-language.md)
- [SqlClient para funções de Entity Framework](sqlclient-for-ef-functions.md)
