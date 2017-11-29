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
# <a name="adding-online-and-offline-status"></a><span data-ttu-id="e1782-102">Adicionando status online e offline</span><span class="sxs-lookup"><span data-stu-id="e1782-102">Adding Online and Offline Status</span></span>
<span data-ttu-id="e1782-103">Em muitos casos, é importante para um aplicativo para monitorar os detalhes específicos sobre o status de uma conexão de canal par.</span><span class="sxs-lookup"><span data-stu-id="e1782-103">In many cases, it is important for an application to monitor specific details about the status of a Peer Channel connection.</span></span> <span data-ttu-id="e1782-104">Você pode obter essas informações ao chamar o `GetProperty` método em uma implementação do <xref:System.ServiceModel.IOnlineStatus> interface.</span><span class="sxs-lookup"><span data-stu-id="e1782-104">You can obtain this information by calling the `GetProperty` method on an implementation of the <xref:System.ServiceModel.IOnlineStatus> interface.</span></span> <span data-ttu-id="e1782-105">Um objeto com uma implementação dessa interface pode monitorar o status de conexão ou se registrar manipuladores de eventos, como `OnOnline` e `OnOffline`e reagir imediatamente quando ocorrem alterações no status online.</span><span class="sxs-lookup"><span data-stu-id="e1782-105">An object with an implementation of this interface can monitor connection status or register for event handlers, such as `OnOnline` and `OnOffline`, and react immediately as changes to online status occur.</span></span>  
  
 <span data-ttu-id="e1782-106">Na infraestrutura de canal par, um cliente é considerado online se ele está conectado pelo menos um outro ponto e offline caso contrário.</span><span class="sxs-lookup"><span data-stu-id="e1782-106">In the Peer Channel infrastructure, a client is considered to be online if it is connected to at least one other peer and offline otherwise.</span></span> <span data-ttu-id="e1782-107">Isso pode ser especialmente útil em ambas depuração um desenvolvimento de aplicativos ou exibir informações detalhadas para o usuário final.</span><span class="sxs-lookup"><span data-stu-id="e1782-107">This can be particularly useful in both debugging a developing applications or displaying detailed information to the end user.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e1782-108">Um manipulador de eventos online deve certificar-se que o nó está aberto antes de enviar as mensagens.</span><span class="sxs-lookup"><span data-stu-id="e1782-108">An online event handler should first ensure that the node is open before sending any messages.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1782-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e1782-109">See Also</span></span>  
 [<span data-ttu-id="e1782-110">Criando um aplicativo de canal par</span><span class="sxs-lookup"><span data-stu-id="e1782-110">Building a Peer Channel Application</span></span>](../../../../docs/framework/wcf/feature-details/building-a-peer-channel-application.md)
