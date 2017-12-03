---
title: Implementando um proxy de descoberta
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: dda20e79-8df3-438e-a281-69d779d978ec
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 98affacf611ad31c7c3f8a93ff5793279a42a128
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="implementing-a-discovery-proxy"></a><span data-ttu-id="6e255-102">Implementando um proxy de descoberta</span><span class="sxs-lookup"><span data-stu-id="6e255-102">Implementing a Discovery Proxy</span></span>
<span data-ttu-id="6e255-103">Esta seção descreve as etapas necessárias para implementar um proxy de descoberta.</span><span class="sxs-lookup"><span data-stu-id="6e255-103">This section describes the steps required to implement a discovery proxy.</span></span> <span data-ttu-id="6e255-104">Um proxy de descoberta é um serviço autônomo que contém um repositório de serviços.</span><span class="sxs-lookup"><span data-stu-id="6e255-104">A discovery proxy is a standalone service that contains a repository of services.</span></span> <span data-ttu-id="6e255-105">Os clientes podem consultar um proxy de descoberta para localizar serviços detectáveis que o proxy está ciente do.</span><span class="sxs-lookup"><span data-stu-id="6e255-105">Clients can query a discovery proxy to find discoverable services that the proxy is aware of.</span></span> <span data-ttu-id="6e255-106">Como um proxy é populado com os serviços é o implementador.</span><span class="sxs-lookup"><span data-stu-id="6e255-106">How a proxy is populated with services is up to the implementer.</span></span> <span data-ttu-id="6e255-107">Por exemplo, um proxy de descoberta pode se conectar a um repositório de serviço existente e fazer essas informações detectáveis, um administrador pode usar uma API de gerenciamento para adicionar serviços de descoberta para um proxy ou um proxy de descoberta pode usar a funcionalidade de lançamento para Atualize seu cache interno.</span><span class="sxs-lookup"><span data-stu-id="6e255-107">For example, a discovery proxy can connect to an existing service repository and make that information discoverable, an administrator can use a management API to add discoverable services to a proxy, or a discovery proxy can use the announcement functionality to update its internal cache.</span></span>  
  
 <span data-ttu-id="6e255-108">A implementação de WCF fornece classes base que permitem que você crie facilmente um proxy.</span><span class="sxs-lookup"><span data-stu-id="6e255-108">The WCF implementation provides base classes that allow you to easily build a proxy.</span></span> <span data-ttu-id="6e255-109">Você pode usar essas APIs para criar um Proxy de descoberta sobre seu repositório existente.</span><span class="sxs-lookup"><span data-stu-id="6e255-109">You can utilize these APIs to build a Discovery Proxy on top of your existing repository.</span></span>  
  
 <span data-ttu-id="6e255-110">O proxy de descoberta implementado aqui é como qualquer outro serviço do WCF, você também pode fazer o proxy de descoberta podem ser descobertos e com que os clientes localizar seus pontos de extremidade.</span><span class="sxs-lookup"><span data-stu-id="6e255-110">The discovery proxy implemented here is like any other WCF services, in that you can also make the discovery proxy discoverable and have the clients locate its endpoints.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6e255-111">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="6e255-111">In This Section</span></span>  
 [<span data-ttu-id="6e255-112">Como: implementar um Proxy de descoberta</span><span class="sxs-lookup"><span data-stu-id="6e255-112">How to: Implement a Discovery Proxy</span></span>](../../../../docs/framework/wcf/feature-details/how-to-implement-a-discovery-proxy.md)  
 <span data-ttu-id="6e255-113">Descreve como implementar um proxy de descoberta.</span><span class="sxs-lookup"><span data-stu-id="6e255-113">Describes how to implement a discovery proxy.</span></span>  
  
 [<span data-ttu-id="6e255-114">Como: implementar um serviço de descoberta que registra com o Proxy de descoberta</span><span class="sxs-lookup"><span data-stu-id="6e255-114">How to: Implement a Discoverable Service that Registers with the Discovery Proxy</span></span>](../../../../docs/framework/wcf/feature-details/discoverable-service-that-registers-with-the-discovery-proxy.md)  
 <span data-ttu-id="6e255-115">Descreve como implementar um detectável [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviço registra com o proxy de descoberta.</span><span class="sxs-lookup"><span data-stu-id="6e255-115">Describes how to implement a discoverable [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service that registers with the discovery proxy.</span></span>  
  
 [<span data-ttu-id="6e255-116">Como: implementar um aplicativo cliente que usa o Proxy de descoberta para localizar um serviço</span><span class="sxs-lookup"><span data-stu-id="6e255-116">How to: Implement a Client Application that Uses the Discovery Proxy to Find a Service</span></span>](../../../../docs/framework/wcf/feature-details/client-app-discovery-proxy-to-find-a-service.md)  
 <span data-ttu-id="6e255-117">Descreve como implementar um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplicativo cliente que usa o proxy de descoberta para pesquisar para um serviço.</span><span class="sxs-lookup"><span data-stu-id="6e255-117">Describes how to implement a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client application that uses the discovery proxy to search for a service.</span></span>  
  
 [<span data-ttu-id="6e255-118">Como: testar o Proxy de descoberta</span><span class="sxs-lookup"><span data-stu-id="6e255-118">How to: Test the Discovery Proxy</span></span>](../../../../docs/framework/wcf/feature-details/how-to-test-the-discovery-proxy.md)  
 <span data-ttu-id="6e255-119">Descreve como testar o código escrito em três tópicos anteriores.</span><span class="sxs-lookup"><span data-stu-id="6e255-119">Describes how to test the code written in the previous three topics.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e255-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6e255-120">See Also</span></span>  
 [<span data-ttu-id="6e255-121">Descoberta do WCF</span><span class="sxs-lookup"><span data-stu-id="6e255-121">WCF Discovery</span></span>](../../../../docs/framework/wcf/feature-details/wcf-discovery.md)  
 [<span data-ttu-id="6e255-122">Como: adicionar programaticamente a capacidade de descoberta para um cliente e de serviço do WCF</span><span class="sxs-lookup"><span data-stu-id="6e255-122">How to: Programmatically Add Discoverability to a WCF Service and Client</span></span>](../../../../docs/framework/wcf/feature-details/how-to-programmatically-add-discoverability-to-a-wcf-service-and-client.md)
