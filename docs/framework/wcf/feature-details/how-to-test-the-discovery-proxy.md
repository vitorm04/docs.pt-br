---
title: 'Como: O Proxy de descoberta de teste'
ms.date: 03/30/2017
ms.assetid: d96e3fa2-3c42-4e5d-8244-2694081bdc32
ms.openlocfilehash: 3c159481813266386706b34d172bbf9614a8253d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54590507"
---
# <a name="how-to-test-the-discovery-proxy"></a><span data-ttu-id="21bdb-102">Como: O Proxy de descoberta de teste</span><span class="sxs-lookup"><span data-stu-id="21bdb-102">How to: Test the Discovery Proxy</span></span>
<span data-ttu-id="21bdb-103">Esta é a quarta de quatro tópicos que mostra como implementar um proxy de descoberta.</span><span class="sxs-lookup"><span data-stu-id="21bdb-103">This is the fourth of four topics that shows how to implement a discovery proxy.</span></span> <span data-ttu-id="21bdb-104">No tópico anterior, [como: Implementar um aplicativo cliente que usa o Proxy de descoberta para localizar um serviço](../../../../docs/framework/wcf/feature-details/client-app-discovery-proxy-to-find-a-service.md), você implementou um aplicativo de cliente do WCF que usa o proxy de descoberta para localizar um serviço e, em seguida, chama o serviço.</span><span class="sxs-lookup"><span data-stu-id="21bdb-104">In the previous topic, [How to: Implement a Client Application that Uses the Discovery Proxy to Find a Service](../../../../docs/framework/wcf/feature-details/client-app-discovery-proxy-to-find-a-service.md), you implemented a WCF client application that uses the discovery proxy to find a service and then calls the service.</span></span> <span data-ttu-id="21bdb-105">Este tópico descreve como verificar o proxy de descoberta, o serviço e o trabalho do aplicativo cliente, conforme o esperado.</span><span class="sxs-lookup"><span data-stu-id="21bdb-105">This topic describes how to verify the discovery proxy, the service, and the client application work as expected.</span></span>  
  
### <a name="run-the-discovery-proxy"></a><span data-ttu-id="21bdb-106">Executar o Proxy de descoberta</span><span class="sxs-lookup"><span data-stu-id="21bdb-106">Run the Discovery Proxy</span></span>  
  
1.  <span data-ttu-id="21bdb-107">Abra um prompt de comando como administrador.</span><span class="sxs-lookup"><span data-stu-id="21bdb-107">Open a command prompt as an administrator.</span></span>  
  
2.  <span data-ttu-id="21bdb-108">Você poderá ver uma caixa de diálogo que diz: Firewall do Windows bloqueou alguns recursos deste programa.</span><span class="sxs-lookup"><span data-stu-id="21bdb-108">You may see a dialog that says: Windows Firewall has blocked some features of this program.</span></span> <span data-ttu-id="21bdb-109">Se você vir essa mensagem, clique o **Unblock** botão.</span><span class="sxs-lookup"><span data-stu-id="21bdb-109">If you see this message, click the **Unblock** button.</span></span>  
  
3.  <span data-ttu-id="21bdb-110">No prompt de comando, execute o proxy de descoberta, DiscoveryProxy.exe.</span><span class="sxs-lookup"><span data-stu-id="21bdb-110">Within the command prompt, run the discovery proxy, DiscoveryProxy.exe.</span></span>  
  
4.  <span data-ttu-id="21bdb-111">O aplicativo deve exibir o seguinte texto: `Proxy started. Hit Enter to exit`.</span><span class="sxs-lookup"><span data-stu-id="21bdb-111">The application should display the following text: `Proxy started. Hit Enter to exit`.</span></span>  
  
### <a name="run-the-discoverable-service"></a><span data-ttu-id="21bdb-112">Executar o serviço de descoberta</span><span class="sxs-lookup"><span data-stu-id="21bdb-112">Run the Discoverable Service</span></span>  
  
1.  <span data-ttu-id="21bdb-113">Abra um prompt de comando como administrador.</span><span class="sxs-lookup"><span data-stu-id="21bdb-113">Open a command prompt as an administrator.</span></span>  
  
2.  <span data-ttu-id="21bdb-114">No prompt de comando, execute o serviço de descoberta Service.exe.</span><span class="sxs-lookup"><span data-stu-id="21bdb-114">Within the command prompt, run the Service.exe discoverable service.</span></span>  
  
