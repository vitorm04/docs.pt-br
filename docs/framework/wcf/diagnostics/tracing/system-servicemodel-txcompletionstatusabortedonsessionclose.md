---
title: System.ServiceModel.TxCompletionStatusAbortedOnSessionClose
ms.date: 03/30/2017
ms.assetid: 7e142e9d-e81b-4309-974a-02e9cc064ea0
ms.openlocfilehash: 7b1f6a2f4a344b566c76d0095942b84a8a4e76f6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59166498"
---
# <a name="systemservicemodeltxcompletionstatusabortedonsessionclose"></a>System.ServiceModel.TxCompletionStatusAbortedOnSessionClose
A transação especificada foi anulada porque estava incompleta quando a sessão foi fechada e TransactionAutoCompleteOnSessionClose OperationBehaviorAttribute foi definida como false.  
  
## <a name="description"></a>Descrição  
 Rastreados se a sessão ativa atual foi fechada e a transação não foi concluída e TransactionAutoCompleteOnSessionClose é definida como `false`.  
  
## <a name="troubleshooting"></a>Solução de problemas  
 Este rastreamento indica um bug potencial do aplicativo que deve ser investigado.  
  
## <a name="see-also"></a>Consulte também

- [Rastreamento](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [Utilizando o rastreamento para solucionar problemas em seu aplicativo](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [Administração e diagnósticos](../../../../../docs/framework/wcf/diagnostics/index.md)
