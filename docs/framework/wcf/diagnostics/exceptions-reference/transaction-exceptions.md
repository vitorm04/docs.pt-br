---
title: "Exceções de transações"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1d27ed51-7eda-477f-9eca-94fa129f3e07
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c5896f1f7e15fa7ed86f80bbd7c06ae77faded90
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="transaction-exceptions"></a>Exceções de transações
Este tópico lista todas as exceções geradas pelo [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] transação.  
  
## <a name="exception-list"></a>Lista de exceções  
  
|Código do recurso|Cadeia de caracteres de recurso|  
|-------------------|---------------------|  
|SFxCannotHaveDifferentTransactionProtocolsInOneBinding|As informações de política que estão sendo importadas de metadados especificam valores diferentes para TransactionProtocol entre as operações. Há suporte para apenas um único TransactionProtocol para cada ponto de extremidade.|  
|SFxTransactionAutoCompleteFalseAndInstanceContextMode|TransactionAutoComplete não pode ser false, a menos que o InstanceContextMode do serviço é PerSession. Foi encontrado um erro na implementação do contrato especificado e operação.|  
|SFxTransactionInvalidSetTransactionComplete|OperationContext.SetTransactionComplete pode ser chamado em uma operação somente quando TransactionAutoComplete está definido como false e TransactionScopeRequired é definido como true. Este é um cenário inválido e a transação atual foi encerrada.|  
|TransactionFlowRequiredIssuedTokens|Para transmitir uma transação, o fluxo de tokens emitidos também deve ter suporte.|  
|TrustDriverVersionDoesNotSupportIssuedTokens|A versão de confiança configurada não oferece suporte a tokens emitidos. Use WSTrustFeb2005 ou superior.|
