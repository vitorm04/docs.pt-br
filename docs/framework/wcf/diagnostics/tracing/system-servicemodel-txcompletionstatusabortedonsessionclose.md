---
title: System.ServiceModel.TxCompletionStatusAbortedOnSessionClose
ms.date: 03/30/2017
ms.assetid: 7e142e9d-e81b-4309-974a-02e9cc064ea0
ms.openlocfilehash: 7ecc70f1c4d7184401dd29908968f628f2e6792a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="systemservicemodeltxcompletionstatusabortedonsessionclose"></a>System.ServiceModel.TxCompletionStatusAbortedOnSessionClose
A transação especificada foi anulada porque não estava concluída quando a sessão foi fechada e o TransactionAutoCompleteOnSessionClose OperationBehaviorAttribute foi definido como false.  
  
## <a name="description"></a>Descrição  
 Rastreado se a sessão ativa atual foi fechada e a transação não foi concluída e TransactionAutoCompleteOnSessionClose é definido como `false`.  
  
## <a name="troubleshooting"></a>Solução de problemas  
 Este rastreamento indica um bug potencial de aplicativo que deve ser investigado.  
  
## <a name="see-also"></a>Consulte também  
 [Rastreamento](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [Usando o rastreamento para solucionar problemas do seu aplicativo](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [Administração e diagnósticos](../../../../../docs/framework/wcf/diagnostics/index.md)
