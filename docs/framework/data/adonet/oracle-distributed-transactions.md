---
title: Transações distribuídas do Oracle
ms.date: 03/30/2017
ms.assetid: c340ca81-ef79-402f-b204-c5156b890fe5
ms.openlocfilehash: 8e7530621254881402570b59b47a22052b40f2b5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54713231"
---
# <a name="oracle-distributed-transactions"></a>Transações distribuídas do Oracle
O <xref:System.Data.OracleClient.OracleConnection> objeto automaticamente se inscreve em uma transação distribuída existente caso Determine que uma transação está ativa. Inscrição automática de transação ocorre quando a conexão for aberto ou recuperado do pool de conexão. Você pode desabilitar a inscrição automática em transações existentes especificando  
  
```  
Enlist=false  
```  
  
 como um parâmetro de cadeia de caracteres de conexão para um <xref:System.Data.OracleClient.OracleConnection>.  
  
## <a name="see-also"></a>Consulte também
- [Oracle and ADO.NET](../../../../docs/framework/data/adonet/oracle-and-adonet.md) (Oracle e ADO.NET)
- [ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
