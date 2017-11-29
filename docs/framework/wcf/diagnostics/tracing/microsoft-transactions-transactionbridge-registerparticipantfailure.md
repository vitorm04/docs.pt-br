---
title: Microsoft.Transactions.TransactionBridge.RegisterParticipantFailure
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3a4ead79-8550-4037-84e3-fd70ff56e001
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 2e3cbe9443f32ec9752198646e96cc1012d7343c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="microsofttransactionstransactionbridgeregisterparticipantfailure"></a>Microsoft.Transactions.TransactionBridge.RegisterParticipantFailure
Falha do serviço de protocolo WS-AT ao registrar um participante para um protocolo de controle.  
  
## <a name="description"></a>Descrição  
 Rastreadas se MSDTC detecta uma solicitação de registro inválida. Isso pode ser causado por várias solicitações de registro de conclusão e erros internos.  
  
## <a name="troubleshooting"></a>Solução de problemas  
 Não tente registrar-se para conclusão mais de uma vez.  Além disso, verifique a cadeia de caracteres de status dentro da mensagem de rastreamento para determinar se há qualquer item acionável.  
  
## <a name="see-also"></a>Consulte também  
 [Rastreamento](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [Usando o rastreamento para solucionar problemas de seu aplicativo](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [Administration and Diagnostics](../../../../../docs/framework/wcf/diagnostics/index.md) (Administração e diagnósticos)
