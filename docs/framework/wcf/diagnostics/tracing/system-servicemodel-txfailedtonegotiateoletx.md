---
title: System.ServiceModel.TxFailedToNegotiateOleTx
ms.date: 03/30/2017
ms.assetid: 3f0f0b4b-a1ad-4704-8329-455daf54892d
ms.openlocfilehash: 6aecc8f808d42c0096f6caef0574c72db6c53079
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54528652"
---
# <a name="systemservicemodeltxfailedtonegotiateoletx"></a>System.ServiceModel.TxFailedToNegotiateOleTx
A negociação de protocolo OleTransactions falhou na conclusão para o contexto de coordenação especificado.  
  
## <a name="description"></a>Descrição  
 Rastreada quando uma transação de entrada com as informações de OleTx não pode usar as informações de OleTx anexadas e será retorno usando WS-AT em vez disso.  
  
## <a name="troubleshooting"></a>Solução de problemas  
 Indica um possível problema com a comunicação de RPC MSDTC entre as máquinas. Se muitos desses rastreamentos aparecem no log, uma queda drástica no desempenho pode resultar.  Se OleTx não for desejado, defina `OleTxUpgradeEnabled` como 0 na configuração do registro WS-AT.  
  
## <a name="see-also"></a>Consulte também
- [Rastreamento](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [Usando o rastreamento para solucionar problemas do seu aplicativo](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [Administração e diagnósticos](../../../../../docs/framework/wcf/diagnostics/index.md)
