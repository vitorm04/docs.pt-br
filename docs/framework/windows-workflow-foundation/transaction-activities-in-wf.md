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
# <a name="transaction-activities-in-wf"></a>Atividades de transação em WF
[!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] tem vários sistema forneceu atividades modelando transações, compensação, e cancelar. Esses modelos de programação permitem que o fluxo de trabalho continue o progresso frente no caso de alterações na lógica comercial e no tratamento de erro. [!INCLUDE[crabout](../../../includes/crabout-md.md)]transações de compensação e cancelamento, consulte [transações](../../../docs/framework/windows-workflow-foundation/workflow-transactions.md), [compensação](../../../docs/framework/windows-workflow-foundation/compensation.md), e [cancelamento](../../../docs/framework/windows-workflow-foundation/modeling-cancellation-behavior-in-workflows.md).  
  
## <a name="transaction-activities"></a>Atividades de transação  
  
|||  
|-|-|  
|<xref:System.Activities.Statements.CancellationScope>|Associa a lógica cancelar, na forma de uma atividade, com um caminho principal de execução, também expresso como uma atividade.|  
|<xref:System.Activities.Statements.CompensableActivity>|Oferece suporte a compensação das atividades filhos.|  
|<xref:System.Activities.Statements.Compensate>|Chama explicitamente o manipulador de compensação de <xref:System.Activities.Statements.CompensableActivity>.|  
|<xref:System.Activities.Statements.Confirm>|Chama explicitamente o manipulador de confirmação de <xref:System.Activities.Statements.CompensableActivity>.|  
|<xref:System.Activities.Statements.TransactionScope>|Delimita um limite de transação.|  
|<xref:System.ServiceModel.Activities.TransactedReceiveScope>|Defina o escopo o tempo de vida de uma transação que é iniciada por uma mensagem recebida. A transação pode ser fluída no fluxo de trabalho na mensagem iniciando, ou ser criada pelo distribuidor quando a mensagem é recebida. **Observação:** o <xref:System.ServiceModel.Activities.TransactedReceiveScope> está localizado no **mensagens** seção o **caixa de ferramentas**.|
