---
title: Funções (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 52b3d776-5acc-4f69-b614-5a43ce56ef9f
ms.openlocfilehash: bef959ae6a835b5d1d696162528a8f904c59e8e5
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91201064"
---
# <a name="functions-entity-sql"></a>Funções (Entity SQL)

Entity SQL oferece suporte funções definidas pelo usuário, funções, canônicas e funções específicos do provedor. As funções definidas pelo usuário são especificadas no modelo conceitual ou embutido na consulta. Para obter mais informações, consulte [funções definidas pelo usuário](user-defined-functions-entity-sql.md).  
  
 As funções canônicas são predefinidas em Entity Framework e devem ser suportados por provedores de dados. Os comandos de Entity SQL irão falhar se um usuário chama uma função que não é suportada por um provedor. Portanto, as funções canônicas são recomendadas em geral sobre as funções Store- específicas, que estão em um namespace específica do provedor. Para obter mais informações, consulte [funções canônicas](canonical-functions.md).  
  
 O provedor gerenciado cliente do Microsoft SQL fornece um conjunto de funções específicos do provedor. Para obter mais informações, consulte [SqlClient para funções de Entity Framework](../sqlclient-for-ef-functions.md).  
  
## <a name="in-this-section"></a>Nesta seção  

 [Funções definidas pelo usuário](user-defined-functions-entity-sql.md)  
  
 [Resolução de sobrecarga de função](function-overload-resolution-entity-sql.md)  
  
 [Funções de Agregação](../aggregate-functions-sqlclient-for-entity-framework.md)  
  
## <a name="see-also"></a>Veja também

- [Visão geral da Entity SQL](entity-sql-overview.md)
