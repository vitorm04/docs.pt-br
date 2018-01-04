---
title: "Exemplo de integração de SystemWebRouting"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f1c94802-95c4-49e4-b1e2-ee9dd126ff93
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1718ea9c6ea1e029b66955e88fd54e20db1a3527
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="systemwebrouting-integration-sample"></a><span data-ttu-id="df821-102">Exemplo de integração de SystemWebRouting</span><span class="sxs-lookup"><span data-stu-id="df821-102">SystemWebRouting Integration Sample</span></span>
<span data-ttu-id="df821-103">Este exemplo demonstra a integração da camada de hospedagem com as classes de <xref:System.Web.Routing> namespace.</span><span class="sxs-lookup"><span data-stu-id="df821-103">This sample demonstrates the hosting layer’s integration with the classes in the <xref:System.Web.Routing> namespace.</span></span> <span data-ttu-id="df821-104">As classes de <xref:System.Web.Routing> namespace permitem que um aplicativo usar URLs não correspondem diretamente a um recurso físico.</span><span class="sxs-lookup"><span data-stu-id="df821-104">The classes in the <xref:System.Web.Routing> namespace allow an application to use URLs that do not directly correspond to a physical resource.</span></span> <span data-ttu-id="df821-105">Usando o roteamento da Web permite ao desenvolvedor criar endereços virtuais para HTTP, em seguida, são mapeados para real [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviços.</span><span class="sxs-lookup"><span data-stu-id="df821-105">Using Web routing allows the developer to create virtual addresses for HTTP that are then mapped back to actual [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] services.</span></span> <span data-ttu-id="df821-106">Isso é útil quando um serviço WCF deve ser hospedado sem a necessidade de um arquivo físico ou recurso, ou quando os serviços devem ser acessados com URLs que não contêm arquivos, como HTML ou. aspx.</span><span class="sxs-lookup"><span data-stu-id="df821-106">This is useful when a WCF service must be hosted without requiring a physical file or resource, or when services must be accessed with URLs that do not contain files such as .html or .aspx.</span></span> <span data-ttu-id="df821-107">Este exemplo demonstra como utilizar o <xref:System.Web.Routing.RouteTable> classe para criar URIs virtuais que são mapeados para executar serviços definidos em global. asax.</span><span class="sxs-lookup"><span data-stu-id="df821-107">This sample demonstrates how to utilize the <xref:System.Web.Routing.RouteTable> class to create virtual URIs that map to running services defined in global.asax.</span></span> <span data-ttu-id="df821-108">Neste exemplo, há dois feeds RSS criados usando o WCF: um `movies` feed e um `channels` feed.</span><span class="sxs-lookup"><span data-stu-id="df821-108">For this example, there are two RSS feeds created using WCF: a `movies` feed and a `channels` feed.</span></span> <span data-ttu-id="df821-109">As URLs para ativar os serviços não contêm uma extensão e são registradas no `Application_Start` método o `Global` classe derivada do <xref:System.Web.HttpApplication.Application_Start> classe.</span><span class="sxs-lookup"><span data-stu-id="df821-109">The URLs to activate the services do not contain an extension and are registered in the `Application_Start` method of the `Global` class derived from the <xref:System.Web.HttpApplication.Application_Start> class.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="df821-110">As classes de <xref:System.Web.Routing> namespace só funciona para serviços hospedados por HTTP.</span><span class="sxs-lookup"><span data-stu-id="df821-110">The classes in the <xref:System.Web.Routing> namespace only work for services hosted over HTTP.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="df821-111">Este exemplo só funciona [!INCLUDE[iisver](../../../../includes/iisver-md.md)], como [!INCLUDE[iis60](../../../../includes/iis60-md.md)] usa um método diferente para dar suporte a URLs sem extensão.</span><span class="sxs-lookup"><span data-stu-id="df821-111">This sample only works in [!INCLUDE[iisver](../../../../includes/iisver-md.md)], as [!INCLUDE[iis60](../../../../includes/iis60-md.md)] uses a different method for supporting extension-less URLs.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="df821-112">Os exemplos podem mais ser instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="df821-112">The samples may already be installed on your computer.</span></span> <span data-ttu-id="df821-113">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="df821-113">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="df821-114">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="df821-114">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="df821-115">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="df821-115">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WebRoutingIntegration`  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="df821-116">Para usar este exemplo</span><span class="sxs-lookup"><span data-stu-id="df821-116">To use this sample</span></span>  
  
1.  <span data-ttu-id="df821-117">Usando [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], abra o arquivo WebRoutingIntegration.sln.</span><span class="sxs-lookup"><span data-stu-id="df821-117">Using [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], open the WebRoutingIntegration.sln file.</span></span>  
  
2.  <span data-ttu-id="df821-118">Para executar a solução e iniciar o servidor de desenvolvimento da Web, pressione F5.</span><span class="sxs-lookup"><span data-stu-id="df821-118">To run the solution and start the Web development server, press F5.</span></span>  
  
     <span data-ttu-id="df821-119">Uma listagem para o exemplo de diretório é exibida.</span><span class="sxs-lookup"><span data-stu-id="df821-119">A directory listing for the sample appears.</span></span> <span data-ttu-id="df821-120">Observe que não há nenhum arquivo com uma extensão de arquivo. svc.</span><span class="sxs-lookup"><span data-stu-id="df821-120">Note that there are no files with an .svc file extension.</span></span>  
  
3.  <span data-ttu-id="df821-121">Na barra de endereços, adicionar `movies` à URL, isso é leituras http://localhost: [porta] filmes e pressione ENTER.</span><span class="sxs-lookup"><span data-stu-id="df821-121">In the address bar, add `movies` to the URL, so that is reads http://localhost:[port]/movies and press ENTER.</span></span>  
  
     <span data-ttu-id="df821-122">O feed de filmes aparece no navegador.</span><span class="sxs-lookup"><span data-stu-id="df821-122">The movies feed appears in the browser.</span></span>  
  
4.  <span data-ttu-id="df821-123">Na barra de endereços, adicionar `channels` à URL, isso é leituras http://localhost: [porta] / canais e pressione ENTER.</span><span class="sxs-lookup"><span data-stu-id="df821-123">In the address bar, add `channels` to the URL, so that is reads http://localhost:[port]/channels and press ENTER.</span></span>  
  
     <span data-ttu-id="df821-124">O feed de canais é exibida no navegador.</span><span class="sxs-lookup"><span data-stu-id="df821-124">The channels feed appears in the browser.</span></span>  
  
5.  <span data-ttu-id="df821-125">Feche o navegador da Web, pressionando ALT + F4.</span><span class="sxs-lookup"><span data-stu-id="df821-125">Close the Web browser, by pressing ALT+F4.</span></span>  
  
     <span data-ttu-id="df821-126">Se o servidor de desenvolvimento não saiu, clique no ícone da área de notificação e selecione **parar**.</span><span class="sxs-lookup"><span data-stu-id="df821-126">If the development server has not exited, right-click the notification area icon and select **Stop**.</span></span>  
  
#### <a name="to-use-this-sample-when-hosted-in-iis"></a><span data-ttu-id="df821-127">Para usar esse exemplo, quando hospedados no IIS</span><span class="sxs-lookup"><span data-stu-id="df821-127">To use this sample when hosted in IIS</span></span>  
  
1.  <span data-ttu-id="df821-128">Usando [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], abra o arquivo WebRoutingIntegration.sln.</span><span class="sxs-lookup"><span data-stu-id="df821-128">Using [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], open the WebRoutingIntegration.sln file.</span></span>  
  
2.  <span data-ttu-id="df821-129">Compile o projeto, pressionando CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="df821-129">Build the project, by pressing CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="df821-130">Crie um aplicativo Web no Gerenciador de serviços de informações da Internet (IIS).</span><span class="sxs-lookup"><span data-stu-id="df821-130">Create a Web application in Internet Information Services (IIS) Manager.</span></span>  
  
    1.  <span data-ttu-id="df821-131">Clique com botão direito no Gerenciador do IIS, o **Default Web Site** e selecione **adicionar um aplicativo**.</span><span class="sxs-lookup"><span data-stu-id="df821-131">In IIS Manager, right click the **Default Web Site** and select **Add an Application**.</span></span>  
  
    2.  <span data-ttu-id="df821-132">Para o **alias**, digite `WebRoutingIntegration`.</span><span class="sxs-lookup"><span data-stu-id="df821-132">For the **alias**, type in `WebRoutingIntegration`.</span></span>  
  
    3.  <span data-ttu-id="df821-133">Para o **caminho físico**, selecione a pasta do serviço dentro do projeto.</span><span class="sxs-lookup"><span data-stu-id="df821-133">For the **Physical Path**, select the Service folder inside the project.</span></span>  
  
    4.  <span data-ttu-id="df821-134">Press **OK**.</span><span class="sxs-lookup"><span data-stu-id="df821-134">Press **OK**.</span></span>  
  
4.  <span data-ttu-id="df821-135">Iniciar o aplicativo, clicando duas vezes o aplicativo Web e selecionando **gerenciar aplicativo** e **procurar**.</span><span class="sxs-lookup"><span data-stu-id="df821-135">Start the application, by right-clicking the Web application and selecting **Manage Application** and then **Browse**.</span></span>  
  
5.  <span data-ttu-id="df821-136">Na barra de endereços, adicionar `movies` à URL, isso é leituras http://localhost: [porta] filmes e pressione ENTER.</span><span class="sxs-lookup"><span data-stu-id="df821-136">In the address bar, add `movies` to the URL, so that is reads http://localhost:[port]/movies and press ENTER.</span></span>  
  
     <span data-ttu-id="df821-137">O feed de filmes aparece no navegador.</span><span class="sxs-lookup"><span data-stu-id="df821-137">The movies feed appears in the browser.</span></span>  
  
6.  <span data-ttu-id="df821-138">Na barra de endereços, adicionar `channels` à URL, isso é leituras http://localhost: [porta] / canais e pressione ENTER.</span><span class="sxs-lookup"><span data-stu-id="df821-138">In the address bar, add `channels` to the URL, so that is reads http://localhost:[port]/channels and press ENTER.</span></span>  
  
     <span data-ttu-id="df821-139">O feed de canais é exibida no navegador.</span><span class="sxs-lookup"><span data-stu-id="df821-139">The channels feed appears in the browser.</span></span>  
  
7.  <span data-ttu-id="df821-140">Feche o navegador da Web, pressionando ALT + F4.</span><span class="sxs-lookup"><span data-stu-id="df821-140">Close the Web browser, by pressing ALT+F4.</span></span>  
  
 <span data-ttu-id="df821-141">Este exemplo demonstra que a camada de hospedagem é capaz de composição com as classes de <xref:System.Web.Routing> namespace para direcionar solicitações de serviços hospedados por HTTP.</span><span class="sxs-lookup"><span data-stu-id="df821-141">This sample demonstrates that the hosting layer is capable of composing with the classes in the <xref:System.Web.Routing> namespace for routing the requests of services hosted over HTTP.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="df821-142">Atualize a versão de pool de aplicativos padrão para [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] se ele estiver definido para a versão 2.</span><span class="sxs-lookup"><span data-stu-id="df821-142">Please update the default application pool version to [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] if it’s set to version 2.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df821-143">Consulte também</span><span class="sxs-lookup"><span data-stu-id="df821-143">See Also</span></span>  
 [<span data-ttu-id="df821-144">Exemplos de persistência e hospedagem de AppFabric</span><span class="sxs-lookup"><span data-stu-id="df821-144">AppFabric Hosting and Persistence Samples</span></span>](http://go.microsoft.com/fwlink/?LinkId=193961)
