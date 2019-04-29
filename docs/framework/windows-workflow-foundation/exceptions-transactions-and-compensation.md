---
title: Exceções, transações, e compensação
ms.date: 03/30/2017
helpviewer_keywords:
- programming [WF], error handling
ms.assetid: 694db4f9-7387-4b13-8f9f-b923b18c7490
ms.openlocfilehash: c4d66e252561ad7b896ff8092e80013c51bd463c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61774004"
---
# <a name="exceptions-transactions-and-compensation"></a>Exceções, transações, e compensação
[!INCLUDE[wf1](../../../includes/wf1-md.md)] fornece vários mecanismos diferentes para manipular condições de erro em tempo de execução em fluxos de trabalho. Fluxos de trabalho podem usar uma combinação de manipuladores, de transações, de cancelar, e de compensação de exceção para manipular normalmente e recuperar as condições de erro.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Exceções](exceptions.md)  
 Demonstra como usar a atividade de <xref:System.Activities.Statements.TryCatch> para tratar exceções em um fluxo de trabalho.  
  
 [Transações](workflow-transactions.md)  
 Demonstra como usar a atividade de <xref:System.Activities.Statements.TransactionScope> para usar transações em um fluxo de trabalho.  
  
 [Compensação](compensation.md)  
 Descreve a compensação em fluxos de trabalho e demonstra como usar atividades de compensação como <xref:System.Activities.Statements.CompensableActivity>, <xref:System.Activities.Statements.Compensate>, e <xref:System.Activities.Statements.Confirm>.  
  
 [Cancelamento](modeling-cancellation-behavior-in-workflows.md)  
 Descreve como executar manipulação cancelar em fluxos de trabalho usando atividades internos bem como atividades personalizados.  
  
 [Depurando fluxos de trabalho](debugging-workflows.md)  
 Descreve como depurar fluxos de trabalho.
