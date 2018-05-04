---
title: Funções definidas pelo usuário (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 3f9e6bbd-8e5a-43e1-809f-f8a61338e522
ms.openlocfilehash: a3c9cda162e77517d480d9e48eb80fa62dd1c161
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="user-defined-functions-entity-sql"></a>Funções definidas pelo usuário (Entity SQL)
Suporte de Entity SQL que chamam funções definidas pelo usuário em uma consulta. Você pode definir essas funções em linha com a consulta (consulte [como: chamar uma função definida pelo usuário](http://msdn.microsoft.com/library/ad131b86-8b4e-4747-8605-d4fc64fb9d02)) ou como parte do modelo conceitual (consulte [como: definir funções de personalizados no modelo conceitual](http://msdn.microsoft.com/library/0dad7b8b-58f6-4271-b238-f34810d68e5f)). Funções de modelo conceitual são definidas como um comando de Entity SQL no [DefiningExpression](http://msdn.microsoft.com/library/d3da8d8b-a048-47ee-8d81-0c2ea3acdd3e) elemento de um [função](http://msdn.microsoft.com/library/dc3beca7-55cf-4977-8db0-5064cdbab134) elemento no modelo conceitual.  
  
 Entity SQL permite que você defina funções no comando de consulta próprias. O [função](../../../../../../docs/framework/data/adonet/ef/language-reference/function-entity-sql.md) operador define as funções embutidas. Você pode definir várias funções em um único comando, e essas funções podem ter o mesmo nome de função, como as assinaturas de função são exclusivos. Para obter mais informações, consulte [a resolução de sobrecarga de função](../../../../../../docs/framework/data/adonet/ef/language-reference/function-overload-resolution-entity-sql.md).  
  
## <a name="see-also"></a>Consulte também  
 [Funções](../../../../../../docs/framework/data/adonet/ef/language-reference/functions-entity-sql.md)
