---
title: System.ServiceModel.Channels.PeerFlooderReceiveMessageQuotaExceeded
ms.date: 03/30/2017
ms.assetid: b8371d0a-843e-440b-b86a-6996db131cb0
ms.openlocfilehash: 0ca3d198ce225221348ac7b405ea91ad215cd298
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61950638"
---
# <a name="systemservicemodelchannelspeerflooderreceivemessagequotaexceeded"></a>System.ServiceModel.Channels.PeerFlooderReceiveMessageQuotaExceeded
A taxa de entrada de recebimento de mensagens é muito alta.  
  
## <a name="description"></a>Descrição  
 Este rastreamento ocorre ao tentar processar as mensagens de entrada. Uma mensagem não pôde ser encaminhada para um vizinho específico porque a cota definida para aquele vizinho foi excedida. Isso ocorre quando um vizinho sem resposta Falha ao limpar uma lista de pendências de mensagens pendentes para aquele vizinho.  
  
## <a name="troubleshooting"></a>Solução de problemas  
 Reduza a taxa na qual as mensagens são enviadas dentro da malha.  
  
## <a name="see-also"></a>Consulte também

- [Rastreamento](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [Usando o rastreamento para solucionar problemas do seu aplicativo](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [Administração e diagnósticos](../../../../../docs/framework/wcf/diagnostics/index.md)
