---
title: Exceções de transações
ms.date: 03/30/2017
ms.assetid: 1d27ed51-7eda-477f-9eca-94fa129f3e07
ms.openlocfilehash: 85d8d043a5610743d6cbad4d950330ed4bedb502
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61936963"
---
# <a name="transaction-exceptions"></a>Exceções de transações
Este tópico lista todas as exceções geradas por transação do Windows Communication Foundation (WCF).  
  
## <a name="exception-list"></a>Lista de exceções  
  
|Código do recurso|Cadeia de caracteres de recurso|  
|-------------------|---------------------|  
|SFxCannotHaveDifferentTransactionProtocolsInOneBinding|As informações de política que está sendo importadas dos metadados especificam valores diferentes para TransactionProtocol entre as operações. Há suporte para apenas um único TransactionProtocol para cada ponto de extremidade.|  
|SFxTransactionAutoCompleteFalseAndInstanceContextMode|TransactionAutoComplete não pode ser false, a menos que InstanceContextMode do serviço é PerSession. Um erro foi encontrado na implementação do contrato especificado e operação.|  
|SFxTransactionInvalidSetTransactionComplete|OperationContext.SetTransactionComplete pode ser chamado em uma operação somente quando TransactionAutoComplete é definido como false e TransactionScopeRequired é definido como true. Esse é um cenário inválido e a transação atual foi encerrada.|  
|TransactionFlowRequiredIssuedTokens|Para fazer fluir uma transação, o fluindo tokens emitidos também deve ter suporte.|  
|TrustDriverVersionDoesNotSupportIssuedTokens|A versão da confiança configurada não oferece suporte a tokens emitidos. Use WSTrustFeb2005 ou posterior.|
