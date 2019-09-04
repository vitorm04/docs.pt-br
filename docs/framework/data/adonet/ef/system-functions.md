---
title: Funções do sistema
ms.date: 03/30/2017
ms.assetid: b7c71b58-09e6-44ce-a3e5-a0fdb892fb86
ms.openlocfilehash: 552f374bc1824a16fb323cd19abe79c1914295a7
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70248230"
---
# <a name="system-functions"></a>Funções do sistema
O provedor de dados. NET Framework para SQL Server (SqlClient) fornece as seguintes funções do sistema:  
  
|Função|Descrição|  
|--------------|-----------------|  
|`CHECKSUM (` `value`, [`value`, [`value`]]`)`|Retorna o valor de soma de verificação. `CHECKSUM` destina para uso em índices de hash de compilação.<br /><br /> **Argumentos**<br /><br /> `value`: A `Boolean`, `Byte` ,`Int16`, ,,`Int32`,, ,`DateTime`, ,`String`ou. `Double` `Binary` `Int64` `Single` `Decimal` `Guid` Você pode especificar um, dois ou três valores.<br /><br /> **Valor retornado**<br /><br /> O valor absoluto de expressão especificada.<br /><br /> **Exemplo**<br /><br /> `SqlServer.CHECKSUM(10,100,1000.0)`|  
|`CURRENT_TIMESTAMP ()`|Gerencia a data e hora no formato interno do SQL Server para valores de `DateTime` com uma precisão de 7 no SQL Server 2008 e uma precisão de 3 no SQL Server 2005.<br /><br /> **Valor retornado**<br /><br /> A data e hora atuais do sistema como `DateTime`.<br /><br /> **Exemplo**<br /><br /> `SqlServer.CURRENT_TIMESTAMP()`|  
|`CURRENT_ USER` `()`|Retorna o nome do usuário atual.<br /><br /> **Valor retornado**<br /><br /> Um `String` ASCII.<br /><br /> **Exemplo**<br /><br /> `SqlServer.CURRENT_USER()`|  
|`DATALENGTH` `(` `expression` `)`|Retorna o número de bytes usados para representar qualquer expressão.<br /><br /> **Argumentos**<br /><br /> `expression`: A `Boolean` ,`Byte`, ,`Int32`, ,`Int64` ,,`DateTime`,, ,`Binary`,, ou `Time` `Double` `Decimal` `Int16` `Single` `DateTimeOffset` `String` `Guid`.<br /><br /> **Valor retornado**<br /><br /> O tamanho das propriedades como `Int32`.<br /><br /> **Exemplo**<br /><br /> `SELECT VALUE SqlServer.DATALENGTH(P.Name)FROM`<br /><br /> `AdventureWorksEntities.Product AS P`|  
|`HOST_NAME()`|Retorna o nome da estação de trabalho.<br /><br /> **Valor retornado**<br /><br /> Um `String` Unicode.<br /><br /> **Exemplo**<br /><br /> `SqlServer.HOST_NAME()`|  
|`ISDATE(` `expression` `)`|Determina se uma expressão de entrada é uma data válida.<br /><br /> **Argumentos**<br /><br /> `expression`: A `Boolean` ,`Byte`, ,`Int32`, ,`Int64` ,,`DateTime`,, ,`Binary`,, ou `Time` `Double` `Decimal` `Int16` `Single` `DateTimeOffset` `String` `Guid`.<br /><br /> **Valor retornado**<br /><br /> Um `Int32`. Um (1) se a expressão de entrada é uma data válida. Zero (0) de outra maneira.<br /><br /> **Exemplo**<br /><br /> `SqlServer.ISDATE('1/1/2006')`|  
|`ISNUMERIC(` `expression` `)`|Determina se uma expressão é um tipo numérico válido.<br /><br /> **Argumentos**<br /><br /> `expression`: A `Boolean` ,`Byte`, ,`Int32`, ,`Int64` ,,`DateTime`,, ,`Binary`,, ou `Time` `Double` `Decimal` `Int16` `Single` `DateTimeOffset` `String` `Guid`.<br /><br /> **Valor retornado**<br /><br /> Um `Int32`. Um (1) se a expressão de entrada é uma data válida. Zero (0) de outra maneira.<br /><br /> **Exemplo**<br /><br /> `SqlServer.ISNUMERIC('21')`|  
|`NEWID()`|Cria um valor exclusivo do tipo GUID.<br /><br /> **Valor retornado**<br /><br /> Um `Guid`.<br /><br /> **Exemplo**<br /><br /> `SqlServer.NEWID()`|  
|`USER_NAME(` `id` `)`|Retorna um nome de usuário de base de dados de um número de identificação especificado.<br /><br /> **Argumentos**<br /><br /> `expression`: Um `Int32` número de identificação associado a um usuário de banco de dados.<br /><br /> **Valor retornado**<br /><br /> Um `String` Unicode.<br /><br /> **Exemplo**<br /><br /> `SqlServer.USER_NAME(0)`|  
  
 Para obter mais informações sobre a cadeia de caracteres funções que SqlClient suporte, consulte a documentação para a versão do SQL Server que você especificou no manifesto do provedor SqlClient:  
  
|SQL Server 2000|SQL Server 2005|SQL Server 2008|  
|---------------------|---------------------|---------------------|  
|[Funções do sistema Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=115918)|[Funções do sistema Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=115917)|[Funções do sistema (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=115919)|  
  
## <a name="see-also"></a>Consulte também

- [Entity SQL Language](./language-reference/entity-sql-language.md) (Linguagem SQL de entidade)
- [SqlClient para funções de Entity Framework](sqlclient-for-ef-functions.md)
