---
title: Acessando o serviço de um navegador da Web (WCF Data Services Quickstart)
description: Aprenda a iniciar o WCF Data Services no Visual Studio e a desabilitar a leitura do feed em um navegador. Obtenha o documento de definição de serviço e acesse os recursos do serviço de dados.
ms.date: 03/30/2017
ms.assetid: 5a6fa180-3094-4e6e-ba2b-8c80975d18d1
ms.openlocfilehash: 713436c31bc3f622c4f44a83e33fff3fcbba1c1c
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85247772"
---
# <a name="accessing-the-service-from-a-web-browser-wcf-data-services-quickstart"></a><span data-ttu-id="67225-104">Acessando o serviço de um navegador da Web (WCF Data Services Quickstart)</span><span class="sxs-lookup"><span data-stu-id="67225-104">Accessing the Service from a Web Browser (WCF Data Services Quickstart)</span></span>

<span data-ttu-id="67225-105">Esta é a segunda tarefa do guia de início rápido do WCF Data Services.</span><span class="sxs-lookup"><span data-stu-id="67225-105">This is the second task of the WCF Data Services quickstart.</span></span> <span data-ttu-id="67225-106">Nesta tarefa, você inicia o WCF Data Services do Visual Studio e, opcionalmente, desabilita a leitura do feed no navegador da Web.</span><span class="sxs-lookup"><span data-stu-id="67225-106">In this task, you start the WCF Data Services from Visual Studio and optionally disable feed reading in the Web browser.</span></span> <span data-ttu-id="67225-107">Em seguida, você recupera o documento de definição de serviço, bem como os recursos do serviço de dados de acesso enviando solicitações HTTP GET por meio de um navegador da Web para os recursos expostos.</span><span class="sxs-lookup"><span data-stu-id="67225-107">You then retrieve the service definition document as well as access data service resources by submitting HTTP GET requests through a Web browser to the exposed resources.</span></span>

> [!NOTE]
> <span data-ttu-id="67225-108">Por padrão, o Visual Studio atribui automaticamente um número de porta para o `localhost` URI no seu computador.</span><span class="sxs-lookup"><span data-stu-id="67225-108">By default, Visual Studio auto-assigns a port number to the `localhost` URI on your computer.</span></span> <span data-ttu-id="67225-109">Essa tarefa usa o número da porta `12345` nos exemplos do URI.</span><span class="sxs-lookup"><span data-stu-id="67225-109">This task uses the port number `12345` in the URI examples.</span></span> <span data-ttu-id="67225-110">Para obter mais informações sobre como definir um número de porta específico em seu projeto do Visual Studio, consulte [criando o serviço de dados](creating-the-data-service.md).</span><span class="sxs-lookup"><span data-stu-id="67225-110">For more information about how to set a specific port number in your Visual Studio project see [Creating the Data Service](creating-the-data-service.md).</span></span>

## <a name="to-request-the-default-service-document-by-using-internet-explorer"></a><span data-ttu-id="67225-111">Para solicitar o documento padrão de serviço usando o Internet Explorer</span><span class="sxs-lookup"><span data-stu-id="67225-111">To request the default service document by using Internet Explorer</span></span>

1. <span data-ttu-id="67225-112">No Internet Explorer, no menu **ferramentas** , selecione **Opções da Internet**, clique na guia **conteúdo** , clique em **configurações**e desmarque a **exibição do feed**.</span><span class="sxs-lookup"><span data-stu-id="67225-112">In Internet Explorer, from the **Tools** menu, select **Internet Options**, click the **Content** tab, click **Settings**, and clear **Turn on feed viewing**.</span></span>

     <span data-ttu-id="67225-113">Isso garantirá que a leitura de feeds estará desabilitada.</span><span class="sxs-lookup"><span data-stu-id="67225-113">This makes sure that feed reading is disabled.</span></span> <span data-ttu-id="67225-114">Se você não desabilitar essa funcionalidade, o navegador da Web tratará o documento codificado AtomPub retornado como um feed XML em vez de exibir os dados XML brutos.</span><span class="sxs-lookup"><span data-stu-id="67225-114">If you do not disable this functionality, then the Web browser will treat the returned AtomPub encoded document as an XML feed instead of displaying the raw XML data.</span></span>

    > [!NOTE]
    > <span data-ttu-id="67225-115">Se seu navegador não puder exibir o feed como dados XML brutos, você ainda deverá ser capaz de exibir o feed como código-fonte para a página.</span><span class="sxs-lookup"><span data-stu-id="67225-115">If your browser cannot display the feed as raw XML data, you should still be able to view the feed as the source code for the page.</span></span>

2. <span data-ttu-id="67225-116">No Visual Studio, pressione a tecla **F5** para iniciar a depuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="67225-116">In Visual Studio, press the **F5** key to start debugging the application.</span></span>

3. <span data-ttu-id="67225-117">Abra um navegador da Web no computador local.</span><span class="sxs-lookup"><span data-stu-id="67225-117">Open a Web browser on the local computer.</span></span> <span data-ttu-id="67225-118">Na barra de endereços, digite a seguinte URL:</span><span class="sxs-lookup"><span data-stu-id="67225-118">In the address bar, enter the following URI:</span></span>

    ```http
    http://localhost:12345/northwind.svc
    ```

     <span data-ttu-id="67225-119">Isso retorna o documento padrão de serviço, que contém uma lista de conjuntos de entidades que são expostos por esse serviço de dados.</span><span class="sxs-lookup"><span data-stu-id="67225-119">This returns the default service document, which contains a list of entity sets that are exposed by this data service.</span></span>

