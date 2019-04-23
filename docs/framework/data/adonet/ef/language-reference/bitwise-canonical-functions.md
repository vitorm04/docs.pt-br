---
title: Funções canônicas bit a bit
ms.date: 03/30/2017
ms.assetid: 993868ca-16e3-47b6-9915-c29cd63b0a21
ms.openlocfilehash: 67d78e8d31f0bc3564a0a111b9bc71cbd0e14f5c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59127785"
---
# <a name="bitwise-canonical-functions"></a>Funções canônicas bit a bit
[!INCLUDE[esql](../../../../../../includes/esql-md.md)] inclui funções canônicas bit a bit.  
  
## <a name="remarks"></a>Comentários  
 A tabela a seguir mostra a [!INCLUDE[esql](../../../../../../includes/esql-md.md)] bit a bit funções canônicas. Essas funções retornarão `Null` se `Null` a entrada é fornecida. O tipo de retorno de funções é o mesmo que os tipos de argumento. Os argumentos devem ser do mesmo tipo, se a função recebe mais de um argumento. Para executar operações bit a bit entre tipos diferentes, você precisa converter explicitamente para o mesmo tipo.  
  
|Função|Descrição|  
|--------------|-----------------|  
|`BitWiseAnd (` `value1` `,`  `value2` `)`|Retorna a conjução bit a bit de `value1` e de `value2` como o tipo de `value1` e de `value2`.<br /><br /> **Argumentos**<br /><br /> Um `Byte`, `Int16`, `Int32`, e `Int64`.<br /><br /> **Exemplo**<br /><br /> `-- The following example returns 1.`<br /><br /> `BitWiseAnd(1,3)`|  
|`BitWiseNot (` `value` `)`|Retorna a negação bit a bit de `value`.<br /><br /> **Argumentos**<br /><br /> Um `Byte`, `Int16`, `Int32`, e `Int64`.<br /><br /> **Exemplo**<br /><br /> `-- The following example returns -4.`<br /><br /> `BitWiseNot(3)`|  
|`BitWiseOr (` `value1` `,`  `value2` `)`|Retorna a disjução bit a bit de `value1` e de `value2` como o tipo de `value1` e de `value2`.<br /><br /> **Argumentos**<br /><br /> Um `Byte`, `Int16`, `Int32` e `Int64`.<br /><br /> **Exemplo**<br /><br /> `-- The following example returns 3.`<br /><br /> `BitWiseOr(1,3)`|  
|`BitWiseXor (` `value1` `,`  `value2` `)`|Retorna a disjunção bit a bit exclusiva de `value1` e de `value2` como o tipo de `value1` e de `value2`.<br /><br /> **Argumentos**<br /><br /> Um `Byte`, `Int16`, `Int32` e `Int64`.<br /><br /> **Exemplo**<br /><br /> `-- The following example returns 2.`<br /><br /> `BitWiseXor (1,3)`|  
  
## <a name="see-also"></a>Consulte também

- [Canonical Functions](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md) (Funções canônicas)
