---
title: Integração de cache ASP.NET
ms.date: 03/30/2017
ms.assetid: f581923a-8a72-42fc-bd6a-46de2aaeecc1
ms.openlocfilehash: 56f686b83deb576f1245a9d4b9df2df433ea1e2f
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70045784"
---
# <a name="aspnet-caching-integration"></a><span data-ttu-id="221a6-102">Integração de cache ASP.NET</span><span class="sxs-lookup"><span data-stu-id="221a6-102">ASP.NET Caching Integration</span></span>

<span data-ttu-id="221a6-103">Este exemplo demonstra como utilizar o cache de saída ASP.NET com o modelo de programação WEB HTTP do WCF.</span><span class="sxs-lookup"><span data-stu-id="221a6-103">This sample demonstrates how to utilize the ASP.NET output cache with the WCF WEB HTTP programming model.</span></span> <span data-ttu-id="221a6-104">Este tópico se concentra no recurso de integração do cache de saída do ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="221a6-104">This topic focuses on the ASP.NET output cache integration feature.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="221a6-105">Demonstra</span><span class="sxs-lookup"><span data-stu-id="221a6-105">Demonstrates</span></span>

<span data-ttu-id="221a6-106">Integração com o cache de saída ASP.NET</span><span class="sxs-lookup"><span data-stu-id="221a6-106">Integration with the ASP.NET Output Cache</span></span>

