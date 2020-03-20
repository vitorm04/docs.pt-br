---
title: Exemplo de integração de SystemWebRouting
ms.date: 03/30/2017
ms.assetid: f1c94802-95c4-49e4-b1e2-ee9dd126ff93
ms.openlocfilehash: 2f12d80085e3ac27dac8ce80b6bb09f69337bfd8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79143948"
---
# <a name="systemwebrouting-integration-sample"></a><span data-ttu-id="93c7c-102">Exemplo de integração de SystemWebRouting</span><span class="sxs-lookup"><span data-stu-id="93c7c-102">SystemWebRouting Integration Sample</span></span>
<span data-ttu-id="93c7c-103">Esta amostra demonstra a integração da camada <xref:System.Web.Routing> de hospedagem com as classes no namespace.</span><span class="sxs-lookup"><span data-stu-id="93c7c-103">This sample demonstrates the hosting layer’s integration with the classes in the <xref:System.Web.Routing> namespace.</span></span> <span data-ttu-id="93c7c-104">As classes <xref:System.Web.Routing> no namespace permitem que um aplicativo use URLs que não correspondam diretamente a um recurso físico.</span><span class="sxs-lookup"><span data-stu-id="93c7c-104">The classes in the <xref:System.Web.Routing> namespace allow an application to use URLs that do not directly correspond to a physical resource.</span></span> <span data-ttu-id="93c7c-105">O uso do roteamento da Web permite que o desenvolvedor crie endereços virtuais para HTTP que são então mapeados de volta aos serviços WCF reais.</span><span class="sxs-lookup"><span data-stu-id="93c7c-105">Using Web routing allows the developer to create virtual addresses for HTTP that are then mapped back to actual WCF services.</span></span> <span data-ttu-id="93c7c-106">Isso é útil quando um serviço WCF deve ser hospedado sem exigir um arquivo físico ou recurso, ou quando os serviços devem ser acessados com URLs que não contêm arquivos como .html ou .aspx.</span><span class="sxs-lookup"><span data-stu-id="93c7c-106">This is useful when a WCF service must be hosted without requiring a physical file or resource, or when services must be accessed with URLs that do not contain files such as .html or .aspx.</span></span> <span data-ttu-id="93c7c-107">Esta amostra demonstra como <xref:System.Web.Routing.RouteTable> utilizar a classe para criar URIs virtuais que mapeiam para executar serviços definidos em global.asax.</span><span class="sxs-lookup"><span data-stu-id="93c7c-107">This sample demonstrates how to utilize the <xref:System.Web.Routing.RouteTable> class to create virtual URIs that map to running services defined in global.asax.</span></span>

> [!NOTE]
> <span data-ttu-id="93c7c-108">As classes <xref:System.Web.Routing> no namespace só funcionam para serviços hospedados em HTTP.</span><span class="sxs-lookup"><span data-stu-id="93c7c-108">The classes in the <xref:System.Web.Routing> namespace only work for services hosted over HTTP.</span></span>  
  
<span data-ttu-id="93c7c-109">Este exemplo usa WCF para criar dois `movies` feeds `channels` RSS: um feed e um feed.</span><span class="sxs-lookup"><span data-stu-id="93c7c-109">This example uses WCF to create two RSS feeds: a `movies` feed and a `channels` feed.</span></span> <span data-ttu-id="93c7c-110">Os URLs para ativar os serviços não contêm `Application_Start` uma `Global` extensão e <xref:System.Web.HttpApplication> estão registrados no método da classe derivada da classe.</span><span class="sxs-lookup"><span data-stu-id="93c7c-110">The URLs to activate the services do not contain an extension and are registered in the `Application_Start` method of the `Global` class derived from the <xref:System.Web.HttpApplication> class.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="93c7c-111">Essa amostra só funciona em Serviços de Informação da Internet (IIS) 7.0 e posteriormente, pois o IIS 6.0 usa um método diferente para suportar URLs sem extensão.</span><span class="sxs-lookup"><span data-stu-id="93c7c-111">This sample only works in Internet Information Services (IIS) 7.0 and later, as IIS 6.0 uses a different method for supporting extension-less URLs.</span></span>  

#### <a name="to-download-this-sample"></a><span data-ttu-id="93c7c-112">Para baixar esta amostra</span><span class="sxs-lookup"><span data-stu-id="93c7c-112">To download this sample</span></span>
  
