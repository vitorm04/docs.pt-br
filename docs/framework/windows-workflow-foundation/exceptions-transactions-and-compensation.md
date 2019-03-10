---
title: Exceções, transações, e compensação
ms.date: 03/30/2017
helpviewer_keywords:
- programming [WF], error handling
ms.assetid: 694db4f9-7387-4b13-8f9f-b923b18c7490
ms.openlocfilehash: c4d66e252561ad7b896ff8092e80013c51bd463c
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57709465"
---
# <a name="exceptions-transactions-and-compensation"></a><span data-ttu-id="eca2c-102">Exceções, transações, e compensação</span><span class="sxs-lookup"><span data-stu-id="eca2c-102">Exceptions, Transactions, and Compensation</span></span>
[!INCLUDE[wf1](../../../includes/wf1-md.md)] <span data-ttu-id="eca2c-103">fornece vários mecanismos diferentes para manipular condições de erro em tempo de execução em fluxos de trabalho.</span><span class="sxs-lookup"><span data-stu-id="eca2c-103">provides several different mechanisms for handling run-time error conditions in workflows.</span></span> <span data-ttu-id="eca2c-104">Fluxos de trabalho podem usar uma combinação de manipuladores, de transações, de cancelar, e de compensação de exceção para manipular normalmente e recuperar as condições de erro.</span><span class="sxs-lookup"><span data-stu-id="eca2c-104">Workflows can use a combination of exception handlers, transactions, cancellation, and compensation to handle and recover gracefully from error conditions.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="eca2c-105">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="eca2c-105">In This Section</span></span>  
 [<span data-ttu-id="eca2c-106">Exceções</span><span class="sxs-lookup"><span data-stu-id="eca2c-106">Exceptions</span></span>](exceptions.md)  
 <span data-ttu-id="eca2c-107">Demonstra como usar a atividade de <xref:System.Activities.Statements.TryCatch> para tratar exceções em um fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="eca2c-107">Demonstrates how to use the <xref:System.Activities.Statements.TryCatch> activity to handle exceptions in a workflow.</span></span>  
  
 [<span data-ttu-id="eca2c-108">Transações</span><span class="sxs-lookup"><span data-stu-id="eca2c-108">Transactions</span></span>](workflow-transactions.md)  
 <span data-ttu-id="eca2c-109">Demonstra como usar a atividade de <xref:System.Activities.Statements.TransactionScope> para usar transações em um fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="eca2c-109">Demonstrates how to use the <xref:System.Activities.Statements.TransactionScope> activity to use transactions in a workflow.</span></span>  
  
 [<span data-ttu-id="eca2c-110">Compensação</span><span class="sxs-lookup"><span data-stu-id="eca2c-110">Compensation</span></span>](compensation.md)  
 <span data-ttu-id="eca2c-111">Descreve a compensação em fluxos de trabalho e demonstra como usar atividades de compensação como <xref:System.Activities.Statements.CompensableActivity>, <xref:System.Activities.Statements.Compensate>, e <xref:System.Activities.Statements.Confirm>.</span><span class="sxs-lookup"><span data-stu-id="eca2c-111">Describes compensation in workflows and demonstrates how to use compensation activities such as <xref:System.Activities.Statements.CompensableActivity>, <xref:System.Activities.Statements.Compensate>, and <xref:System.Activities.Statements.Confirm>.</span></span>  
  
 [<span data-ttu-id="eca2c-112">Cancelamento</span><span class="sxs-lookup"><span data-stu-id="eca2c-112">Cancellation</span></span>](modeling-cancellation-behavior-in-workflows.md)  
 <span data-ttu-id="eca2c-113">Descreve como executar manipulação cancelar em fluxos de trabalho usando atividades internos bem como atividades personalizados.</span><span class="sxs-lookup"><span data-stu-id="eca2c-113">Describes how to perform cancellation handling in workflows using built-in activities as well as custom activities.</span></span>  
  
 [<span data-ttu-id="eca2c-114">Depurando fluxos de trabalho</span><span class="sxs-lookup"><span data-stu-id="eca2c-114">Debugging Workflows</span></span>](debugging-workflows.md)  
 <span data-ttu-id="eca2c-115">Descreve como depurar fluxos de trabalho.</span><span class="sxs-lookup"><span data-stu-id="eca2c-115">Describes how to debug workflows.</span></span>
