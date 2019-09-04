---
title: Funções definidas pelo usuário (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 3f9e6bbd-8e5a-43e1-809f-f8a61338e522
ms.openlocfilehash: 9ddafb18a10ff2313fd27eab453907054a35218a
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70248765"
---
# <a name="user-defined-functions-entity-sql"></a>Funções definidas pelo usuário (Entity SQL)
Suporte de Entity SQL que chamam funções definidas pelo usuário em uma consulta. Você pode definir essas funções embutidas com a consulta ( [consulte Como: Chame uma função](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd490951(v=vs.100))definida pelo usuário ou como parte do modelo conceitual (consulte [como: Definir funções personalizadas no modelo](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd456812(v=vs.100))conceitual). As funções de modelo conceitual são definidas como um comando Entity SQL no elemento de [definição](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#definingexpression-element-csdl) de um elemento [Function](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#function-element-csdl) no modelo conceitual.  
  
 Entity SQL permite que você defina funções no comando de consulta próprias. O operador [Function](function-entity-sql.md) define funções embutidas. Você pode definir várias funções em um único comando, e essas funções podem ter o mesmo nome de função, como as assinaturas de função são exclusivos. Para obter mais informações, consulte [resolução de sobrecarga de função](function-overload-resolution-entity-sql.md).  
  
## <a name="see-also"></a>Consulte também

- [Funções](functions-entity-sql.md)
