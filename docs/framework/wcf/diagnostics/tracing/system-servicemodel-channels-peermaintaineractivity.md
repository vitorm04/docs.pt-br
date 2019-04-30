---
title: System.ServiceModel.Channels.PeerMaintainerActivity
ms.date: 03/30/2017
ms.assetid: ef28d086-d7fb-4e81-82e9-45a54647783b
ms.openlocfilehash: ea4c8110a8f820e0c6204fbd22b3d5b747709fba
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61950456"
---
# <a name="systemservicemodelchannelspeermaintaineractivity"></a>System.ServiceModel.Channels.PeerMaintainerActivity
O módulo PeerMaintainer está executando uma operação específica (contidos no corpo da mensagem de rastreamento para obter detalhes).  
  
## <a name="description"></a>Descrição  
 Este rastreamento ocorre durante as várias operações de PeerMaintainer.  
  
 PeerMaintainer é um componente interno de PeerNode. A cada minuto, ou cada 32 mensagens recebidas, ele envia uma mensagem de LinkUtility para seus vizinhos com estatísticas sobre quantas mensagens são trocadas e quantos são úteis (não-duplicatas, tratamento). Isso ajuda a determinar o utilitário de Link de um vizinho específico. Aproximadamente a cada cinco minutos, o mantenedor verifica a integridade das conexões de vizinho. Se o número de conexões de vizinho exceder a quantidade ideal, o mantenedor remove desativar as conexões menos úteis. Se não há conexões suficientes, o mantenedor adquire novas conexões.  
  
## <a name="see-also"></a>Consulte também

- [Rastreamento](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [Usando o rastreamento para solucionar problemas do seu aplicativo](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [Administração e diagnósticos](../../../../../docs/framework/wcf/diagnostics/index.md)
