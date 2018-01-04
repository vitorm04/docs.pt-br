---
title: WCF e WebSockets
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1e53b49e-022c-49c7-8984-4b21b53c05b3
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e84bf7a94a6a6fa980e223daf0a6c7aaf489bb6e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="wcf-and-websockets"></a>WCF e WebSockets
O .NET Framework 4.5 introduz suporte para WebSockets no Windows Communication Foundation.  WebSockets é uma tecnologia eficiente e com base em padrões que permite a comunicação bidirecional sobre as portas HTTP padrão 80 e 443. O uso de portas HTTP padrão permite que o WebSockets comunique-se por meio da Web por meio de intermediários.  Duas novas associações padrão foram adicionadas à comunicação de suporte em um transporte de WebSocket. <xref:System.ServiceModel.NetHttpBinding> e <xref:System.ServiceModel.NetHttpsBinding>. Configurações específicas do WebSocket podem ser configuradas no <xref:System.ServiceModel.Channels.HttpTransportBindingElement> acessando o <xref:System.ServiceModel.Channels.HttpTransportBindingElement.WebSocketSettings%2A> propriedade.
  
## <a name="in-this-section"></a>Nesta seção  
 [Usando o NetHttpBinding](../../../../docs/framework/wcf/feature-details/using-the-nethttpbinding.md)  
 Discute o <xref:System.ServiceModel.NetHttpBinding> e como configurá-lo.  
  
 [Como criar um serviço WCF que se comunica por meio de WebSockets](../../../../docs/framework/wcf/feature-details/how-to-create-a-wcf-service-that-communicates-over-websockets.md)  
 Descreve como criar um serviço WCF que se comunica sobre Websockets.  
  
## <a name="reference"></a>Referência  
  
## <a name="related-sections"></a>Seções relacionadas
