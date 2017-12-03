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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7fab7247540ba4e098a793adebab54ca4219e503
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="exceptions-transactions-and-compensation"></a>Exceções, transações, e compensação
[!INCLUDE[wf1](../../../includes/wf1-md.md)] fornece vários mecanismos diferentes para manipular condições de erro em tempo de execução em fluxos de trabalho. Fluxos de trabalho podem usar uma combinação de manipuladores, de transações, de cancelar, e de compensação de exceção para manipular normalmente e recuperar as condições de erro.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Exceções](../../../docs/framework/windows-workflow-foundation/exceptions.md)  
 Demonstra como usar a atividade de <xref:System.Activities.Statements.TryCatch> para tratar exceções em um fluxo de trabalho.  
  
 [Transações](../../../docs/framework/windows-workflow-foundation/workflow-transactions.md)  
 Demonstra como usar a atividade de <xref:System.Activities.Statements.TransactionScope> para usar transações em um fluxo de trabalho.  
  
 [Compensação](../../../docs/framework/windows-workflow-foundation/compensation.md)  
 Descreve a compensação em fluxos de trabalho e demonstra como usar atividades de compensação como <xref:System.Activities.Statements.CompensableActivity>, <xref:System.Activities.Statements.Compensate>, e <xref:System.Activities.Statements.Confirm>.  
  
 [Cancelamento](../../../docs/framework/windows-workflow-foundation/modeling-cancellation-behavior-in-workflows.md)  
 Descreve como executar manipulação cancelar em fluxos de trabalho usando atividades internos bem como atividades personalizados.  
  
 [Depurando fluxos de trabalho](../../../docs/framework/windows-workflow-foundation/debugging-workflows.md)  
 Descreve como depurar fluxos de trabalho.
