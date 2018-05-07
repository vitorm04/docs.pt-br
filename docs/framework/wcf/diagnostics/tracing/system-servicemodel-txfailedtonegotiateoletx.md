---
title: System.ServiceModel.TxFailedToNegotiateOleTx
ms.date: 03/30/2017
ms.assetid: 3f0f0b4b-a1ad-4704-8329-455daf54892d
ms.openlocfilehash: 7f376244343a75c16d5d2355642d626f666e42bb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="systemservicemodeltxfailedtonegotiateoletx"></a>System.ServiceModel.TxFailedToNegotiateOleTx
A negociação de protocolo OleTransactions não foi concluída para o contexto de coordenação especificado.  
  
## <a name="description"></a>Descrição  
 Rastreada quando uma transação de entrada com informações de OleTx não pode usar as informações de OleTx anexadas e será retorno usando o WS-AT em vez disso.  
  
## <a name="troubleshooting"></a>Solução de problemas  
 Indica um possível problema com a comunicação do MSDTC RPC entre os computadores. Se muitos esses rastreamentos aparecem no log, pode resultar uma redução significativa no desempenho.  Se OleTx não for desejada, defina `OleTxUpgradeEnabled` como 0 na configuração de registro do WS-AT.  
  
## <a name="see-also"></a>Consulte também  
 [Rastreamento](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [Usando o rastreamento para solucionar problemas do seu aplicativo](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [Administração e diagnósticos](../../../../../docs/framework/wcf/diagnostics/index.md)
