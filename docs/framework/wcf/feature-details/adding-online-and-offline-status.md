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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 1a9f4cf65febd955e69d81f8dbb8f97aaa24e68c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="adding-online-and-offline-status"></a>Adicionando status online e offline
Em muitos casos, é importante para um aplicativo para monitorar os detalhes específicos sobre o status de uma conexão de canal par. Você pode obter essas informações ao chamar o `GetProperty` método em uma implementação do <xref:System.ServiceModel.IOnlineStatus> interface. Um objeto com uma implementação dessa interface pode monitorar o status de conexão ou se registrar manipuladores de eventos, como `OnOnline` e `OnOffline`e reagir imediatamente quando ocorrem alterações no status online.  
  
 Na infraestrutura de canal par, um cliente é considerado online se ele está conectado pelo menos um outro ponto e offline caso contrário. Isso pode ser especialmente útil em ambas depuração um desenvolvimento de aplicativos ou exibir informações detalhadas para o usuário final.  
  
> [!NOTE]
>  Um manipulador de eventos online deve certificar-se que o nó está aberto antes de enviar as mensagens.  
  
## <a name="see-also"></a>Consulte também  
 [Criando um aplicativo de canal par](../../../../docs/framework/wcf/feature-details/building-a-peer-channel-application.md)
