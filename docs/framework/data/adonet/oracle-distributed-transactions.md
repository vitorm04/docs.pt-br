---
title: Transações distribuídas do Oracle
ms.date: 03/30/2017
ms.assetid: c340ca81-ef79-402f-b204-c5156b890fe5
ms.openlocfilehash: edd06b94ce4157e90d334ee7feac2a449f7ee74b
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73040473"
---
# <a name="oracle-distributed-transactions"></a>Transações distribuídas do Oracle
O objeto <xref:System.Data.OracleClient.OracleConnection> será automaticamente inscrito em uma transação distribuída existente se determinar que uma transação está ativa. A inscrição de transação automática ocorre quando a conexão é aberta ou recuperada do pool de conexões. Você pode desabilitar a inscrição automática em transações existentes especificando  
  
```csharp  
Enlist=false  
```  
  
 como um parâmetro de cadeia de conexão para um <xref:System.Data.OracleClient.OracleConnection>.  
  
## <a name="see-also"></a>Consulte também

- [Oracle and ADO.NET](oracle-and-adonet.md) (Oracle e ADO.NET)
- [ADO.NET Overview](ado-net-overview.md) (Visão geral do ADO.NET)
