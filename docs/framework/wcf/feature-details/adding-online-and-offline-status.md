---
title: Adicionando status online e offline
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 05e5f51d-81b6-4c17-b364-9dda447a5fce
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: adb767d3b7a7b991ebcfd8c44e55edb8726cb627
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="adding-online-and-offline-status"></a>Adicionando status online e offline
Em muitos casos, é importante para um aplicativo para monitorar os detalhes específicos sobre o status de uma conexão de canal par. Você pode obter essas informações ao chamar o `GetProperty` método em uma implementação do <xref:System.ServiceModel.IOnlineStatus> interface. Um objeto com uma implementação dessa interface pode monitorar o status de conexão ou se registrar manipuladores de eventos, como `OnOnline` e `OnOffline`e reagir imediatamente quando ocorrem alterações no status online.  
  
 Na infraestrutura de canal par, um cliente é considerado online se ele está conectado pelo menos um outro ponto e offline caso contrário. Isso pode ser especialmente útil em ambas depuração um desenvolvimento de aplicativos ou exibir informações detalhadas para o usuário final.  
  
> [!NOTE]
>  Um manipulador de eventos online deve certificar-se que o nó está aberto antes de enviar as mensagens.  
  
## <a name="see-also"></a>Consulte também  
 [Compilando um aplicativo de canal par](../../../../docs/framework/wcf/feature-details/building-a-peer-channel-application.md)
