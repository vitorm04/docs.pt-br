---
title: System.ServiceModel.Channels.PeerMaintainerActivity
ms.date: 03/30/2017
ms.assetid: ef28d086-d7fb-4e81-82e9-45a54647783b
ms.openlocfilehash: a7f353b00796c845f5686ca2926bbe7effe09e3e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33480578"
---
# <a name="systemservicemodelchannelspeermaintaineractivity"></a>System.ServiceModel.Channels.PeerMaintainerActivity
O módulo PeerMaintainer está executando uma operação específica (contidos no corpo da mensagem de rastreamento para obter detalhes).  
  
## <a name="description"></a>Descrição  
 Este rastreamento ocorre durante a várias operações PeerMaintainer.  
  
 PeerMaintainer é um componente interno de PeerNode. A cada minuto, ou cada 32 mensagens recebidas, ele envia uma mensagem LinkUtility para seus vizinhos com estatísticas sobre quantas mensagens são trocadas e quantas são úteis (não-duplicatas, tratamento). Isso ajuda a determinar o utilitário de Link de um vizinho específico. Aproximadamente a cada cinco minutos, o mantenedor verifica a integridade de conexões vizinhas. Se o número de conexões vizinhas excede a quantidade ideal, o mantenedor remove desativar as conexões menos úteis. Se não há conexões suficientes, o mantenedor adquire novas conexões.  
  
## <a name="see-also"></a>Consulte também  
 [Rastreamento](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [Usando o rastreamento para solucionar problemas do seu aplicativo](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [Administração e diagnósticos](../../../../../docs/framework/wcf/diagnostics/index.md)
