---
title: Exemplo de integração de SystemWebRouting
ms.date: 03/30/2017
ms.assetid: f1c94802-95c4-49e4-b1e2-ee9dd126ff93
ms.openlocfilehash: 58d720f164c4c35f3de4c282e9aa983d11e4040b
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90555205"
---
# <a name="systemwebrouting-integration-sample"></a><span data-ttu-id="3bf1c-102">Exemplo de integração de SystemWebRouting</span><span class="sxs-lookup"><span data-stu-id="3bf1c-102">SystemWebRouting Integration Sample</span></span>
<span data-ttu-id="3bf1c-103">Este exemplo demonstra a integração da camada de hospedagem com as classes no <xref:System.Web.Routing> namespace.</span><span class="sxs-lookup"><span data-stu-id="3bf1c-103">This sample demonstrates the hosting layer’s integration with the classes in the <xref:System.Web.Routing> namespace.</span></span> <span data-ttu-id="3bf1c-104">As classes no <xref:System.Web.Routing> namespace permitem que um aplicativo use URLs que não correspondem diretamente a um recurso físico.</span><span class="sxs-lookup"><span data-stu-id="3bf1c-104">The classes in the <xref:System.Web.Routing> namespace allow an application to use URLs that do not directly correspond to a physical resource.</span></span> <span data-ttu-id="3bf1c-105">Usar o roteamento da Web permite que o desenvolvedor crie endereços virtuais para HTTP que são então mapeados de volta para os serviços reais do WCF.</span><span class="sxs-lookup"><span data-stu-id="3bf1c-105">Using Web routing allows the developer to create virtual addresses for HTTP that are then mapped back to actual WCF services.</span></span> <span data-ttu-id="3bf1c-106">Isso é útil quando um serviço WCF deve ser hospedado sem a necessidade de um arquivo ou recurso físico, ou quando os serviços devem ser acessados com URLs que não contêm arquivos como. html ou. aspx.</span><span class="sxs-lookup"><span data-stu-id="3bf1c-106">This is useful when a WCF service must be hosted without requiring a physical file or resource, or when services must be accessed with URLs that do not contain files such as .html or .aspx.</span></span> <span data-ttu-id="3bf1c-107">Este exemplo demonstra como utilizar a <xref:System.Web.Routing.RouteTable> classe para criar URIs virtuais que mapeiam para serviços em execução definidos em global. asax.</span><span class="sxs-lookup"><span data-stu-id="3bf1c-107">This sample demonstrates how to utilize the <xref:System.Web.Routing.RouteTable> class to create virtual URIs that map to running services defined in global.asax.</span></span>

> [!NOTE]
> <span data-ttu-id="3bf1c-108">As classes no <xref:System.Web.Routing> namespace só funcionam para serviços hospedados via http.</span><span class="sxs-lookup"><span data-stu-id="3bf1c-108">The classes in the <xref:System.Web.Routing> namespace only work for services hosted over HTTP.</span></span>  
  
<span data-ttu-id="3bf1c-109">Este exemplo usa o WCF para criar dois RSS feeds: um `movies` feed e um `channels` feed.</span><span class="sxs-lookup"><span data-stu-id="3bf1c-109">This example uses WCF to create two RSS feeds: a `movies` feed and a `channels` feed.</span></span> <span data-ttu-id="3bf1c-110">As URLs para ativar os serviços não contêm uma extensão e são registradas no `Application_Start` método da `Global` classe derivada da <xref:System.Web.HttpApplication> classe.</span><span class="sxs-lookup"><span data-stu-id="3bf1c-110">The URLs to activate the services do not contain an extension and are registered in the `Application_Start` method of the `Global` class derived from the <xref:System.Web.HttpApplication> class.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3bf1c-111">Este exemplo só funciona no Serviços de Informações da Internet (IIS) 7,0 e posterior, pois o IIS 6,0 usa um método diferente para dar suporte a URLs sem extensão.</span><span class="sxs-lookup"><span data-stu-id="3bf1c-111">This sample only works in Internet Information Services (IIS) 7.0 and later, as IIS 6.0 uses a different method for supporting extension-less URLs.</span></span>  

#### <a name="to-download-this-sample"></a><span data-ttu-id="3bf1c-112">Para baixar este exemplo</span><span class="sxs-lookup"><span data-stu-id="3bf1c-112">To download this sample</span></span>
  
