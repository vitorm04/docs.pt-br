---
title: Atividades de transação em WF
ms.date: 03/30/2017
ms.assetid: fb33378e-82c6-4ea0-870f-76dc77e7f0fe
ms.openlocfilehash: 7ffd64abdc6edf45174d4b756833d65ec0ef747c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61670255"
---
# <a name="transaction-activities-in-wf"></a>Atividades de transação em WF
[!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] tem vários sistema forneceu atividades modelando transações, compensação, e cancelar. Esses modelos de programação permitem que o fluxo de trabalho continue o progresso frente no caso de alterações na lógica comercial e no tratamento de erro. Para obter mais informações sobre transações, compensação e cancelamento, consulte [transações](workflow-transactions.md), [compensação](compensation.md), e [cancelamento](modeling-cancellation-behavior-in-workflows.md).  
  
## <a name="transaction-activities"></a>Atividades de transação  
  
|||  
|-|-|  
|<xref:System.Activities.Statements.CancellationScope>|Associa a lógica cancelar, na forma de uma atividade, com um caminho principal de execução, também expresso como uma atividade.|  
|<xref:System.Activities.Statements.CompensableActivity>|Oferece suporte a compensação das atividades filhos.|  
|<xref:System.Activities.Statements.Compensate>|Chama explicitamente o manipulador de compensação de <xref:System.Activities.Statements.CompensableActivity>.|  
|<xref:System.Activities.Statements.Confirm>|Chama explicitamente o manipulador de confirmação de <xref:System.Activities.Statements.CompensableActivity>.|  
|<xref:System.Activities.Statements.TransactionScope>|Delimita um limite de transação.|  
|<xref:System.ServiceModel.Activities.TransactedReceiveScope>|Defina o escopo o tempo de vida de uma transação que é iniciada por uma mensagem recebida. A transação pode ser fluída no fluxo de trabalho na mensagem iniciando, ou ser criada pelo distribuidor quando a mensagem é recebida. **Observação:**  O <xref:System.ServiceModel.Activities.TransactedReceiveScope> está localizado na **Messaging** seção o **caixa de ferramentas**.|
