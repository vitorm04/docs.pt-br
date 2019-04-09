---
title: Funções canônicas de cadeias de caracteres
ms.date: 03/30/2017
ms.assetid: 5e2cbebd-5df3-47c7-b0e2-49a17ab22bfb
ms.openlocfilehash: bfd18f0302b897dabd7c75118e3892df6153ea63
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59155279"
---
# <a name="string-canonical-functions"></a>Funções canônicas de cadeias de caracteres
[!INCLUDE[esql](../../../../../../includes/esql-md.md)] inclui funções canônicas de cadeia de caracteres.  
  
## <a name="remarks"></a>Comentários  
 A tabela a seguir mostra a cadeia de caracteres [!INCLUDE[esql](../../../../../../includes/esql-md.md)] funções canônicas.  
  
|Função|Descrição|  
|--------------|-----------------|  
|`Concat(string1, string2)`|Retorna uma cadeia de caracteres que contém `string2` acrescentado a `string1`.<br /><br /> **Arguments**<br /><br /> `string1`: A cadeia de caracteres para o qual `string2` é acrescentado.<br /><br /> `string2`: A cadeia de caracteres que é acrescentada ao `string1`.<br /><br /> **Valor de retorno**<br /><br /> Um `String`. Um erro ocorrerá se o comprimento da cadeia de caracteres do valor de retorno é maior do que o comprimento máximo permitido.<br /><br /> **Exemplo**<br /><br /> `-- The following example returns abcxyz.`<br /><br /> `Concat('abc', 'xyz')`|  
|`Contains(string, target)`|Retorna `true` se `target` está contido em `string`.<br /><br /> **Arguments**<br /><br /> `string`: A cadeia de caracteres que é pesquisada.<br /><br /> `target`: A cadeia de caracteres de destino que é pesquisada.<br /><br /> **Valor de retorno**<br /><br /> `true` Se `target` está contida no `string`; caso contrário `false`.<br /><br /> **Exemplo**<br /><br /> `-- The following example returns true.`<br /><br /> `Contains('abc', 'bc')`|  
|`EndsWith(string, target)`|Retorna `true` se `target` termina com `string`.<br /><br /> **Arguments**<br /><br /> `string`: A cadeia de caracteres que é pesquisada.<br /><br /> `target`: A cadeia de caracteres de destino pesquisada no final da `string`.<br /><br /> **Valor de retorno**<br /><br /> `True` Se `string` termina com `target`; caso contrário `false`.<br /><br /> **Exemplo**<br /><br /> `-- The following example returns true.`<br /><br /> `EndsWith('abc', 'bc')` ***Observação:**  Se você estiver usando o provedor de dados do SQL Server, essa função retorna `false` se a cadeia de caracteres é armazenada em uma coluna de cadeia de caracteres de comprimento fixo e `target` é uma constante.INesse caso, a cadeia de caracteres inteira é pesquisada, incluindo todos os espaço à direita de preenchimento.AUma solução alternativa é possível quebrar dados a cadeia de caracteres de comprimento fixo, como no exemplo a seguir:`EndsWith(TRIM(string), target)`|  
|`IndexOf(target, string)`|Retorna a posição de `target` dentro de `string`0, ou se não foi encontrado. Retorna 1 para indicar o início de `string`. A numeração de índice parte de 1.<br /><br /> **Arguments**<br /><br /> `target`: A cadeia de caracteres que é procurada.<br /><br /> `string`: A cadeia de caracteres que é pesquisada.<br /><br /> **Valor de retorno**<br /><br /> Um `Int32`.<br /><br /> **Exemplo**<br /><br /> `-- The following example returns 4.`<br /><br /> `IndexOf('xyz', 'abcxyz')`|  
|`Left(string, length)`|Retorna o primeiro caracteres de `length` do lado esquerdo de `string`. Se o comprimento de `string` é menor que `length`, a cadeia de caracteres inteira é retornada.<br /><br /> **Arguments**<br /><br /> `string`: Um `String`.<br /><br /> `length`: Uma `Int16`, `Int32`, `Int64`, ou `Byte`. `length` não pode ser menor que zero.<br /><br /> **Valor de retorno**<br /><br /> Um `String`.<br /><br /> **Exemplo**<br /><br /> `-- The following example returns abc.`<br /><br /> `Left('abcxyz', 3)`|  
|`Length(string)`|Retorna o tamanho (de`Int32`), em caracteres, a cadeia de caracteres.<br /><br /> **Arguments**<br /><br /> `string`: Um `String`.<br /><br /> **Valor de retorno**<br /><br /> Um `Int32`.<br /><br /> **Exemplo**<br /><br /> `-- The following example returns 6.`<br /><br /> `Legth('abcxyz')`|  
|`LTrim(string)`|Retorna `string` sem espaço em branco à esquerda.<br /><br /> **Arguments**<br /><br /> Um `String`.<br /><br /> **Valor de retorno**<br /><br /> Um `String`.<br /><br /> **Exemplo**<br /><br /> `-- The following example returns abc.`<br /><br /> `LTrim('   abc')`|  
|`Replace(string1, string2, string3)`|Retorna `string1`, com todas as ocorrências de `string2` substituiu por `string3`.<br /><br /> **Arguments**<br /><br /> Um `String`.<br /><br /> **Valor de retorno**<br /><br /> Um `String`.<br /><br /> **Exemplo**<br /><br /> `-- The following example returns abcxyz.`<br /><br /> `Concat('abc', 'xyz')`|  
|`Reverse(string)`|Retorna `string` com a ordem dos caracteres revertidas.<br /><br /> **Arguments**<br /><br /> Um `String`.<br /><br /> **Valor de retorno**<br /><br /> Um `String`.<br /><br /> **Exemplo**<br /><br /> `-- The following example returns dcba.`<br /><br /> `Reverse('abcd')`|  
|`Right(string, length)`|Retorna o último `length` caracteres da `string`. Se o comprimento de `string` é menor que `length`, a cadeia de caracteres inteira é retornada.<br /><br /> **Arguments**<br /><br /> `string`: Um `String`.<br /><br /> `length`: Uma `Int16`, `Int32`, `Int64`, ou `Byte`. `length` não pode ser menor que zero.<br /><br /> **Valor de retorno**<br /><br /> Um `String`.<br /><br /> **Exemplo**<br /><br /> `-- The following example returns xyz.`<br /><br /> `Right('abcxyz', 3)`|  
|`RTrim(string)`|Retorna `string` sem espaço em branco à direita.<br /><br /> **Arguments**<br /><br /> Um `String`.<br /><br /> **Valor de retorno**<br /><br /> Um `String`.|  
|`Substring(string, start, length)`|Retorna a subcadeia de caracteres de cadeia de caracteres começando na posição `start`, com um comprimento de caracteres de `length` . Um início de 1 indica o primeiro caractere da cadeia de caracteres. A numeração de índice parte de 1.<br /><br /> **Arguments**<br /><br /> `string`: Um `String`.<br /><br /> `start`: Uma `Int16`, `Int32`, `Int64` e `Byte`. `start` não pode ser menor que 1.<br /><br /> `length`: Uma `Int16`, `Int32`, `Int64` e `Byte`. `length` não pode ser menor que zero.<br /><br /> **Valor de retorno**<br /><br /> Um `String`.<br /><br /> **Exemplo**<br /><br /> `-- The following example returns xyz.`<br /><br /> `Substring('abcxyz', 4, 3)`|  
|`StartsWith(string, target)`|Retorna `true` se inicia de `string` com `target`.<br /><br /> **Arguments**<br /><br /> `string`: A cadeia de caracteres que é pesquisada.<br /><br /> `target`: A cadeia de caracteres de destino pesquisada no início de `string`.<br /><br /> **Valor de retorno**<br /><br /> `True` Se `string` começa com `target`; caso contrário `false`.<br /><br /> **Exemplo**<br /><br /> `-- The following example returns true.`<br /><br /> `StartsWith('abc', 'ab')`|  
|`ToLower(string)`|Retorna `string` com os caracteres maiúsculas convertidos em minúsculas.<br /><br /> **Arguments**<br /><br /> Um `String`.<br /><br /> **Valor de retorno**<br /><br /> Um `String`.<br /><br /> **Exemplo**<br /><br /> `-- The following example returns abc.`<br /><br /> `ToLower('ABC')`|  
|`ToUpper(string)`|Retorna `string` com os caracteres em minúsculas convertidos para maiúsculas.<br /><br /> **Arguments**<br /><br /> Um `String`.<br /><br /> **Valor de retorno**<br /><br /> Um `String`.<br /><br /> **Exemplo**<br /><br /> `-- The following example returns ABC.`<br /><br /> `ToUpper('abc')`|  
|`Trim(string)`|Retorna `string` sem espaço em branco à esquerda e à direita.<br /><br /> **Arguments**<br /><br /> Um `String`.<br /><br /> **Valor de retorno**<br /><br /> Um `String`.<br /><br /> **Exemplo**<br /><br /> `-- The following example returns abc.`<br /><br /> `Trim('      abc   ')`|  
  
 Essas funções retornará `null` se entrada dada de `null` .  
  
 Funcionalidade equivalente está disponível no provedor gerenciado cliente do Microsoft SQL. Para obter mais informações, consulte [SqlClient para funções de Entity Framework](../../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md).  
  
## <a name="see-also"></a>Consulte também

- [Funções canônicas](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md)
