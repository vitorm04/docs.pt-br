---
title: Implementando um proxy de descoberta
ms.date: 03/30/2017
ms.assetid: dda20e79-8df3-438e-a281-69d779d978ec
ms.openlocfilehash: 5d9296d8ba70d4c9e8d8339fa3a032d9c4c62826
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59140992"
---
# <a name="implementing-a-discovery-proxy"></a><span data-ttu-id="c7d14-102">Implementando um proxy de descoberta</span><span class="sxs-lookup"><span data-stu-id="c7d14-102">Implementing a Discovery Proxy</span></span>
<span data-ttu-id="c7d14-103">Esta seção descreve as etapas necessárias para implementar um proxy de descoberta.</span><span class="sxs-lookup"><span data-stu-id="c7d14-103">This section describes the steps required to implement a discovery proxy.</span></span> <span data-ttu-id="c7d14-104">Um proxy de descoberta é um serviço autônomo que contém um repositório de serviços.</span><span class="sxs-lookup"><span data-stu-id="c7d14-104">A discovery proxy is a standalone service that contains a repository of services.</span></span> <span data-ttu-id="c7d14-105">Os clientes podem consultar um proxy de descoberta para localizar serviços podem ser descobertos que o proxy está ciente.</span><span class="sxs-lookup"><span data-stu-id="c7d14-105">Clients can query a discovery proxy to find discoverable services that the proxy is aware of.</span></span> <span data-ttu-id="c7d14-106">Como um proxy é preenchido com os serviços cabe ao implementador.</span><span class="sxs-lookup"><span data-stu-id="c7d14-106">How a proxy is populated with services is up to the implementer.</span></span> <span data-ttu-id="c7d14-107">Por exemplo, um proxy de descoberta pode se conectar a um repositório de serviço existente e tornar essas informações detectáveis, um administrador pode usar uma API de gerenciamento para adicionar serviços podem ser descobertos para um proxy ou um proxy de descoberta pode usar a funcionalidade de anúncio Atualize seu cache interno.</span><span class="sxs-lookup"><span data-stu-id="c7d14-107">For example, a discovery proxy can connect to an existing service repository and make that information discoverable, an administrator can use a management API to add discoverable services to a proxy, or a discovery proxy can use the announcement functionality to update its internal cache.</span></span>  
  
 <span data-ttu-id="c7d14-108">A implementação do WCF fornece as classes base que permitem que você crie facilmente um proxy.</span><span class="sxs-lookup"><span data-stu-id="c7d14-108">The WCF implementation provides base classes that allow you to easily build a proxy.</span></span> <span data-ttu-id="c7d14-109">Você pode usar essas APIs para criar um Proxy de descoberta na parte superior de seu repositório existente.</span><span class="sxs-lookup"><span data-stu-id="c7d14-109">You can utilize these APIs to build a Discovery Proxy on top of your existing repository.</span></span>  
  
 <span data-ttu-id="c7d14-110">O proxy de descoberta implementado aqui é como qualquer outro serviço do WCF, em que você também pode fazer o proxy de descoberta podem ser descobertos e fazer com que os clientes localizar seus pontos de extremidade.</span><span class="sxs-lookup"><span data-stu-id="c7d14-110">The discovery proxy implemented here is like any other WCF services, in that you can also make the discovery proxy discoverable and have the clients locate its endpoints.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c7d14-111">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="c7d14-111">In This Section</span></span>  
 [<span data-ttu-id="c7d14-112">Como: implementar um proxy de descoberta</span><span class="sxs-lookup"><span data-stu-id="c7d14-112">How to: Implement a Discovery Proxy</span></span>](../../../../docs/framework/wcf/feature-details/how-to-implement-a-discovery-proxy.md)  
 <span data-ttu-id="c7d14-113">Descreve como implementar um proxy de descoberta.</span><span class="sxs-lookup"><span data-stu-id="c7d14-113">Describes how to implement a discovery proxy.</span></span>  
  
 [<span data-ttu-id="c7d14-114">Como: implementar um serviço de descoberta que registra usando o proxy de descoberta</span><span class="sxs-lookup"><span data-stu-id="c7d14-114">How to: Implement a Discoverable Service that Registers with the Discovery Proxy</span></span>](../../../../docs/framework/wcf/feature-details/discoverable-service-that-registers-with-the-discovery-proxy.md)  
 <span data-ttu-id="c7d14-115">Descreve como implementar um serviço WCF de descoberta que registra com o proxy de descoberta.</span><span class="sxs-lookup"><span data-stu-id="c7d14-115">Describes how to implement a discoverable WCF service that registers with the discovery proxy.</span></span>  
  
 [<span data-ttu-id="c7d14-116">Como: implementar um aplicativo cliente que utiliza o proxy de descoberta para encontrar um serviço</span><span class="sxs-lookup"><span data-stu-id="c7d14-116">How to: Implement a Client Application that Uses the Discovery Proxy to Find a Service</span></span>](../../../../docs/framework/wcf/feature-details/client-app-discovery-proxy-to-find-a-service.md)  
 <span data-ttu-id="c7d14-117">Descreve como implementar um aplicativo de cliente do WCF que usa o proxy de descoberta para pesquisar para um serviço.</span><span class="sxs-lookup"><span data-stu-id="c7d14-117">Describes how to implement a WCF client application that uses the discovery proxy to search for a service.</span></span>  
  
 [<span data-ttu-id="c7d14-118">Como: testar o proxy de descoberta</span><span class="sxs-lookup"><span data-stu-id="c7d14-118">How to: Test the Discovery Proxy</span></span>](../../../../docs/framework/wcf/feature-details/how-to-test-the-discovery-proxy.md)  
 <span data-ttu-id="c7d14-119">Descreve como testar o código escrito em três tópicos anteriores.</span><span class="sxs-lookup"><span data-stu-id="c7d14-119">Describes how to test the code written in the previous three topics.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7d14-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c7d14-120">See also</span></span>

- [<span data-ttu-id="c7d14-121">Descoberta de WCF</span><span class="sxs-lookup"><span data-stu-id="c7d14-121">WCF Discovery</span></span>](../../../../docs/framework/wcf/feature-details/wcf-discovery.md)
- [<span data-ttu-id="c7d14-122">Como: adicionar programaticamente a capacidade de descoberta para um cliente e serviço do WCF</span><span class="sxs-lookup"><span data-stu-id="c7d14-122">How to: Programmatically Add Discoverability to a WCF Service and Client</span></span>](../../../../docs/framework/wcf/feature-details/how-to-programmatically-add-discoverability-to-a-wcf-service-and-client.md)
