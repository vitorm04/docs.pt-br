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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: be53af47aef4d42ddd2c77fbd29c8c9e9961c47b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
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
