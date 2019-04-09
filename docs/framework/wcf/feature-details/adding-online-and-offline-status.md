---
title: Adicionando status online e offline
ms.date: 03/30/2017
ms.assetid: 05e5f51d-81b6-4c17-b364-9dda447a5fce
ms.openlocfilehash: 15a963d4de0dcf1d7f0162b0a3266e17d4073ecd
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59147687"
---
# <a name="adding-online-and-offline-status"></a><span data-ttu-id="c3260-102">Adicionando status online e offline</span><span class="sxs-lookup"><span data-stu-id="c3260-102">Adding Online and Offline Status</span></span>
<span data-ttu-id="c3260-103">Em muitos casos, é importante para um aplicativo monitorar os detalhes específicos sobre o status de uma conexão de canal par.</span><span class="sxs-lookup"><span data-stu-id="c3260-103">In many cases, it is important for an application to monitor specific details about the status of a Peer Channel connection.</span></span> <span data-ttu-id="c3260-104">Você pode obter essas informações por meio da chamada a `GetProperty` método em uma implementação do <xref:System.ServiceModel.IOnlineStatus> interface.</span><span class="sxs-lookup"><span data-stu-id="c3260-104">You can obtain this information by calling the `GetProperty` method on an implementation of the <xref:System.ServiceModel.IOnlineStatus> interface.</span></span> <span data-ttu-id="c3260-105">Um objeto com uma implementação dessa interface pode monitorar o status de conexão ou se registrar para manipuladores de eventos, tais como `OnOnline` e `OnOffline`e reagir imediatamente conforme ocorrem alterações no status online.</span><span class="sxs-lookup"><span data-stu-id="c3260-105">An object with an implementation of this interface can monitor connection status or register for event handlers, such as `OnOnline` and `OnOffline`, and react immediately as changes to online status occur.</span></span>  
  
 <span data-ttu-id="c3260-106">Na infra-estrutura de canal par, um cliente é considerado online se ele está conectado pelo menos um outro ponto e offline caso contrário.</span><span class="sxs-lookup"><span data-stu-id="c3260-106">In the Peer Channel infrastructure, a client is considered to be online if it is connected to at least one other peer and offline otherwise.</span></span> <span data-ttu-id="c3260-107">Isso pode ser especialmente útil em tanto um desenvolvimento de aplicativos de depuração ou exibir informações detalhadas para o usuário final.</span><span class="sxs-lookup"><span data-stu-id="c3260-107">This can be particularly useful in both debugging a developing applications or displaying detailed information to the end user.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c3260-108">Um manipulador de eventos online deve certificar-se que o nó está aberto antes de enviar todas as mensagens.</span><span class="sxs-lookup"><span data-stu-id="c3260-108">An online event handler should first ensure that the node is open before sending any messages.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3260-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c3260-109">See also</span></span>

- [<span data-ttu-id="c3260-110">Compilando um aplicativo de canal par</span><span class="sxs-lookup"><span data-stu-id="c3260-110">Building a Peer Channel Application</span></span>](../../../../docs/framework/wcf/feature-details/building-a-peer-channel-application.md)
