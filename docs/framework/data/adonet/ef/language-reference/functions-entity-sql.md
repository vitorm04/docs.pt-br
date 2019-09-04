---
title: Funções (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 52b3d776-5acc-4f69-b614-5a43ce56ef9f
ms.openlocfilehash: ec94a0f16fb3b836297f6675cc938a711816555b
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250915"
---
# <a name="functions-entity-sql"></a>Funções (Entity SQL)
Entity SQL oferece suporte funções definidas pelo usuário, funções, canônicas e funções específicos do provedor. As funções definidas pelo usuário são especificadas no modelo conceitual ou embutido na consulta. Para obter mais informações, consulte [funções definidas pelo usuário](user-defined-functions-entity-sql.md).  
  
 As funções canônicas são predefinidas em Entity Framework e devem ser suportados por provedores de dados. Os comandos de Entity SQL irão falhar se um usuário chama uma função que não é suportada por um provedor. Portanto, as funções canônicas são recomendadas em geral sobre as funções Store- específicas, que estão em um namespace específica do provedor. Para obter mais informações, consulte [funções canônicas](canonical-functions.md).  
  
 O provedor gerenciado cliente do Microsoft SQL fornece um conjunto de funções específicos do provedor. Para obter mais informações, consulte [SqlClient para funções de Entity Framework](../sqlclient-for-ef-functions.md).  
  
## <a name="in-this-section"></a>Nesta seção  
 [Funções definidas pelo usuário](user-defined-functions-entity-sql.md)  
  
 [Resolução de sobrecarga de função](function-overload-resolution-entity-sql.md)  
  
 [Funções agregadas](../aggregate-functions-sqlclient-for-entity-framework.md)  
  
## <a name="see-also"></a>Consulte também

- [Visão geral do Entity SQL](entity-sql-overview.md)