<span data-ttu-id="93c7c-113">Esta amostra já pode estar instalada no seu computador.</span><span class="sxs-lookup"><span data-stu-id="93c7c-113">This sample may already be installed on your computer.</span></span> <span data-ttu-id="93c7c-114">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="93c7c-114">Check for the following (default) directory before continuing.</span></span>  

`<InstallDrive>:\WF_WCF_Samples`  

 <span data-ttu-id="93c7c-115">Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation).</span><span class="sxs-lookup"><span data-stu-id="93c7c-115">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="93c7c-116">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="93c7c-116">This sample is located in the following directory.</span></span>  

`<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WebRoutingIntegration`  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="93c7c-117">Para usar este exemplo</span><span class="sxs-lookup"><span data-stu-id="93c7c-117">To use this sample</span></span>  
  
1. <span data-ttu-id="93c7c-118">Usando o Visual Studio, abra o arquivo WebRoutingIntegration.sln.</span><span class="sxs-lookup"><span data-stu-id="93c7c-118">Using Visual Studio, open the WebRoutingIntegration.sln file.</span></span>  
  
2. <span data-ttu-id="93c7c-119">Para executar a solução e iniciar o servidor de desenvolvimento web, pressione F5.</span><span class="sxs-lookup"><span data-stu-id="93c7c-119">To run the solution and start the Web development server, press F5.</span></span>  
  
     <span data-ttu-id="93c7c-120">Uma lista de diretórios para a amostra é exibida.</span><span class="sxs-lookup"><span data-stu-id="93c7c-120">A directory listing for the sample appears.</span></span> <span data-ttu-id="93c7c-121">Observe que não há arquivos com uma extensão de arquivo .svc.</span><span class="sxs-lookup"><span data-stu-id="93c7c-121">Note that there are no files with an .svc file extension.</span></span>  
  
3. <span data-ttu-id="93c7c-122">Na barra de `movies` endereços, `http://localhost:[port]/movies` adicione à URL, para que ela leia e pressione ENTER.</span><span class="sxs-lookup"><span data-stu-id="93c7c-122">In the address bar, add `movies` to the URL, so that it reads `http://localhost:[port]/movies` and press ENTER.</span></span>  
  
     <span data-ttu-id="93c7c-123">O feed de filmes aparece no navegador.</span><span class="sxs-lookup"><span data-stu-id="93c7c-123">The movies feed appears in the browser.</span></span>  
  
4. <span data-ttu-id="93c7c-124">Na barra de `channels` endereços, adicione à URL, `http://localhost:[port]/channels` de modo que seja leitura e pressione ENTER.</span><span class="sxs-lookup"><span data-stu-id="93c7c-124">In the address bar, add `channels` to the URL, so that is reads `http://localhost:[port]/channels` and press ENTER.</span></span>  
  
     <span data-ttu-id="93c7c-125">O feed de canais aparece no navegador.</span><span class="sxs-lookup"><span data-stu-id="93c7c-125">The channels feed appears in the browser.</span></span>  
  
5. <span data-ttu-id="93c7c-126">Feche o navegador da Web pressionando ALT+F4.</span><span class="sxs-lookup"><span data-stu-id="93c7c-126">Close the Web browser, by pressing ALT+F4.</span></span>  
  
     <span data-ttu-id="93c7c-127">Se o servidor de desenvolvimento não tiver saído, clique com o botão direito do mouse no ícone da área de notificação e selecione **Parar**.</span><span class="sxs-lookup"><span data-stu-id="93c7c-127">If the development server has not exited, right-click the notification area icon and select **Stop**.</span></span>  
  
#### <a name="to-use-this-sample-when-hosted-in-iis"></a><span data-ttu-id="93c7c-128">Para usar esta amostra quando hospedado no IIS</span><span class="sxs-lookup"><span data-stu-id="93c7c-128">To use this sample when hosted in IIS</span></span>  
  
1. <span data-ttu-id="93c7c-129">Usando o Visual Studio, abra o arquivo WebRoutingIntegration.sln.</span><span class="sxs-lookup"><span data-stu-id="93c7c-129">Using Visual Studio, open the WebRoutingIntegration.sln file.</span></span>  
  
2. <span data-ttu-id="93c7c-130">Construa o projeto, pressionando CTRL+SHIFT+B.</span><span class="sxs-lookup"><span data-stu-id="93c7c-130">Build the project, by pressing CTRL+SHIFT+B.</span></span>  
  
