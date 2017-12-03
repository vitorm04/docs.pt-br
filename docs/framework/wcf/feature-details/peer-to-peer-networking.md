---
title: Rede peer-to-peer
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ad6cb67b-fd1c-4ca1-a767-b410da2e16ca
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d3ef21d4ab431ea4e1e1ac0392b3f088a7053c80
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="peer-to-peer-networking"></a><span data-ttu-id="45c85-102">Rede peer-to-peer</span><span class="sxs-lookup"><span data-stu-id="45c85-102">Peer-to-Peer Networking</span></span>
<span data-ttu-id="45c85-103">Canal par é uma tecnologia de comunicação (P2P) com vários participantes, ponto a ponto no [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="45c85-103">Peer Channel is a multiparty, peer-to-peer (P2P) communication technology in [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].</span></span> <span data-ttu-id="45c85-104">Ele fornece um seguro e escalonável com base em mensagem P2P canal de comunicação para os desenvolvedores de aplicativos.</span><span class="sxs-lookup"><span data-stu-id="45c85-104">It provides a secure and scalable message-based P2P communication channel for application developers.</span></span> <span data-ttu-id="45c85-105">Um exemplo comum de um aplicativo com vários participantes que pode se beneficiar de canal par é um aplicativo de colaboração, como bate-papo, quando um grupo de pessoas bate-papo entre si de maneira ponto a ponto, sem servidores.</span><span class="sxs-lookup"><span data-stu-id="45c85-105">One common example of a multiparty application that can benefit from Peer Channel is a collaborative application, such as chat, where a group of people chat with one another in a peer-to-peer manner without servers.</span></span> <span data-ttu-id="45c85-106">Canal par permite P2P colaboração, distribuição de conteúdo, balanceamento de carga e processamento distribuído para os cenários de consumidor e empresariais.</span><span class="sxs-lookup"><span data-stu-id="45c85-106">Peer Channel enables P2P collaboration, content distribution, load balancing, and distributed processing for both consumer and enterprise scenarios.</span></span>  
  
 <span data-ttu-id="45c85-107">Canal par é habilitado por padrão em [!INCLUDE[wv](../../../../includes/wv-md.md)], conforme são todos [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="45c85-107">Peer Channel is enabled by default on [!INCLUDE[wv](../../../../includes/wv-md.md)], as is all of [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span> <span data-ttu-id="45c85-108">Para acessar as classes de canal par, adicione referências a System.ServiceModel.dll para seu projeto.</span><span class="sxs-lookup"><span data-stu-id="45c85-108">To access Peer Channel classes, add references to System.ServiceModel.dll to your project.</span></span>  
  
 <span data-ttu-id="45c85-109">As seções a seguir contêm informações sobre rede ponto a ponto e o uso de classes de canal par para criar aplicativos de rede ponto a ponto.</span><span class="sxs-lookup"><span data-stu-id="45c85-109">The following sections contain information about peer-to-peer networking and the use of Peer Channel classes to create peer-enabled network applications.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="45c85-110">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="45c85-110">In This Section</span></span>  
 <span data-ttu-id="45c85-111">[Cenários de canal de mesmo nível](../../../../docs/framework/wcf/feature-details/peer-channel-scenarios.md): Descreve cenários de desenvolvimento com suporte das APIs de canal par, por exemplo, mensagens, colaboração, publicação/assinatura distribuídas de processamento e jogos.</span><span class="sxs-lookup"><span data-stu-id="45c85-111">[Peer Channel Scenarios](../../../../docs/framework/wcf/feature-details/peer-channel-scenarios.md):  Describes development scenarios supported by the Peer Channel APIs, such as publication/subscription messaging, collaboration, distributed processing, and gaming.</span></span>  
  
 <span data-ttu-id="45c85-112">[Conceitos de canal de mesmo nível](../../../../docs/framework/wcf/feature-details/peer-channel-concepts.md): descreve malhas de ponto a ponto, nós pares, segurança de canal par e resolvedor Peer.</span><span class="sxs-lookup"><span data-stu-id="45c85-112">[Peer Channel Concepts](../../../../docs/framework/wcf/feature-details/peer-channel-concepts.md):  Describes Peer Meshes, Peer Nodes, Peer Channel security, and Peer Resolvers.</span></span>  
  
 <span data-ttu-id="45c85-113">[Criando um aplicativo de canal par](../../../../docs/framework/wcf/feature-details/building-a-peer-channel-application.md): fornece orientação sobre como desenvolver aplicativos de canal par.</span><span class="sxs-lookup"><span data-stu-id="45c85-113">[Building a Peer Channel Application](../../../../docs/framework/wcf/feature-details/building-a-peer-channel-application.md):  Provides guidance on developing Peer Channel applications.</span></span>  
  
## <a name="peer-channel-code-examples"></a><span data-ttu-id="45c85-114">Exemplos de código de canal par</span><span class="sxs-lookup"><span data-stu-id="45c85-114">Peer Channel Code Examples</span></span>  
 [<span data-ttu-id="45c85-115">Resolvedor de pares personalizado de canal par</span><span class="sxs-lookup"><span data-stu-id="45c85-115">Peer Channel Custom Peer Resolver</span></span>](http://msdn.microsoft.com/en-us/5b75a2bb-7ff1-4a14-abe7-3debf0537d23)  
  
## <a name="peer-channel-team-blog"></a><span data-ttu-id="45c85-116">Blog da equipe do canal par</span><span class="sxs-lookup"><span data-stu-id="45c85-116">Peer Channel Team blog</span></span>  
 <span data-ttu-id="45c85-117">[Blog da equipe do canal par](http://go.microsoft.com/fwlink/?LinkID=114530) (http://go.microsoft.com/fwlink/?LinkID=114530)</span><span class="sxs-lookup"><span data-stu-id="45c85-117">[Peer Channel Team Blog](http://go.microsoft.com/fwlink/?LinkID=114530) (http://go.microsoft.com/fwlink/?LinkID=114530)</span></span>
