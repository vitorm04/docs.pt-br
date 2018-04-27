---
title: Transactions2
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 51212219-a39e-448e-bff3-10064ff5de64
caps.latest.revision: 5
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 53389822f635151d15c2ae205c5a421a331c063b
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/27/2018
---
# <a name="transactions"></a>Transações
Esta seção contém exemplos que demonstram as transações de fluxo de trabalho no Windows Workflow Foundation (WF).  
  
## <a name="in-this-section"></a>Nesta seção  
 [TransactionScope básico](../../../../docs/framework/windows-workflow-foundation/samples/basic-transactionscope.md)  
 Consiste em quatro cenários que mostram como aninhar instâncias de <xref:System.Activities.Statements.TransactionScope> .  
  
 [Uso de TransactedReceiveScope](../../../../docs/framework/windows-workflow-foundation/samples/use-of-transactedreceivescope.md)  
 Demonstra como fluir uma transação de um cliente a um servidor usando <xref:System.Activities.Statements.TransactionScope> para criar uma nova transação no cliente e em <xref:System.ServiceModel.Activities.TransactedReceiveScope> para receber uma mensagem com uma transação fluída e definir o escopo o tempo de vida de transação no servidor.  
  
 [Aninhamento de TransactionScope em um serviço](../../../../docs/framework/windows-workflow-foundation/samples/nesting-of-transactionscope-within-a-service.md)  
 Consiste de dois cenários que mostram como manipular instâncias de atividade de <xref:System.Activities.Statements.TransactionScope> em um serviço.
