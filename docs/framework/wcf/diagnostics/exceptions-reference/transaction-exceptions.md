---
title: Exceções de transações
ms.date: 03/30/2017
ms.assetid: 1d27ed51-7eda-477f-9eca-94fa129f3e07
ms.openlocfilehash: 85d8d043a5610743d6cbad4d950330ed4bedb502
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="transaction-exceptions"></a>Exceções de transações
Este tópico lista todas as exceções geradas por transações do Windows Communication Foundation (WCF).  
  
## <a name="exception-list"></a>Lista de exceções  
  
|Código do recurso|Cadeia de caracteres de recurso|  
|-------------------|---------------------|  
|SFxCannotHaveDifferentTransactionProtocolsInOneBinding|As informações de política que estão sendo importadas de metadados especificam valores diferentes para TransactionProtocol entre as operações. Há suporte para apenas um único TransactionProtocol para cada ponto de extremidade.|  
|SFxTransactionAutoCompleteFalseAndInstanceContextMode|TransactionAutoComplete não pode ser false, a menos que o InstanceContextMode do serviço é PerSession. Foi encontrado um erro na implementação do contrato especificado e operação.|  
|SFxTransactionInvalidSetTransactionComplete|OperationContext.SetTransactionComplete pode ser chamado em uma operação somente quando TransactionAutoComplete está definido como false e TransactionScopeRequired é definido como true. Este é um cenário inválido e a transação atual foi encerrada.|  
|TransactionFlowRequiredIssuedTokens|Para transmitir uma transação, o fluxo de tokens emitidos também deve ter suporte.|  
|TrustDriverVersionDoesNotSupportIssuedTokens|A versão de confiança configurada não oferece suporte a tokens emitidos. Use WSTrustFeb2005 ou superior.|
