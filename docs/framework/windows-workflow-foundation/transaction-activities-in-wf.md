---
title: "Atividades de transação em WF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fb33378e-82c6-4ea0-870f-76dc77e7f0fe
caps.latest.revision: "10"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: f6132f1d9cbeef3ed7af5d2b711d04e8bd5755bb
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="transaction-activities-in-wf"></a><span data-ttu-id="59e90-102">Atividades de transação em WF</span><span class="sxs-lookup"><span data-stu-id="59e90-102">Transaction Activities in WF</span></span>
<span data-ttu-id="59e90-103">[!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] tem vários sistema forneceu atividades modelando transações, compensação, e cancelar.</span><span class="sxs-lookup"><span data-stu-id="59e90-103">The [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] has several system-provided activities for modeling transactions, compensation, and cancellation.</span></span> <span data-ttu-id="59e90-104">Esses modelos de programação permitem que o fluxo de trabalho continue o progresso frente no caso de alterações na lógica comercial e no tratamento de erro.</span><span class="sxs-lookup"><span data-stu-id="59e90-104">These programming models allow the workflow to continue forward progress in the event of changes in business logic and error handling.</span></span> [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="59e90-105">transações de compensação e cancelamento, consulte [transações](../../../docs/framework/windows-workflow-foundation/workflow-transactions.md), [compensação](../../../docs/framework/windows-workflow-foundation/compensation.md), e [cancelamento](../../../docs/framework/windows-workflow-foundation/modeling-cancellation-behavior-in-workflows.md).</span><span class="sxs-lookup"><span data-stu-id="59e90-105"> transactions, compensation, and cancellation, see [Transactions](../../../docs/framework/windows-workflow-foundation/workflow-transactions.md), [Compensation](../../../docs/framework/windows-workflow-foundation/compensation.md), and [Cancellation](../../../docs/framework/windows-workflow-foundation/modeling-cancellation-behavior-in-workflows.md).</span></span>  
  
## <a name="transaction-activities"></a><span data-ttu-id="59e90-106">Atividades de transação</span><span class="sxs-lookup"><span data-stu-id="59e90-106">Transaction Activities</span></span>  
  
|||  
|-|-|  
|<xref:System.Activities.Statements.CancellationScope>|<span data-ttu-id="59e90-107">Associa a lógica cancelar, na forma de uma atividade, com um caminho principal de execução, também expresso como uma atividade.</span><span class="sxs-lookup"><span data-stu-id="59e90-107">Associates cancellation logic, in the form of an activity, with a main path of execution, also expressed as an activity.</span></span>|  
|<xref:System.Activities.Statements.CompensableActivity>|<span data-ttu-id="59e90-108">Oferece suporte a compensação das atividades filhos.</span><span class="sxs-lookup"><span data-stu-id="59e90-108">Supports compensation of its child activities.</span></span>|  
|<xref:System.Activities.Statements.Compensate>|<span data-ttu-id="59e90-109">Chama explicitamente o manipulador de compensação de <xref:System.Activities.Statements.CompensableActivity>.</span><span class="sxs-lookup"><span data-stu-id="59e90-109">Explicitly invokes the compensation handler of a <xref:System.Activities.Statements.CompensableActivity>.</span></span>|  
|<xref:System.Activities.Statements.Confirm>|<span data-ttu-id="59e90-110">Chama explicitamente o manipulador de confirmação de <xref:System.Activities.Statements.CompensableActivity>.</span><span class="sxs-lookup"><span data-stu-id="59e90-110">Explicitly invokes the confirmation handler of a <xref:System.Activities.Statements.CompensableActivity>.</span></span>|  
|<xref:System.Activities.Statements.TransactionScope>|<span data-ttu-id="59e90-111">Delimita um limite de transação.</span><span class="sxs-lookup"><span data-stu-id="59e90-111">Demarcates a transaction boundary.</span></span>|  
|<xref:System.ServiceModel.Activities.TransactedReceiveScope>|<span data-ttu-id="59e90-112">Defina o escopo o tempo de vida de uma transação que é iniciada por uma mensagem recebida.</span><span class="sxs-lookup"><span data-stu-id="59e90-112">Scopes the lifetime of a transaction that is initiated by a received message.</span></span> <span data-ttu-id="59e90-113">A transação pode ser fluída no fluxo de trabalho na mensagem iniciando, ou ser criada pelo distribuidor quando a mensagem é recebida.</span><span class="sxs-lookup"><span data-stu-id="59e90-113">The transaction may be flowed into the workflow on the initiating message, or created by the dispatcher when the message is received.</span></span> <span data-ttu-id="59e90-114">**Observação:** o <xref:System.ServiceModel.Activities.TransactedReceiveScope> está localizado no **mensagens** seção o **caixa de ferramentas**.</span><span class="sxs-lookup"><span data-stu-id="59e90-114">**Note:**  The <xref:System.ServiceModel.Activities.TransactedReceiveScope> is located in the **Messaging** section of the **Toolbox**.</span></span>|
