---
title: Adicionando status online e offline
ms.date: 03/30/2017
ms.assetid: 05e5f51d-81b6-4c17-b364-9dda447a5fce
ms.openlocfilehash: 74b113d64003756982a6b5701d9601c3116a9046
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69960653"
---
# <a name="adding-online-and-offline-status"></a><span data-ttu-id="ad756-102">Adicionando status online e offline</span><span class="sxs-lookup"><span data-stu-id="ad756-102">Adding Online and Offline Status</span></span>
<span data-ttu-id="ad756-103">Em muitos casos, é importante que um aplicativo monitore detalhes específicos sobre o status de uma conexão de canal de mesmo nível.</span><span class="sxs-lookup"><span data-stu-id="ad756-103">In many cases, it is important for an application to monitor specific details about the status of a Peer Channel connection.</span></span> <span data-ttu-id="ad756-104">Você pode obter essas informações chamando o `GetProperty` método em uma implementação <xref:System.ServiceModel.IOnlineStatus> da interface.</span><span class="sxs-lookup"><span data-stu-id="ad756-104">You can obtain this information by calling the `GetProperty` method on an implementation of the <xref:System.ServiceModel.IOnlineStatus> interface.</span></span> <span data-ttu-id="ad756-105">Um objeto com uma implementação dessa interface pode monitorar o status da conexão ou registrar-se para manipuladores de `OnOnline` eventos `OnOffline`, como e e reagir imediatamente conforme as alterações no status online ocorrem.</span><span class="sxs-lookup"><span data-stu-id="ad756-105">An object with an implementation of this interface can monitor connection status or register for event handlers, such as `OnOnline` and `OnOffline`, and react immediately as changes to online status occur.</span></span>  
  
 <span data-ttu-id="ad756-106">Na infraestrutura de canal par, um cliente será considerado online se estiver conectado a pelo menos um outro par e offline do contrário.</span><span class="sxs-lookup"><span data-stu-id="ad756-106">In the Peer Channel infrastructure, a client is considered to be online if it is connected to at least one other peer and offline otherwise.</span></span> <span data-ttu-id="ad756-107">Isso pode ser particularmente útil na depuração de aplicativos de desenvolvimento ou na exibição de informações detalhadas para o usuário final.</span><span class="sxs-lookup"><span data-stu-id="ad756-107">This can be particularly useful in both debugging a developing applications or displaying detailed information to the end user.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ad756-108">Um manipulador de eventos online deve primeiro garantir que o nó esteja aberto antes de enviar qualquer mensagem.</span><span class="sxs-lookup"><span data-stu-id="ad756-108">An online event handler should first ensure that the node is open before sending any messages.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad756-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ad756-109">See also</span></span>

- [<span data-ttu-id="ad756-110">Compilando um aplicativo de canal par</span><span class="sxs-lookup"><span data-stu-id="ad756-110">Building a Peer Channel Application</span></span>](../../../../docs/framework/wcf/feature-details/building-a-peer-channel-application.md)
