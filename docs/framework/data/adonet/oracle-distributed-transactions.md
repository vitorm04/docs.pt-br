---
title: Transações distribuídas do Oracle
ms.date: 03/30/2017
ms.assetid: c340ca81-ef79-402f-b204-c5156b890fe5
ms.openlocfilehash: a21134c3283d3d9d8d7660eecaaf74d60ecf6662
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91166515"
---
# <a name="oracle-distributed-transactions"></a>Transações distribuídas do Oracle

O <xref:System.Data.OracleClient.OracleConnection> objeto será automaticamente inscrito em uma transação distribuída existente se determinar que uma transação está ativa. A inscrição de transação automática ocorre quando a conexão é aberta ou recuperada do pool de conexões. Você pode desabilitar a inscrição automática em transações existentes especificando  
  
```csharp  
Enlist=false  
```  
  
 como um parâmetro de cadeia de conexão para um <xref:System.Data.OracleClient.OracleConnection> .  
  
## <a name="see-also"></a>Confira também

- [Oracle e ADO.NET](oracle-and-adonet.md)
- [Visão geral do ADO.NET](ado-net-overview.md)