3.  <span data-ttu-id="21bdb-115">O DiscoveryProxy.exe deve exibir o seguinte texto: `******* Adding the following service: ** [Service Contract Name] ** [Service Endpoint Addr] 3.******* Done *******` .</span><span class="sxs-lookup"><span data-stu-id="21bdb-115">The DiscoveryProxy.exe should display the following text: `******* Adding the following service: ** [Service Contract Name] ** [Service Endpoint Addr] 3.******* Done *******` .</span></span>  
  
### <a name="run-the-client-application"></a><span data-ttu-id="21bdb-116">Executar o aplicativo cliente</span><span class="sxs-lookup"><span data-stu-id="21bdb-116">Run the Client Application</span></span>  
  
1.  <span data-ttu-id="21bdb-117">Abra um prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="21bdb-117">Open a command prompt.</span></span>  
  
2.  <span data-ttu-id="21bdb-118">No prompt de comando, execute o aplicativo de client.exe.</span><span class="sxs-lookup"><span data-stu-id="21bdb-118">Within the command prompt, run the client.exe application.</span></span>  
  
3.  <span data-ttu-id="21bdb-119">Depois de alguns segundos, o aplicativo cliente exibe o texto a seguir: Conectar-se no [serviço de ponto de extremidade].</span><span class="sxs-lookup"><span data-stu-id="21bdb-119">After a few seconds the client application displays the following text: Connecting to [Service-Endpoint].</span></span>  
  
4.  <span data-ttu-id="21bdb-120">O service.exe deve, em seguida, exibir o texto a seguir: Solicitação recebida a saudação, responderá.</span><span class="sxs-lookup"><span data-stu-id="21bdb-120">The service.exe should then display the following text: Greeting request received, I will respond.</span></span>  
  
5.  <span data-ttu-id="21bdb-121">O client.exe deve, em seguida, exibir o texto a seguir: Cliente de Olá!</span><span class="sxs-lookup"><span data-stu-id="21bdb-121">The client.exe should then display the following text: Hello Client!</span></span>  
  
### <a name="shut-down-the-applications"></a><span data-ttu-id="21bdb-122">Desligue os aplicativos</span><span class="sxs-lookup"><span data-stu-id="21bdb-122">Shut Down the Applications</span></span>  
  
1.  <span data-ttu-id="21bdb-123">Desligar o aplicativo cliente.</span><span class="sxs-lookup"><span data-stu-id="21bdb-123">Shut down the client application.</span></span>  
  
2.  <span data-ttu-id="21bdb-124">Desligamento do serviço.</span><span class="sxs-lookup"><span data-stu-id="21bdb-124">Shut down the service.</span></span> <span data-ttu-id="21bdb-125">O proxy de descoberta exibe o seguinte texto: `******* Removing the following service: ** [Service Contract Name] ** [Service Endpoint Addr] 2.3.******* Done *******`.</span><span class="sxs-lookup"><span data-stu-id="21bdb-125">The discovery proxy displays the following text: `******* Removing the following service: ** [Service Contract Name] ** [Service Endpoint Addr] 2.3.******* Done *******`.</span></span>  
  
3.  <span data-ttu-id="21bdb-126">Desligue o proxy de descoberta.</span><span class="sxs-lookup"><span data-stu-id="21bdb-126">Shut down the discovery proxy.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21bdb-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="21bdb-127">See also</span></span>
- [<span data-ttu-id="21bdb-128">Visão geral de descoberta do WCF</span><span class="sxs-lookup"><span data-stu-id="21bdb-128">WCF Discovery Overview</span></span>](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md)
- [<span data-ttu-id="21bdb-129">Como: Implementar um Proxy de descoberta</span><span class="sxs-lookup"><span data-stu-id="21bdb-129">How to: Implement a Discovery Proxy</span></span>](../../../../docs/framework/wcf/feature-details/how-to-implement-a-discovery-proxy.md)
- [<span data-ttu-id="21bdb-130">Como: Implementar um serviço de descoberta que registra com o Proxy de descoberta</span><span class="sxs-lookup"><span data-stu-id="21bdb-130">How to: Implement a Discoverable Service that Registers with the Discovery Proxy</span></span>](../../../../docs/framework/wcf/feature-details/discoverable-service-that-registers-with-the-discovery-proxy.md)
- [<span data-ttu-id="21bdb-131">Como: Implementar um aplicativo cliente que usa o Proxy de descoberta para localizar um serviço</span><span class="sxs-lookup"><span data-stu-id="21bdb-131">How to: Implement a Client Application that Uses the Discovery Proxy to Find a Service</span></span>](../../../../docs/framework/wcf/feature-details/client-app-discovery-proxy-to-find-a-service.md)
