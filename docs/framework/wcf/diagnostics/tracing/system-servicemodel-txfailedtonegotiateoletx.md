---
title: System.ServiceModel.TxFailedToNegotiateOleTx
ms.date: 03/30/2017
ms.assetid: 3f0f0b4b-a1ad-4704-8329-455daf54892d
ms.openlocfilehash: 2de1aa51d58d9d86f953e027fd3f7f172e3887d3
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59097558"
---
# <a name="systemservicemodeltxfailedtonegotiateoletx"></a>System.ServiceModel.TxFailedToNegotiateOleTx
A negociação de protocolo OleTransactions falhou na conclusão para o contexto de coordenação especificado.  
  
## <a name="description"></a>Descrição  
 Rastreada quando uma transação de entrada com as informações de OleTx não pode usar as informações de OleTx anexadas e será retorno usando WS-AT em vez disso.  
  
## <a name="troubleshooting"></a>Solução de problemas  
 Indica um possível problema com a comunicação de RPC MSDTC entre as máquinas. Se muitos desses rastreamentos aparecem no log, uma queda drástica no desempenho pode resultar.  Se OleTx não for desejado, defina `OleTxUpgradeEnabled` como 0 na configuração do registro WS-AT.  
  
## <a name="see-also"></a>Consulte também

- [Rastreamento](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [Utilizando o rastreamento para solucionar problemas em seu aplicativo](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [Administração e diagnósticos](../../../../../docs/framework/wcf/diagnostics/index.md)
