---
title: Adicionando status online e offline
ms.date: 03/30/2017
ms.assetid: 05e5f51d-81b6-4c17-b364-9dda447a5fce
ms.openlocfilehash: da170bbc22d04dcbf5f7cd4ac084a004bb4b026e
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84597677"
---
# <a name="adding-online-and-offline-status"></a><span data-ttu-id="36d0c-102">Adicionando status online e offline</span><span class="sxs-lookup"><span data-stu-id="36d0c-102">Adding Online and Offline Status</span></span>
<span data-ttu-id="36d0c-103">Em muitos casos, é importante que um aplicativo monitore detalhes específicos sobre o status de uma conexão de canal de mesmo nível.</span><span class="sxs-lookup"><span data-stu-id="36d0c-103">In many cases, it is important for an application to monitor specific details about the status of a Peer Channel connection.</span></span> <span data-ttu-id="36d0c-104">Você pode obter essas informações chamando o `GetProperty` método em uma implementação da <xref:System.ServiceModel.IOnlineStatus> interface.</span><span class="sxs-lookup"><span data-stu-id="36d0c-104">You can obtain this information by calling the `GetProperty` method on an implementation of the <xref:System.ServiceModel.IOnlineStatus> interface.</span></span> <span data-ttu-id="36d0c-105">Um objeto com uma implementação dessa interface pode monitorar o status da conexão ou registrar-se para manipuladores de eventos, como `OnOnline` e e `OnOffline` reagir imediatamente conforme as alterações no status online ocorrem.</span><span class="sxs-lookup"><span data-stu-id="36d0c-105">An object with an implementation of this interface can monitor connection status or register for event handlers, such as `OnOnline` and `OnOffline`, and react immediately as changes to online status occur.</span></span>  
  
 <span data-ttu-id="36d0c-106">Na infraestrutura de canal par, um cliente será considerado online se estiver conectado a pelo menos um outro par e offline do contrário.</span><span class="sxs-lookup"><span data-stu-id="36d0c-106">In the Peer Channel infrastructure, a client is considered to be online if it is connected to at least one other peer and offline otherwise.</span></span> <span data-ttu-id="36d0c-107">Isso pode ser particularmente útil na depuração de aplicativos de desenvolvimento ou na exibição de informações detalhadas para o usuário final.</span><span class="sxs-lookup"><span data-stu-id="36d0c-107">This can be particularly useful in both debugging a developing applications or displaying detailed information to the end user.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="36d0c-108">Um manipulador de eventos online deve primeiro garantir que o nó esteja aberto antes de enviar qualquer mensagem.</span><span class="sxs-lookup"><span data-stu-id="36d0c-108">An online event handler should first ensure that the node is open before sending any messages.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36d0c-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="36d0c-109">See also</span></span>

- [<span data-ttu-id="36d0c-110">Compilando um aplicativo de canal par</span><span class="sxs-lookup"><span data-stu-id="36d0c-110">Building a Peer Channel Application</span></span>](building-a-peer-channel-application.md)
