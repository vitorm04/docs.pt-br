---
title: Transações distribuídas do Oracle
ms.date: 03/30/2017
ms.assetid: c340ca81-ef79-402f-b204-c5156b890fe5
ms.openlocfilehash: 4af1c98818f1929850c5ae78892c64993a93d4d2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59116211"
---
# <a name="oracle-distributed-transactions"></a>Transações distribuídas do Oracle
O <xref:System.Data.OracleClient.OracleConnection> objeto automaticamente se inscreve em uma transação distribuída existente caso Determine que uma transação está ativa. Inscrição automática de transação ocorre quando a conexão for aberto ou recuperado do pool de conexão. Você pode desabilitar a inscrição automática em transações existentes especificando  
  
```  
Enlist=false  
```  
  
 como um parâmetro de cadeia de caracteres de conexão para um <xref:System.Data.OracleClient.OracleConnection>.  
  
## <a name="see-also"></a>Consulte também

- [Oracle e ADO.NET](../../../../docs/framework/data/adonet/oracle-and-adonet.md)
- [Central de desenvolvedores de provedores gerenciados ADO.NET e DataSet](https://go.microsoft.com/fwlink/?LinkId=217917)