<span data-ttu-id="3bf1c-113">Este exemplo pode já estar instalado em seu computador.</span><span class="sxs-lookup"><span data-stu-id="3bf1c-113">This sample may already be installed on your computer.</span></span> <span data-ttu-id="3bf1c-114">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="3bf1c-114">Check for the following (default) directory before continuing.</span></span>  

`<InstallDrive>:\WF_WCF_Samples`  

 <span data-ttu-id="3bf1c-115">Se esse diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos de Windows Workflow Foundation (WF) para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="3bf1c-115">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="3bf1c-116">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="3bf1c-116">This sample is located in the following directory.</span></span>  

`<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WebRoutingIntegration`  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="3bf1c-117">Para usar este exemplo</span><span class="sxs-lookup"><span data-stu-id="3bf1c-117">To use this sample</span></span>  
  
1. <span data-ttu-id="3bf1c-118">Usando o Visual Studio, abra o arquivo WebRoutingIntegration. sln.</span><span class="sxs-lookup"><span data-stu-id="3bf1c-118">Using Visual Studio, open the WebRoutingIntegration.sln file.</span></span>  
  
2. <span data-ttu-id="3bf1c-119">Para executar a solução e iniciar o servidor de desenvolvimento da Web, pressione F5.</span><span class="sxs-lookup"><span data-stu-id="3bf1c-119">To run the solution and start the Web development server, press F5.</span></span>  
  
     <span data-ttu-id="3bf1c-120">Uma listagem de diretório para o exemplo é exibida.</span><span class="sxs-lookup"><span data-stu-id="3bf1c-120">A directory listing for the sample appears.</span></span> <span data-ttu-id="3bf1c-121">Observe que não há arquivos com uma extensão de arquivo. svc.</span><span class="sxs-lookup"><span data-stu-id="3bf1c-121">Note that there are no files with an .svc file extension.</span></span>  
  
3. <span data-ttu-id="3bf1c-122">Na barra de endereços, adicione `movies` à URL, para que ela leia `http://localhost:[port]/movies` e pressione Enter.</span><span class="sxs-lookup"><span data-stu-id="3bf1c-122">In the address bar, add `movies` to the URL, so that it reads `http://localhost:[port]/movies` and press ENTER.</span></span>  
  
     <span data-ttu-id="3bf1c-123">O feed de filmes aparece no navegador.</span><span class="sxs-lookup"><span data-stu-id="3bf1c-123">The movies feed appears in the browser.</span></span>  
  
4. <span data-ttu-id="3bf1c-124">Na barra de endereços, adicione `channels` à URL, para que seja leituras `http://localhost:[port]/channels` e pressione Enter.</span><span class="sxs-lookup"><span data-stu-id="3bf1c-124">In the address bar, add `channels` to the URL, so that is reads `http://localhost:[port]/channels` and press ENTER.</span></span>  
  
     <span data-ttu-id="3bf1c-125">O feed canais é exibido no navegador.</span><span class="sxs-lookup"><span data-stu-id="3bf1c-125">The channels feed appears in the browser.</span></span>  
  
5. <span data-ttu-id="3bf1c-126">Feche o navegador da Web, pressionando ALT + F4.</span><span class="sxs-lookup"><span data-stu-id="3bf1c-126">Close the Web browser, by pressing ALT+F4.</span></span>  
  
     <span data-ttu-id="3bf1c-127">Se o servidor de desenvolvimento não tiver sido encerrado, clique com o botão direito do mouse no ícone da área de notificação e selecione **parar**.</span><span class="sxs-lookup"><span data-stu-id="3bf1c-127">If the development server has not exited, right-click the notification area icon and select **Stop**.</span></span>  
  
#### <a name="to-use-this-sample-when-hosted-in-iis"></a><span data-ttu-id="3bf1c-128">Para usar este exemplo quando hospedado no IIS</span><span class="sxs-lookup"><span data-stu-id="3bf1c-128">To use this sample when hosted in IIS</span></span>  
  
1. <span data-ttu-id="3bf1c-129">Usando o Visual Studio, abra o arquivo WebRoutingIntegration. sln.</span><span class="sxs-lookup"><span data-stu-id="3bf1c-129">Using Visual Studio, open the WebRoutingIntegration.sln file.</span></span>  
  
2. <span data-ttu-id="3bf1c-130">Crie o projeto pressionando CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="3bf1c-130">Build the project, by pressing CTRL+SHIFT+B.</span></span>  
  
