---
title: "Exceções, transações, e compensação"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: programming [WF], error handling
ms.assetid: 694db4f9-7387-4b13-8f9f-b923b18c7490
caps.latest.revision: "12"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: be803580a4d8ed195222e5960cfa6e26804d91c5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="exceptions-transactions-and-compensation"></a><span data-ttu-id="74488-102">Exceções, transações, e compensação</span><span class="sxs-lookup"><span data-stu-id="74488-102">Exceptions, Transactions, and Compensation</span></span>
[!INCLUDE[wf1](../../../includes/wf1-md.md)]<span data-ttu-id="74488-103"> fornece vários mecanismos diferentes para manipular condições de erro em tempo de execução em fluxos de trabalho.</span><span class="sxs-lookup"><span data-stu-id="74488-103"> provides several different mechanisms for handling run-time error conditions in workflows.</span></span> <span data-ttu-id="74488-104">Fluxos de trabalho podem usar uma combinação de manipuladores, de transações, de cancelar, e de compensação de exceção para manipular normalmente e recuperar as condições de erro.</span><span class="sxs-lookup"><span data-stu-id="74488-104">Workflows can use a combination of exception handlers, transactions, cancellation, and compensation to handle and recover gracefully from error conditions.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="74488-105">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="74488-105">In This Section</span></span>  
 [<span data-ttu-id="74488-106">Exceções</span><span class="sxs-lookup"><span data-stu-id="74488-106">Exceptions</span></span>](../../../docs/framework/windows-workflow-foundation/exceptions.md)  
 <span data-ttu-id="74488-107">Demonstra como usar a atividade de <xref:System.Activities.Statements.TryCatch> para tratar exceções em um fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="74488-107">Demonstrates how to use the <xref:System.Activities.Statements.TryCatch> activity to handle exceptions in a workflow.</span></span>  
  
 [<span data-ttu-id="74488-108">Transações</span><span class="sxs-lookup"><span data-stu-id="74488-108">Transactions</span></span>](../../../docs/framework/windows-workflow-foundation/workflow-transactions.md)  
 <span data-ttu-id="74488-109">Demonstra como usar a atividade de <xref:System.Activities.Statements.TransactionScope> para usar transações em um fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="74488-109">Demonstrates how to use the <xref:System.Activities.Statements.TransactionScope> activity to use transactions in a workflow.</span></span>  
  
 [<span data-ttu-id="74488-110">Compensação</span><span class="sxs-lookup"><span data-stu-id="74488-110">Compensation</span></span>](../../../docs/framework/windows-workflow-foundation/compensation.md)  
 <span data-ttu-id="74488-111">Descreve a compensação em fluxos de trabalho e demonstra como usar atividades de compensação como <xref:System.Activities.Statements.CompensableActivity>, <xref:System.Activities.Statements.Compensate>, e <xref:System.Activities.Statements.Confirm>.</span><span class="sxs-lookup"><span data-stu-id="74488-111">Describes compensation in workflows and demonstrates how to use compensation activities such as <xref:System.Activities.Statements.CompensableActivity>, <xref:System.Activities.Statements.Compensate>, and <xref:System.Activities.Statements.Confirm>.</span></span>  
  
 [<span data-ttu-id="74488-112">Cancelamento</span><span class="sxs-lookup"><span data-stu-id="74488-112">Cancellation</span></span>](../../../docs/framework/windows-workflow-foundation/modeling-cancellation-behavior-in-workflows.md)  
 <span data-ttu-id="74488-113">Descreve como executar manipulação cancelar em fluxos de trabalho usando atividades internos bem como atividades personalizados.</span><span class="sxs-lookup"><span data-stu-id="74488-113">Describes how to perform cancellation handling in workflows using built-in activities as well as custom activities.</span></span>  
  
 [<span data-ttu-id="74488-114">Depurando fluxos de trabalho</span><span class="sxs-lookup"><span data-stu-id="74488-114">Debugging Workflows</span></span>](../../../docs/framework/windows-workflow-foundation/debugging-workflows.md)  
 <span data-ttu-id="74488-115">Descreve como depurar fluxos de trabalho.</span><span class="sxs-lookup"><span data-stu-id="74488-115">Describes how to debug workflows.</span></span>
