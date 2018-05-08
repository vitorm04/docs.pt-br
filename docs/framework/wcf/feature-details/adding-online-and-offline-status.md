---
title: Adicionando status online e offline
ms.date: 03/30/2017
ms.assetid: 05e5f51d-81b6-4c17-b364-9dda447a5fce
ms.openlocfilehash: fb19614c1975c5634a81ca2f40edb145b724cd1d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="adding-online-and-offline-status"></a>Adicionando status online e offline
Em muitos casos, é importante para um aplicativo para monitorar os detalhes específicos sobre o status de uma conexão de canal par. Você pode obter essas informações ao chamar o `GetProperty` método em uma implementação do <xref:System.ServiceModel.IOnlineStatus> interface. Um objeto com uma implementação dessa interface pode monitorar o status de conexão ou se registrar manipuladores de eventos, como `OnOnline` e `OnOffline`e reagir imediatamente quando ocorrem alterações no status online.  
  
 Na infraestrutura de canal par, um cliente é considerado online se ele está conectado pelo menos um outro ponto e offline caso contrário. Isso pode ser especialmente útil em ambas depuração um desenvolvimento de aplicativos ou exibir informações detalhadas para o usuário final.  
  
> [!NOTE]
>  Um manipulador de eventos online deve certificar-se que o nó está aberto antes de enviar as mensagens.  
  
## <a name="see-also"></a>Consulte também  
 [Compilando um aplicativo de canal par](../../../../docs/framework/wcf/feature-details/building-a-peer-channel-application.md)
