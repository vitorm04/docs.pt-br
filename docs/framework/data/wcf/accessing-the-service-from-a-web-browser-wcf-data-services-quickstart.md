---
title: Acessando o serviço de um navegador da Web (WCF Data Services Quickstart)
ms.date: 03/30/2017
ms.assetid: 5a6fa180-3094-4e6e-ba2b-8c80975d18d1
ms.openlocfilehash: eb7f1c97722b45a93c310fb8bcbdb42beece2553
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70780537"
---
# <a name="accessing-the-service-from-a-web-browser-wcf-data-services-quickstart"></a><span data-ttu-id="f23e9-102">Acessando o serviço de um navegador da Web (WCF Data Services Quickstart)</span><span class="sxs-lookup"><span data-stu-id="f23e9-102">Accessing the Service from a Web Browser (WCF Data Services Quickstart)</span></span>

<span data-ttu-id="f23e9-103">Esta é a segunda tarefa do guia de início rápido do WCF Data Services.</span><span class="sxs-lookup"><span data-stu-id="f23e9-103">This is the second task of the WCF Data Services quickstart.</span></span> <span data-ttu-id="f23e9-104">Nesta tarefa, você inicia o WCF Data Services do Visual Studio e, opcionalmente, desabilita a leitura do feed no navegador da Web.</span><span class="sxs-lookup"><span data-stu-id="f23e9-104">In this task, you start the WCF Data Services from Visual Studio and optionally disable feed reading in the Web browser.</span></span> <span data-ttu-id="f23e9-105">Em seguida, você recupera o documento de definição de serviço, bem como os recursos do serviço de dados de acesso enviando solicitações HTTP GET por meio de um navegador da Web para os recursos expostos.</span><span class="sxs-lookup"><span data-stu-id="f23e9-105">You then retrieve the service definition document as well as access data service resources by submitting HTTP GET requests through a Web browser to the exposed resources.</span></span>

> [!NOTE]
> <span data-ttu-id="f23e9-106">Por padrão, o Visual Studio atribui automaticamente um número de porta para o `localhost` URI no seu computador.</span><span class="sxs-lookup"><span data-stu-id="f23e9-106">By default, Visual Studio auto-assigns a port number to the `localhost` URI on your computer.</span></span> <span data-ttu-id="f23e9-107">Essa tarefa usa o número da porta `12345` nos exemplos do URI.</span><span class="sxs-lookup"><span data-stu-id="f23e9-107">This task uses the port number `12345` in the URI examples.</span></span> <span data-ttu-id="f23e9-108">Para obter mais informações sobre como definir um número de porta específico em seu projeto do Visual Studio, consulte [criando o serviço de dados](creating-the-data-service.md).</span><span class="sxs-lookup"><span data-stu-id="f23e9-108">For more information about how to set a specific port number in your Visual Studio project see [Creating the Data Service](creating-the-data-service.md).</span></span>

## <a name="to-request-the-default-service-document-by-using-internet-explorer"></a><span data-ttu-id="f23e9-109">Para solicitar o documento padrão de serviço usando o Internet Explorer</span><span class="sxs-lookup"><span data-stu-id="f23e9-109">To request the default service document by using Internet Explorer</span></span>

1. <span data-ttu-id="f23e9-110">No Internet Explorer, no menu **ferramentas** , selecione **Opções da Internet**, clique na guia **conteúdo** , clique em **configurações**e desmarque a **exibição do feed**.</span><span class="sxs-lookup"><span data-stu-id="f23e9-110">In Internet Explorer, from the **Tools** menu, select **Internet Options**, click the **Content** tab, click **Settings**, and clear **Turn on feed viewing**.</span></span>

     <span data-ttu-id="f23e9-111">Isso garantirá que a leitura de feeds estará desabilitada.</span><span class="sxs-lookup"><span data-stu-id="f23e9-111">This makes sure that feed reading is disabled.</span></span> <span data-ttu-id="f23e9-112">Se você não desabilitar essa funcionalidade, o navegador da Web tratará o documento codificado AtomPub retornado como um feed XML em vez de exibir os dados XML brutos.</span><span class="sxs-lookup"><span data-stu-id="f23e9-112">If you do not disable this functionality, then the Web browser will treat the returned AtomPub encoded document as an XML feed instead of displaying the raw XML data.</span></span>

    > [!NOTE]
    > <span data-ttu-id="f23e9-113">Se seu navegador não puder exibir o feed como dados XML brutos, você ainda deverá ser capaz de exibir o feed como código-fonte para a página.</span><span class="sxs-lookup"><span data-stu-id="f23e9-113">If your browser cannot display the feed as raw XML data, you should still be able to view the feed as the source code for the page.</span></span>

2. <span data-ttu-id="f23e9-114">No Visual Studio, pressione a tecla **F5** para iniciar a depuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f23e9-114">In Visual Studio, press the **F5** key to start debugging the application.</span></span>

3. <span data-ttu-id="f23e9-115">Abra um navegador da Web no computador local.</span><span class="sxs-lookup"><span data-stu-id="f23e9-115">Open a Web browser on the local computer.</span></span> <span data-ttu-id="f23e9-116">Na barra de endereços, digite a seguinte URL:</span><span class="sxs-lookup"><span data-stu-id="f23e9-116">In the address bar, enter the following URI:</span></span>

    ```
    http://localhost:12345/northwind.svc
    ```

     <span data-ttu-id="f23e9-117">Isso retorna o documento padrão de serviço, que contém uma lista de conjuntos de entidades que são expostos por esse serviço de dados.</span><span class="sxs-lookup"><span data-stu-id="f23e9-117">This returns the default service document, which contains a list of entity sets that are exposed by this data service.</span></span>