## <a name="to-access-entity-set-resources-from-a-web-browser"></a><span data-ttu-id="67225-120">Para acessar os recursos do conjunto de entidades de um navegador da Web</span><span class="sxs-lookup"><span data-stu-id="67225-120">To access entity set resources from a Web browser</span></span>

1. <span data-ttu-id="67225-121">Na barra de endereços do seu navegador da Web, digite a seguinte URL:</span><span class="sxs-lookup"><span data-stu-id="67225-121">In the address bar of your Web browser, enter the following URI:</span></span>

    ```http
    http://localhost:12345/northwind.svc/Customers
    ```

     <span data-ttu-id="67225-122">Isso retorna um conjunto de todos os clientes no banco de dados de exemplo Northwind.</span><span class="sxs-lookup"><span data-stu-id="67225-122">This returns a set of all customers in the Northwind sample database.</span></span>

2. <span data-ttu-id="67225-123">Na barra de endereços do seu navegador da Web, digite a seguinte URL:</span><span class="sxs-lookup"><span data-stu-id="67225-123">In the address bar of your Web browser, enter the following URI:</span></span>

    ```http
    http://localhost:12345/northwind.svc/Customers('ALFKI')
    ```

     <span data-ttu-id="67225-124">Isso retorna uma instância de entidade para o cliente específico, `ALFKI`.</span><span class="sxs-lookup"><span data-stu-id="67225-124">This returns an entity instance for the specific customer, `ALFKI`.</span></span>

3. <span data-ttu-id="67225-125">Na barra de endereços do seu navegador da Web, digite a seguinte URL:</span><span class="sxs-lookup"><span data-stu-id="67225-125">In the address bar of your Web browser, enter the following URI:</span></span>

    ```http
    http://localhost:12345/northwind.svc/Customers('ALFKI')/Orders
    ```

     <span data-ttu-id="67225-126">Isso percorre a relação entre clientes e pedidos para retornar um conjunto de todos os pedidos para o cliente específico `ALFKI`.</span><span class="sxs-lookup"><span data-stu-id="67225-126">This traverses the relationship between customers and orders to return a set of all orders for the specific customer `ALFKI`.</span></span>

4. <span data-ttu-id="67225-127">Na barra de endereços do seu navegador da Web, digite a seguinte URL:</span><span class="sxs-lookup"><span data-stu-id="67225-127">In the address bar of your Web browser, enter the following URI:</span></span>

    ```http
    http://localhost:12345/northwind.svc/Customers('ALFKI')/Orders?$filter=OrderID eq 10643
    ```

     <span data-ttu-id="67225-128">Isso filtra os pedidos que pertencem ao cliente específico `ALFKI` de modo que somente uma ordem específica seja retornada com base no valor `OrderID` fornecido.</span><span class="sxs-lookup"><span data-stu-id="67225-128">This filters orders that belong to the specific customer `ALFKI` so that only a specific order is returned based on the supplied `OrderID` value.</span></span>

## <a name="next-steps"></a><span data-ttu-id="67225-129">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="67225-129">Next Steps</span></span>

<span data-ttu-id="67225-130">Você acessou com êxito a WCF Data Services de um navegador da Web, com o navegador emitindo solicitações HTTP GET para os recursos especificados.</span><span class="sxs-lookup"><span data-stu-id="67225-130">You have successfully accessed the WCF Data Services from a Web browser, with the browser issuing HTTP GET requests to specified resources.</span></span> <span data-ttu-id="67225-131">Um navegador da Web fornece uma maneira fácil para experimentar a sintaxe de endereçamento de solicitações e exibir os resultados.</span><span class="sxs-lookup"><span data-stu-id="67225-131">A Web browser provides an easy way to experiment with the addressing syntax of requests and view the results.</span></span> <span data-ttu-id="67225-132">No entanto, um serviço de dados de produção geralmente não é acessado por esse método.</span><span class="sxs-lookup"><span data-stu-id="67225-132">However, a production data service is not generally accessed by this method.</span></span> <span data-ttu-id="67225-133">Normalmente, os aplicativos interagem com o serviço de dados por meio de código de aplicativo ou linguagens de script.</span><span class="sxs-lookup"><span data-stu-id="67225-133">Typically, applications interact with the data service through application code or scripting languages.</span></span> <span data-ttu-id="67225-134">Em seguida, você criará um aplicativo cliente que usa bibliotecas de cliente para acessar os recursos do serviço de dados como se eles fossem Common Language Runtime (CLR):</span><span class="sxs-lookup"><span data-stu-id="67225-134">Next, you will create a client application that uses client libraries to access data service resources as if they were common language runtime (CLR) objects:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="67225-135">Criando o aplicativo cliente do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="67225-135">Creating the .NET Framework Client Application</span></span>](creating-the-dotnet-client-application-wcf-data-services-quickstart.md)

## <a name="see-also"></a><span data-ttu-id="67225-136">Veja também</span><span class="sxs-lookup"><span data-stu-id="67225-136">See also</span></span>

- [<span data-ttu-id="67225-137">Acessando recursos do serviço de dados</span><span class="sxs-lookup"><span data-stu-id="67225-137">Accessing Data Service Resources</span></span>](accessing-data-service-resources-wcf-data-services.md)
