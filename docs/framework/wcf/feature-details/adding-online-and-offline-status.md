---
title: Adicionando status online e offline
ms.date: 03/30/2017
ms.assetid: 05e5f51d-81b6-4c17-b364-9dda447a5fce
ms.openlocfilehash: 6a04648e4251774538d298b35d1d655e09e03495
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54591884"
---
# <a name="adding-online-and-offline-status"></a>Adicionando status online e offline
Em muitos casos, é importante para um aplicativo monitorar os detalhes específicos sobre o status de uma conexão de canal par. Você pode obter essas informações por meio da chamada a `GetProperty` método em uma implementação do <xref:System.ServiceModel.IOnlineStatus> interface. Um objeto com uma implementação dessa interface pode monitorar o status de conexão ou se registrar para manipuladores de eventos, tais como `OnOnline` e `OnOffline`e reagir imediatamente conforme ocorrem alterações no status online.  
  
 Na infra-estrutura de canal par, um cliente é considerado online se ele está conectado pelo menos um outro ponto e offline caso contrário. Isso pode ser especialmente útil em tanto um desenvolvimento de aplicativos de depuração ou exibir informações detalhadas para o usuário final.  
  
> [!NOTE]
>  Um manipulador de eventos online deve certificar-se que o nó está aberto antes de enviar todas as mensagens.  
  
## <a name="see-also"></a>Consulte também
- [Compilando um aplicativo de canal par](../../../../docs/framework/wcf/feature-details/building-a-peer-channel-application.md)
