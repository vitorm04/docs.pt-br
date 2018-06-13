---
title: Como testar o proxy de descoberta
ms.date: 03/30/2017
ms.assetid: d96e3fa2-3c42-4e5d-8244-2694081bdc32
ms.openlocfilehash: 35edbd03e912ae2d9c491afb28dee1c4a3055d14
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33491216"
---
# <a name="how-to-test-the-discovery-proxy"></a><span data-ttu-id="f21f8-102">Como testar o proxy de descoberta</span><span class="sxs-lookup"><span data-stu-id="f21f8-102">How to: Test the Discovery Proxy</span></span>
<span data-ttu-id="f21f8-103">Esta é a quarta de quatro tópicos que mostra como implementar um proxy de descoberta.</span><span class="sxs-lookup"><span data-stu-id="f21f8-103">This is the fourth of four topics that shows how to implement a discovery proxy.</span></span> <span data-ttu-id="f21f8-104">No tópico anterior, [como: implementar um aplicativo cliente que usa o Proxy de descoberta para localizar um serviço](../../../../docs/framework/wcf/feature-details/client-app-discovery-proxy-to-find-a-service.md), implementado um aplicativo de cliente do WCF que usa o proxy de descoberta para localizar um serviço e, em seguida, chama o serviço.</span><span class="sxs-lookup"><span data-stu-id="f21f8-104">In the previous topic, [How to: Implement a Client Application that Uses the Discovery Proxy to Find a Service](../../../../docs/framework/wcf/feature-details/client-app-discovery-proxy-to-find-a-service.md), you implemented a WCF client application that uses the discovery proxy to find a service and then calls the service.</span></span> <span data-ttu-id="f21f8-105">Este tópico descreve como verificar o proxy de descoberta, o serviço e o trabalho de aplicativo cliente, conforme o esperado.</span><span class="sxs-lookup"><span data-stu-id="f21f8-105">This topic describes how to verify the discovery proxy, the service, and the client application work as expected.</span></span>  
  
### <a name="run-the-discovery-proxy"></a><span data-ttu-id="f21f8-106">Executar o Proxy de descoberta</span><span class="sxs-lookup"><span data-stu-id="f21f8-106">Run the Discovery Proxy</span></span>  
  
1.  <span data-ttu-id="f21f8-107">Abra um prompt de comando como administrador.</span><span class="sxs-lookup"><span data-stu-id="f21f8-107">Open a command prompt as an administrator.</span></span>  
  
2.  <span data-ttu-id="f21f8-108">Você verá um diálogo que informa: Firewall do Windows bloqueou alguns recursos deste programa.</span><span class="sxs-lookup"><span data-stu-id="f21f8-108">You may see a dialog that says: Windows Firewall has blocked some features of this program.</span></span> <span data-ttu-id="f21f8-109">Se você vir essa mensagem, clique no **desbloquear** botão.</span><span class="sxs-lookup"><span data-stu-id="f21f8-109">If you see this message, click the **Unblock** button.</span></span>  
  
3.  <span data-ttu-id="f21f8-110">No prompt de comando, execute o proxy de descoberta, DiscoveryProxy.exe.</span><span class="sxs-lookup"><span data-stu-id="f21f8-110">Within the command prompt, run the discovery proxy, DiscoveryProxy.exe.</span></span>  
  
4.  <span data-ttu-id="f21f8-111">O aplicativo deve exibir o seguinte texto: `Proxy started. Hit Enter to exit`.</span><span class="sxs-lookup"><span data-stu-id="f21f8-111">The application should display the following text: `Proxy started. Hit Enter to exit`.</span></span>  
  
### <a name="run-the-discoverable-service"></a><span data-ttu-id="f21f8-112">Executar o serviço de descoberta</span><span class="sxs-lookup"><span data-stu-id="f21f8-112">Run the Discoverable Service</span></span>  
  
1.  <span data-ttu-id="f21f8-113">Abra um prompt de comando como administrador.</span><span class="sxs-lookup"><span data-stu-id="f21f8-113">Open a command prompt as an administrator.</span></span>  
  
2.  <span data-ttu-id="f21f8-114">No prompt de comando, execute o serviço detectável Service.exe.</span><span class="sxs-lookup"><span data-stu-id="f21f8-114">Within the command prompt, run the Service.exe discoverable service.</span></span>  
  