> [!IMPORTANT]
> <span data-ttu-id="221a6-107">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="221a6-107">The samples may already be installed on your machine.</span></span> <span data-ttu-id="221a6-108">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="221a6-108">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="221a6-109">Se esse diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos de Windows Workflow Foundation (WF) para .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) [!INCLUDE[wf1](../../../../includes/wf1-md.md)] e exemplos.</span><span class="sxs-lookup"><span data-stu-id="221a6-109">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="221a6-110">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="221a6-110">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\AspNetCachingIntegration`

## <a name="discussion"></a><span data-ttu-id="221a6-111">Discussão</span><span class="sxs-lookup"><span data-stu-id="221a6-111">Discussion</span></span>

<span data-ttu-id="221a6-112">O exemplo usa o <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> para utilizar o cache de saída do ASP.NET com o serviço do Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="221a6-112">The sample uses the <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> to utilize ASP.NET output caching with the Windows Communication Foundation (WCF) service.</span></span> <span data-ttu-id="221a6-113">O <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> é aplicado às operações de serviço e fornece o nome de um perfil de cache em um arquivo de configuração que deve ser aplicado a respostas da operação especificada.</span><span class="sxs-lookup"><span data-stu-id="221a6-113">The <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> is applied to service operations, and provides the name of a cache profile in a configuration file that should be applied to responses from the given operation.</span></span>

<span data-ttu-id="221a6-114">No arquivo Service.cs do projeto de serviço de exemplo, as `GetCustomer` operações e `GetCustomers` são marcadas com o <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute>, que fornece o nome do perfil de cache "CacheFor60Seconds".</span><span class="sxs-lookup"><span data-stu-id="221a6-114">In the Service.cs file of the sample Service project, both the `GetCustomer` and `GetCustomers` operations are marked with the <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute>, which provides the cache profile name "CacheFor60Seconds".</span></span> <span data-ttu-id="221a6-115">No arquivo Web. config do projeto de serviço, o perfil de cache "CacheFor60Seconds" é fornecido sob o elemento`caching`< > de <`system.web`>.</span><span class="sxs-lookup"><span data-stu-id="221a6-115">In the Web.config file of the Service project, the cache profile "CacheFor60Seconds" is provided under the <`caching`> element of <`system.web`>.</span></span> <span data-ttu-id="221a6-116">Para esse perfil de cache, o valor do `duration` atributo é "60", portanto, as respostas associadas a esse perfil são armazenadas em cache no cache de saída ASP.net por 60 segundos.</span><span class="sxs-lookup"><span data-stu-id="221a6-116">For this cache profile, the value of the `duration` attribute is "60", so responses associated with this profile are cached in the ASP.NET output cache for 60 seconds.</span></span> <span data-ttu-id="221a6-117">Além disso, para esse perfil de cache `varmByParam` , o atributo é definido como "Format" para que as solicitações com `format` valores diferentes para o parâmetro de cadeia de caracteres de consulta tenham suas respostas armazenadas em cache separadamente.</span><span class="sxs-lookup"><span data-stu-id="221a6-117">Also, for this cache profile, the `varmByParam` attribute is set to "format" so requests with different values for the `format` query string parameter have their responses cached separately.</span></span> <span data-ttu-id="221a6-118">Por fim, o atributo do `varyByHeader` perfil de cache é definido como "Accept", portanto, as solicitações com valores de cabeçalho Accept diferentes têm suas respostas armazenadas em cache separadamente.</span><span class="sxs-lookup"><span data-stu-id="221a6-118">Lastly, the cache profile’s `varyByHeader` attribute is set to "Accept", so requests with different Accept header values have their responses cached separately.</span></span>

<span data-ttu-id="221a6-119">Program.cs no projeto do cliente demonstra como um cliente desse tipo pode ser criado usando <xref:System.Net.HttpWebRequest>o.</span><span class="sxs-lookup"><span data-stu-id="221a6-119">Program.cs in the Client project demonstrates how such a client can be authored using <xref:System.Net.HttpWebRequest>.</span></span> <span data-ttu-id="221a6-120">Observe que essa é apenas uma maneira de acessar um serviço WCF.</span><span class="sxs-lookup"><span data-stu-id="221a6-120">Note that this is just one way to access a WCF service.</span></span> <span data-ttu-id="221a6-121">Também é possível acessar o serviço usando outras classes de .NET Framework, como a fábrica de canais do <xref:System.Net.WebClient>WCF e o.</span><span class="sxs-lookup"><span data-stu-id="221a6-121">It is also possible to access the service using other .NET Framework classes like the WCF channel factory and <xref:System.Net.WebClient>.</span></span> <span data-ttu-id="221a6-122">Outros exemplos no SDK (como o exemplo de [serviço http básico](../../../../docs/framework/wcf/samples/basic-http-service.md) ) ilustram como usar essas classes para se comunicar com um serviço WCF.</span><span class="sxs-lookup"><span data-stu-id="221a6-122">Other samples in the SDK (such as the [Basic HTTP Service](../../../../docs/framework/wcf/samples/basic-http-service.md) sample) illustrate how to use these classes to communicate with a WCF service.</span></span>

## <a name="to-run-the-sample"></a><span data-ttu-id="221a6-123">Para executar a amostra</span><span class="sxs-lookup"><span data-stu-id="221a6-123">To run the sample</span></span>

<span data-ttu-id="221a6-124">O exemplo consiste em três projetos:</span><span class="sxs-lookup"><span data-stu-id="221a6-124">The sample consists of three projects:</span></span>

- <span data-ttu-id="221a6-125">**Serviço**: Um projeto de aplicativo Web que inclui um serviço HTTP do WCF hospedado em ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="221a6-125">**Service**: A Web Application project that includes a WCF HTTP service hosted in ASP.NET.</span></span>

- <span data-ttu-id="221a6-126">**Cliente**: Um projeto de aplicativo de console que faz chamadas para o serviço.</span><span class="sxs-lookup"><span data-stu-id="221a6-126">**Client**: A console application project that makes calls to the service.</span></span>

- <span data-ttu-id="221a6-127">**Comum**: Uma biblioteca compartilhada que contém o tipo de cliente usado pelo cliente e serviço.</span><span class="sxs-lookup"><span data-stu-id="221a6-127">**Common**: A shared library that contains the Customer type used by the client and service.</span></span>

<span data-ttu-id="221a6-128">À medida que o aplicativo de console do cliente é executado, o cliente faz solicitações ao serviço e grava as informações pertinentes das respostas na janela do console.</span><span class="sxs-lookup"><span data-stu-id="221a6-128">As the Client console application runs, the client makes requests to the service and writes the pertinent information from the responses to the console window.</span></span>

#### <a name="to-run-the-sample"></a><span data-ttu-id="221a6-129">Para executar a amostra</span><span class="sxs-lookup"><span data-stu-id="221a6-129">To run the sample</span></span>

1. <span data-ttu-id="221a6-130">Abra a solução para o exemplo de integração do cache ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="221a6-130">Open the solution for the ASP.NET Caching Integration Sample.</span></span>

2. <span data-ttu-id="221a6-131">Pressione CTRL+SHIFT+B para criar a solução.</span><span class="sxs-lookup"><span data-stu-id="221a6-131">Press CTRL+SHIFT+B to build the solution.</span></span>

3. <span data-ttu-id="221a6-132">Se a janela de **Gerenciador de soluções** ainda não estiver aberta, pressione CTRL + W + S.</span><span class="sxs-lookup"><span data-stu-id="221a6-132">If the **Solution Explorer** window is not already open, press CTRL+W+S.</span></span>

4. <span data-ttu-id="221a6-133">Na janela **Gerenciador de soluções** , clique com o botão direito do mouse no projeto de **serviço** e selecione **Iniciar nova instância**.</span><span class="sxs-lookup"><span data-stu-id="221a6-133">From the **Solution Explorer** window, right click the **Service** project and select **Start New Instance**.</span></span> <span data-ttu-id="221a6-134">Isso inicia o servidor de desenvolvimento do ASP.NET, que hospeda o serviço.</span><span class="sxs-lookup"><span data-stu-id="221a6-134">This launches the ASP.NET development server, which hosts the service.</span></span>

5. <span data-ttu-id="221a6-135">Na janela **Gerenciador de soluções** , clique com o botão direito do mouse no projeto **cliente** e selecione **Iniciar nova instância**.</span><span class="sxs-lookup"><span data-stu-id="221a6-135">From the **Solution Explorer** window, right click the **Client** project and select **Start New Instance**.</span></span>

6. <span data-ttu-id="221a6-136">A janela do console do cliente é exibida e fornece o URI do serviço em execução e o URI da página de ajuda HTML para o serviço em execução.</span><span class="sxs-lookup"><span data-stu-id="221a6-136">The client console window appears and provides the URI of the running service and the URI of the HTML help page for the running service.</span></span> <span data-ttu-id="221a6-137">Em qualquer momento, você pode exibir a página de ajuda HTML digitando o URI da página de ajuda em um navegador.</span><span class="sxs-lookup"><span data-stu-id="221a6-137">At any point in time you can view the HTML help page by typing the URI of the help page in a browser.</span></span>

7. <span data-ttu-id="221a6-138">À medida que o exemplo é executado, o cliente grava o status da atividade atual.</span><span class="sxs-lookup"><span data-stu-id="221a6-138">As the sample runs, the client writes the status of the current activity.</span></span>

8. <span data-ttu-id="221a6-139">Pressione qualquer tecla para encerrar o aplicativo de console do cliente.</span><span class="sxs-lookup"><span data-stu-id="221a6-139">Press any key to terminate the client console application.</span></span>

9. <span data-ttu-id="221a6-140">Pressione SHIFT + F5 para parar a depuração do serviço.</span><span class="sxs-lookup"><span data-stu-id="221a6-140">Press SHIFT+F5 to stop debugging the service.</span></span>

10. <span data-ttu-id="221a6-141">Na área de notificação do Windows, clique com o botão direito do mouse no ícone do servidor de desenvolvimento ASP.NET e selecione **parar**.</span><span class="sxs-lookup"><span data-stu-id="221a6-141">In the Windows Notification Area, right click the ASP.NET development server icon and select **Stop**.</span></span>