3. <span data-ttu-id="93c7c-131">Crie um aplicativo web no Gerenciador de Serviços de Informação da Internet (IIS).</span><span class="sxs-lookup"><span data-stu-id="93c7c-131">Create a Web application in Internet Information Services (IIS) Manager.</span></span>  
  
    1. <span data-ttu-id="93c7c-132">No IIS Manager, clique com o botão direito do mouse no **Site padrão da Web** e **selecione Adicionar um aplicativo**.</span><span class="sxs-lookup"><span data-stu-id="93c7c-132">In IIS Manager, right click the **Default Web Site** and select **Add an Application**.</span></span>  
  
    2. <span data-ttu-id="93c7c-133">Para o **alias,** digite `WebRoutingIntegration`.</span><span class="sxs-lookup"><span data-stu-id="93c7c-133">For the **alias**, type in `WebRoutingIntegration`.</span></span>  
  
    3. <span data-ttu-id="93c7c-134">Para o **Caminho Físico,** selecione a pasta Serviço dentro do projeto.</span><span class="sxs-lookup"><span data-stu-id="93c7c-134">For the **Physical Path**, select the Service folder inside the project.</span></span>  
  
    4. <span data-ttu-id="93c7c-135">Pressione **OK**.</span><span class="sxs-lookup"><span data-stu-id="93c7c-135">Press **OK**.</span></span>  
  
4. <span data-ttu-id="93c7c-136">Inicie o aplicativo, clicando com o botão direito do mouse no aplicativo web e selecionando **Gerenciar o aplicativo** e, em seguida, **procurar**.</span><span class="sxs-lookup"><span data-stu-id="93c7c-136">Start the application, by right-clicking the Web application and selecting **Manage Application** and then **Browse**.</span></span>  
  
5. <span data-ttu-id="93c7c-137">Na barra de `movies` endereços, adicione à URL, `http://localhost:[port]/movies` de modo que seja leitura e pressione ENTER.</span><span class="sxs-lookup"><span data-stu-id="93c7c-137">In the address bar, add `movies` to the URL, so that is reads `http://localhost:[port]/movies` and press ENTER.</span></span>  
  
     <span data-ttu-id="93c7c-138">O feed de filmes aparece no navegador.</span><span class="sxs-lookup"><span data-stu-id="93c7c-138">The movies feed appears in the browser.</span></span>  
  
6. <span data-ttu-id="93c7c-139">Na barra de `channels` endereços, adicione à URL, `http://localhost:[port]/channels` de modo que seja leitura e pressione ENTER.</span><span class="sxs-lookup"><span data-stu-id="93c7c-139">In the address bar, add `channels` to the URL, so that is reads `http://localhost:[port]/channels` and press ENTER.</span></span>  
  
     <span data-ttu-id="93c7c-140">O feed de canais aparece no navegador.</span><span class="sxs-lookup"><span data-stu-id="93c7c-140">The channels feed appears in the browser.</span></span>  
  
7. <span data-ttu-id="93c7c-141">Feche o navegador da Web pressionando ALT+F4.</span><span class="sxs-lookup"><span data-stu-id="93c7c-141">Close the Web browser, by pressing ALT+F4.</span></span>  
  
 <span data-ttu-id="93c7c-142">Esta amostra demonstra que a camada de hospedagem <xref:System.Web.Routing> é capaz de compor com as classes no namespace para roteamento das solicitações de serviços hospedados em HTTP.</span><span class="sxs-lookup"><span data-stu-id="93c7c-142">This sample demonstrates that the hosting layer is capable of composing with the classes in the <xref:System.Web.Routing> namespace for routing the requests of services hosted over HTTP.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="93c7c-143">Você deve atualizar a versão padrão do pool de aplicativos para .NET Framework 4 se estiver definida como versão 2.</span><span class="sxs-lookup"><span data-stu-id="93c7c-143">You must update the default application pool version to .NET Framework 4 if it’s set to version 2.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93c7c-144">Confira também</span><span class="sxs-lookup"><span data-stu-id="93c7c-144">See also</span></span>

- <span data-ttu-id="93c7c-145">[Hospedagem de AppFabric e persistência Exemplos](https://docs.microsoft.com/previous-versions/appfabric/ff383418(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="93c7c-145">[AppFabric Hosting and Persistence Samples](https://docs.microsoft.com/previous-versions/appfabric/ff383418(v=azure.10))</span></span>