3.  <span data-ttu-id="f21f8-115">O DiscoveryProxy.exe devem exibir o seguinte texto: `******* Adding the following service: ** [Service Contract Name] ** [Service Endpoint Addr] 3.******* Done *******` .</span><span class="sxs-lookup"><span data-stu-id="f21f8-115">The DiscoveryProxy.exe should display the following text: `******* Adding the following service: ** [Service Contract Name] ** [Service Endpoint Addr] 3.******* Done *******` .</span></span>  
  
### <a name="run-the-client-application"></a><span data-ttu-id="f21f8-116">Executar o aplicativo cliente</span><span class="sxs-lookup"><span data-stu-id="f21f8-116">Run the Client Application</span></span>  
  
1.  <span data-ttu-id="f21f8-117">Abra um prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="f21f8-117">Open a command prompt.</span></span>  
  
2.  <span data-ttu-id="f21f8-118">No prompt de comando, execute o aplicativo client.exe.</span><span class="sxs-lookup"><span data-stu-id="f21f8-118">Within the command prompt, run the client.exe application.</span></span>  
  
3.  <span data-ttu-id="f21f8-119">Depois de alguns segundos, o aplicativo cliente exibe o seguinte texto: conectar-se a [serviço de ponto de extremidade].</span><span class="sxs-lookup"><span data-stu-id="f21f8-119">After a few seconds the client application displays the following text: Connecting to [Service-Endpoint].</span></span>  
  
4.  <span data-ttu-id="f21f8-120">O service.exe deve exibir o seguinte texto: saudação solicitação recebida, I responderá.</span><span class="sxs-lookup"><span data-stu-id="f21f8-120">The service.exe should then display the following text: Greeting request received, I will respond.</span></span>  
  
5.  <span data-ttu-id="f21f8-121">O client.exe deve exibir o seguinte texto: cliente Olá!</span><span class="sxs-lookup"><span data-stu-id="f21f8-121">The client.exe should then display the following text: Hello Client!</span></span>  
  
### <a name="shut-down-the-applications"></a><span data-ttu-id="f21f8-122">Desligar os aplicativos</span><span class="sxs-lookup"><span data-stu-id="f21f8-122">Shut Down the Applications</span></span>  
  
1.  <span data-ttu-id="f21f8-123">Desligar o aplicativo cliente.</span><span class="sxs-lookup"><span data-stu-id="f21f8-123">Shut down the client application.</span></span>  
  
2.  <span data-ttu-id="f21f8-124">Desligar o serviço.</span><span class="sxs-lookup"><span data-stu-id="f21f8-124">Shut down the service.</span></span> <span data-ttu-id="f21f8-125">O proxy de descoberta exibe o seguinte texto: `******* Removing the following service: ** [Service Contract Name] ** [Service Endpoint Addr] 2.3.******* Done *******`.</span><span class="sxs-lookup"><span data-stu-id="f21f8-125">The discovery proxy displays the following text: `******* Removing the following service: ** [Service Contract Name] ** [Service Endpoint Addr] 2.3.******* Done *******`.</span></span>  
  
3.  <span data-ttu-id="f21f8-126">Desligar o proxy de descoberta.</span><span class="sxs-lookup"><span data-stu-id="f21f8-126">Shut down the discovery proxy.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f21f8-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f21f8-127">See Also</span></span>  
 [<span data-ttu-id="f21f8-128">Visão geral de descoberta do WCF</span><span class="sxs-lookup"><span data-stu-id="f21f8-128">WCF Discovery Overview</span></span>](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md)  
 [<span data-ttu-id="f21f8-129">Como implementar um proxy de descoberta</span><span class="sxs-lookup"><span data-stu-id="f21f8-129">How to: Implement a Discovery Proxy</span></span>](../../../../docs/framework/wcf/feature-details/how-to-implement-a-discovery-proxy.md)  
 [<span data-ttu-id="f21f8-130">Como implementar um serviço de descoberta que registra usando o proxy de descoberta</span><span class="sxs-lookup"><span data-stu-id="f21f8-130">How to: Implement a Discoverable Service that Registers with the Discovery Proxy</span></span>](../../../../docs/framework/wcf/feature-details/discoverable-service-that-registers-with-the-discovery-proxy.md)  
 [<span data-ttu-id="f21f8-131">Como implementar um aplicativo cliente que usa o proxy de descoberta para localizar um serviço</span><span class="sxs-lookup"><span data-stu-id="f21f8-131">How to: Implement a Client Application that Uses the Discovery Proxy to Find a Service</span></span>](../../../../docs/framework/wcf/feature-details/client-app-discovery-proxy-to-find-a-service.md)