## <a name="to-access-entity-set-resources-from-a-web-browser"></a><span data-ttu-id="f23e9-118">Para acessar os recursos do conjunto de entidades de um navegador da Web</span><span class="sxs-lookup"><span data-stu-id="f23e9-118">To access entity set resources from a Web browser</span></span>

1. <span data-ttu-id="f23e9-119">Na barra de endereços do seu navegador da Web, digite a seguinte URL:</span><span class="sxs-lookup"><span data-stu-id="f23e9-119">In the address bar of your Web browser, enter the following URI:</span></span>

    ```
    http://localhost:12345/northwind.svc/Customers
    ```

     <span data-ttu-id="f23e9-120">Isso retorna um conjunto de todos os clientes no banco de dados de exemplo Northwind.</span><span class="sxs-lookup"><span data-stu-id="f23e9-120">This returns a set of all customers in the Northwind sample database.</span></span>

2. <span data-ttu-id="f23e9-121">Na barra de endereços do seu navegador da Web, digite a seguinte URL:</span><span class="sxs-lookup"><span data-stu-id="f23e9-121">In the address bar of your Web browser, enter the following URI:</span></span>

    ```
    http://localhost:12345/northwind.svc/Customers('ALFKI')
    ```

     <span data-ttu-id="f23e9-122">Isso retorna uma instância de entidade para o cliente específico, `ALFKI`.</span><span class="sxs-lookup"><span data-stu-id="f23e9-122">This returns an entity instance for the specific customer, `ALFKI`.</span></span>

3. <span data-ttu-id="f23e9-123">Na barra de endereços do seu navegador da Web, digite a seguinte URL:</span><span class="sxs-lookup"><span data-stu-id="f23e9-123">In the address bar of your Web browser, enter the following URI:</span></span>

    ```
    http://localhost:12345/northwind.svc/Customers('ALFKI')/Orders
    ```

     <span data-ttu-id="f23e9-124">Isso percorre a relação entre clientes e pedidos para retornar um conjunto de todos os pedidos para o cliente específico `ALFKI`.</span><span class="sxs-lookup"><span data-stu-id="f23e9-124">This traverses the relationship between customers and orders to return a set of all orders for the specific customer `ALFKI`.</span></span>

4. <span data-ttu-id="f23e9-125">Na barra de endereços do seu navegador da Web, digite a seguinte URL:</span><span class="sxs-lookup"><span data-stu-id="f23e9-125">In the address bar of your Web browser, enter the following URI:</span></span>

    ```
    http://localhost:12345/northwind.svc/Customers('ALFKI')/Orders?$filter=OrderID eq 10643
    ```

     <span data-ttu-id="f23e9-126">Isso filtra os pedidos que pertencem ao cliente específico `ALFKI` de modo que somente uma ordem específica seja retornada com base no valor `OrderID` fornecido.</span><span class="sxs-lookup"><span data-stu-id="f23e9-126">This filters orders that belong to the specific customer `ALFKI` so that only a specific order is returned based on the supplied `OrderID` value.</span></span>

## <a name="next-steps"></a><span data-ttu-id="f23e9-127">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="f23e9-127">Next Steps</span></span>

<span data-ttu-id="f23e9-128">Você acessou com êxito a WCF Data Services de um navegador da Web, com o navegador emitindo solicitações HTTP GET para os recursos especificados.</span><span class="sxs-lookup"><span data-stu-id="f23e9-128">You have successfully accessed the WCF Data Services from a Web browser, with the browser issuing HTTP GET requests to specified resources.</span></span> <span data-ttu-id="f23e9-129">Um navegador da Web fornece uma maneira fácil para experimentar a sintaxe de endereçamento de solicitações e exibir os resultados.</span><span class="sxs-lookup"><span data-stu-id="f23e9-129">A Web browser provides an easy way to experiment with the addressing syntax of requests and view the results.</span></span> <span data-ttu-id="f23e9-130">No entanto, um serviço de dados de produção geralmente não é acessado por esse método.</span><span class="sxs-lookup"><span data-stu-id="f23e9-130">However, a production data service is not generally accessed by this method.</span></span> <span data-ttu-id="f23e9-131">Normalmente, os aplicativos interagem com o serviço de dados por meio de código de aplicativo ou linguagens de script.</span><span class="sxs-lookup"><span data-stu-id="f23e9-131">Typically, applications interact with the data service through application code or scripting languages.</span></span> <span data-ttu-id="f23e9-132">Em seguida, você criará um aplicativo cliente que usa bibliotecas de cliente para acessar os recursos do serviço de dados como se eles fossem Common Language Runtime (CLR):</span><span class="sxs-lookup"><span data-stu-id="f23e9-132">Next, you will create a client application that uses client libraries to access data service resources as if they were common language runtime (CLR) objects:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="f23e9-133">Criando o aplicativo cliente do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="f23e9-133">Creating the .NET Framework Client Application</span></span>](creating-the-dotnet-client-application-wcf-data-services-quickstart.md)

## <a name="see-also"></a><span data-ttu-id="f23e9-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f23e9-134">See also</span></span>

- [<span data-ttu-id="f23e9-135">Acessando recursos do serviço de dados</span><span class="sxs-lookup"><span data-stu-id="f23e9-135">Accessing Data Service Resources</span></span>](accessing-data-service-resources-wcf-data-services.md)