3. <span data-ttu-id="3bf1c-131">Crie um aplicativo Web no Gerenciador do Serviços de Informações da Internet (IIS).</span><span class="sxs-lookup"><span data-stu-id="3bf1c-131">Create a Web application in Internet Information Services (IIS) Manager.</span></span>  
  
    1. <span data-ttu-id="3bf1c-132">No Gerenciador do IIS, clique com o botão direito do mouse no **site padrão** e selecione **Adicionar um aplicativo**.</span><span class="sxs-lookup"><span data-stu-id="3bf1c-132">In IIS Manager, right click the **Default Web Site** and select **Add an Application**.</span></span>  
  
    2. <span data-ttu-id="3bf1c-133">Para o **alias**, digite `WebRoutingIntegration` .</span><span class="sxs-lookup"><span data-stu-id="3bf1c-133">For the **alias**, type in `WebRoutingIntegration`.</span></span>  
  
    3. <span data-ttu-id="3bf1c-134">Para o **caminho físico**, selecione a pasta de serviço dentro do projeto.</span><span class="sxs-lookup"><span data-stu-id="3bf1c-134">For the **Physical Path**, select the Service folder inside the project.</span></span>  
  
    4. <span data-ttu-id="3bf1c-135">Pressione **OK**.</span><span class="sxs-lookup"><span data-stu-id="3bf1c-135">Press **OK**.</span></span>  
  
4. <span data-ttu-id="3bf1c-136">Inicie o aplicativo clicando com o botão direito do mouse no aplicativo Web e selecionando **gerenciar aplicativo** e, em seguida, **procurar**.</span><span class="sxs-lookup"><span data-stu-id="3bf1c-136">Start the application, by right-clicking the Web application and selecting **Manage Application** and then **Browse**.</span></span>  
  
5. <span data-ttu-id="3bf1c-137">Na barra de endereços, adicione `movies` à URL, para que seja leituras `http://localhost:[port]/movies` e pressione Enter.</span><span class="sxs-lookup"><span data-stu-id="3bf1c-137">In the address bar, add `movies` to the URL, so that is reads `http://localhost:[port]/movies` and press ENTER.</span></span>  
  
     <span data-ttu-id="3bf1c-138">O feed de filmes aparece no navegador.</span><span class="sxs-lookup"><span data-stu-id="3bf1c-138">The movies feed appears in the browser.</span></span>  
  
6. <span data-ttu-id="3bf1c-139">Na barra de endereços, adicione `channels` à URL, para que seja leituras `http://localhost:[port]/channels` e pressione Enter.</span><span class="sxs-lookup"><span data-stu-id="3bf1c-139">In the address bar, add `channels` to the URL, so that is reads `http://localhost:[port]/channels` and press ENTER.</span></span>  
  
     <span data-ttu-id="3bf1c-140">O feed canais é exibido no navegador.</span><span class="sxs-lookup"><span data-stu-id="3bf1c-140">The channels feed appears in the browser.</span></span>  
  
7. <span data-ttu-id="3bf1c-141">Feche o navegador da Web, pressionando ALT + F4.</span><span class="sxs-lookup"><span data-stu-id="3bf1c-141">Close the Web browser, by pressing ALT+F4.</span></span>  
  
 <span data-ttu-id="3bf1c-142">Este exemplo demonstra que a camada de hospedagem é capaz de compor com as classes no <xref:System.Web.Routing> namespace para rotear as solicitações de serviços hospedados via http.</span><span class="sxs-lookup"><span data-stu-id="3bf1c-142">This sample demonstrates that the hosting layer is capable of composing with the classes in the <xref:System.Web.Routing> namespace for routing the requests of services hosted over HTTP.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3bf1c-143">Você deve atualizar a versão padrão do pool de aplicativos para .NET Framework 4 se ela estiver definida para a versão 2.</span><span class="sxs-lookup"><span data-stu-id="3bf1c-143">You must update the default application pool version to .NET Framework 4 if it’s set to version 2.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3bf1c-144">Confira também</span><span class="sxs-lookup"><span data-stu-id="3bf1c-144">See also</span></span>

- <span data-ttu-id="3bf1c-145">[Hospedagem de AppFabric e persistência Exemplos](/previous-versions/appfabric/ff383418(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="3bf1c-145">[AppFabric Hosting and Persistence Samples](/previous-versions/appfabric/ff383418(v=azure.10))</span></span>
