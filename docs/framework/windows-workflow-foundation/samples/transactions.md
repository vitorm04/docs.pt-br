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
# <a name="transactions"></a><span data-ttu-id="27f0d-102">Transações</span><span class="sxs-lookup"><span data-stu-id="27f0d-102">Transactions</span></span>
<span data-ttu-id="27f0d-103">Esta seção contém exemplos que demonstram as transações de fluxo de trabalho no Windows Workflow Foundation (WF).</span><span class="sxs-lookup"><span data-stu-id="27f0d-103">This section contains samples that demonstrate workflow transactions in Windows Workflow Foundation (WF).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="27f0d-104">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="27f0d-104">In This Section</span></span>  
 [<span data-ttu-id="27f0d-105">TransactionScope básico</span><span class="sxs-lookup"><span data-stu-id="27f0d-105">Basic TransactionScope</span></span>](../../../../docs/framework/windows-workflow-foundation/samples/basic-transactionscope.md)  
 <span data-ttu-id="27f0d-106">Consiste em quatro cenários que mostram como aninhar instâncias de <xref:System.Activities.Statements.TransactionScope> .</span><span class="sxs-lookup"><span data-stu-id="27f0d-106">Consists of four scenarios that show how to nest <xref:System.Activities.Statements.TransactionScope> instances.</span></span>  
  
 [<span data-ttu-id="27f0d-107">Uso de TransactedReceiveScope</span><span class="sxs-lookup"><span data-stu-id="27f0d-107">Use of TransactedReceiveScope</span></span>](../../../../docs/framework/windows-workflow-foundation/samples/use-of-transactedreceivescope.md)  
 <span data-ttu-id="27f0d-108">Demonstra como fluir uma transação de um cliente a um servidor usando <xref:System.Activities.Statements.TransactionScope> para criar uma nova transação no cliente e em <xref:System.ServiceModel.Activities.TransactedReceiveScope> para receber uma mensagem com uma transação fluída e definir o escopo o tempo de vida de transação no servidor.</span><span class="sxs-lookup"><span data-stu-id="27f0d-108">Demonstrates how to flow a transaction from a client to a server using <xref:System.Activities.Statements.TransactionScope> to create a new transaction on the client and a <xref:System.ServiceModel.Activities.TransactedReceiveScope> to receive a message with a flowed transaction and scope the lifetime of the transaction on the server.</span></span>  
  
 [<span data-ttu-id="27f0d-109">Aninhamento de TransactionScope em um serviço</span><span class="sxs-lookup"><span data-stu-id="27f0d-109">Nesting of TransactionScope within a service</span></span>](../../../../docs/framework/windows-workflow-foundation/samples/nesting-of-transactionscope-within-a-service.md)  
 <span data-ttu-id="27f0d-110">Consiste de dois cenários que mostram como manipular instâncias de atividade de <xref:System.Activities.Statements.TransactionScope> em um serviço.</span><span class="sxs-lookup"><span data-stu-id="27f0d-110">Consists of two scenarios that show how to handle <xref:System.Activities.Statements.TransactionScope> activity instances within a service.</span></span>
