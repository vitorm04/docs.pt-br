---
title: Transações distribuídas do Oracle
ms.date: 03/30/2017
ms.assetid: c340ca81-ef79-402f-b204-c5156b890fe5
ms.openlocfilehash: 0e9dcb30eb1962071d7154d4bbf929871c8a12d2
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="oracle-distributed-transactions"></a>Transações distribuídas do Oracle
O <xref:System.Data.OracleClient.OracleConnection> objeto inscreve automaticamente em uma transação distribuída existente se ela determina se uma transação está ativa. Inscrição de transação automática ocorre quando a conexão está aberta ou recuperado do pool de conexão. Você pode desabilitar a inscrição automática em transações, especificando  
  
```  
Enlist=false  
```  
  
 como um parâmetro de cadeia de caracteres de conexão para um <xref:System.Data.OracleClient.OracleConnection>.  
  
## <a name="see-also"></a>Consulte também  
 [Oracle and ADO.NET](../../../../docs/framework/data/adonet/oracle-and-adonet.md) (Oracle e ADO.NET)  
 [ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
