---
title: System.ServiceModel.Channels.TcpConnectError
ms.date: 03/30/2017
ms.assetid: 22d93797-072e-405d-a3e0-5c519ddf290b
ms.openlocfilehash: 0bfd35e2b3ca421745701a91f2a5bfc91f3063aa
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59091441"
---
# <a name="systemservicemodelchannelstcpconnecterror"></a>System.ServiceModel.Channels.TcpConnectError
Falha na operação de conexão TCP.  
  
## <a name="description"></a>Descrição  
 Rastreamento de nível de aviso indica uma falha ao se conectar a um ponto de extremidade TCP. Isso pode acontecer se o ponto de extremidade remoto não está respondendo em um determinado endereço IP e porta. Este rastreamento pode ser ignorado se subsequentes tenta se conectar a outro IP válido endereços (por exemplo, endereços IPv4 ou IPv6, ou outros endereços IP que representa um determinado nome de host) tenha êxito. A exceção dentro desse rastreamento pode revelar informações adicionais sobre o erro.  
  
## <a name="see-also"></a>Consulte também

- [Rastreamento](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [Usando o rastreamento para solucionar problemas do seu aplicativo](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [Administração e diagnósticos](../../../../../docs/framework/wcf/diagnostics/index.md)
