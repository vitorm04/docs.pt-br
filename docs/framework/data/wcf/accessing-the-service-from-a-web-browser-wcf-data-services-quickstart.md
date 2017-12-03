---
title: "Acessando o serviço de um navegador da Web (WCF Data Services Quickstart)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5a6fa180-3094-4e6e-ba2b-8c80975d18d1
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 49deb2e209127f92a333195e9fcd0d1e1bece7d8
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="accessing-the-service-from-a-web-browser-wcf-data-services-quickstart"></a><span data-ttu-id="5d171-102">Acessando o serviço de um navegador da Web (WCF Data Services Quickstart)</span><span class="sxs-lookup"><span data-stu-id="5d171-102">Accessing the Service from a Web Browser (WCF Data Services Quickstart)</span></span>
<span data-ttu-id="5d171-103">Nesta tarefa, você irá iniciar o [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] do [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] e opcionalmente desabilitará a leitura de feeds no navegador da Web.</span><span class="sxs-lookup"><span data-stu-id="5d171-103">In this task, you will start the [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] from [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] and optionally disable feed reading in the Web browser.</span></span> <span data-ttu-id="5d171-104">Você será, em seguida, recuperar o documento de definição de serviço, bem como acessar os recursos de serviço de dados ao enviar solicitações HTTP GET por meio de um navegador da Web para os recursos expostos.</span><span class="sxs-lookup"><span data-stu-id="5d171-104">You will then retrieve the service definition document as well as access data service resources by submitting HTTP GET requests through a Web browser to the exposed resources.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5d171-105">Por padrão, o [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] atribui automaticamente um número de porta para o URI do `localhost` no seu computador.</span><span class="sxs-lookup"><span data-stu-id="5d171-105">By default, [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] auto-assigns a port number to the `localhost` URI on your computer.</span></span> <span data-ttu-id="5d171-106">Essa tarefa usa o número da porta `12345` nos exemplos do URI.</span><span class="sxs-lookup"><span data-stu-id="5d171-106">This task uses the port number `12345` in the URI examples.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="5d171-107">como definir um número de porta específico no seu [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] projeto consulte [criando o serviço de dados](../../../../docs/framework/data/wcf/creating-the-data-service.md).</span><span class="sxs-lookup"><span data-stu-id="5d171-107"> how to set a specific port number in your [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] project see [Creating the Data Service](../../../../docs/framework/data/wcf/creating-the-data-service.md).</span></span>  
  
### <a name="to-request-the-default-service-document-by-using-internet-explorer"></a><span data-ttu-id="5d171-108">Para solicitar o documento padrão de serviço usando o Internet Explorer</span><span class="sxs-lookup"><span data-stu-id="5d171-108">To request the default service document by using Internet Explorer</span></span>  
  
1.  <span data-ttu-id="5d171-109">No Internet Explorer, do **ferramentas** menu, selecione **opções da Internet**, clique no **conteúdo** , clique em **configurações**e desmarque  **Ativar visualização de feed**.</span><span class="sxs-lookup"><span data-stu-id="5d171-109">In Internet Explorer, from the **Tools** menu, select **Internet Options**, click the **Content** tab, click **Settings**, and clear **Turn on feed viewing**.</span></span>  
  
     <span data-ttu-id="5d171-110">Isso garantirá que a leitura de feeds estará desabilitada.</span><span class="sxs-lookup"><span data-stu-id="5d171-110">This makes sure that feed reading is disabled.</span></span> <span data-ttu-id="5d171-111">Se você não desabilitar essa funcionalidade, o navegador da Web tratará o documento codificado AtomPub retornado como um feed XML em vez de exibir os dados XML brutos.</span><span class="sxs-lookup"><span data-stu-id="5d171-111">If you do not disable this functionality, then the Web browser will treat the returned AtomPub encoded document as an XML feed instead of displaying the raw XML data.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="5d171-112">Se seu navegador não puder exibir o feed como dados XML brutos, você ainda deverá ser capaz de exibir o feed como código-fonte para a página.</span><span class="sxs-lookup"><span data-stu-id="5d171-112">If your browser cannot display the feed as raw XML data, you should still be able to view the feed as the source code for the page.</span></span>  
  
2.  <span data-ttu-id="5d171-113">No [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)], pressione a tecla F5 para iniciar a depuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="5d171-113">In [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)], press the F5 key to start debugging the application.</span></span>  
  
3.  <span data-ttu-id="5d171-114">Abra um navegador da Web no computador local.</span><span class="sxs-lookup"><span data-stu-id="5d171-114">Open a Web browser on the local computer.</span></span> <span data-ttu-id="5d171-115">Na barra de endereços, digite a seguinte URL:</span><span class="sxs-lookup"><span data-stu-id="5d171-115">In the address bar, enter the following URI:</span></span>  
  
    ```  
    http://localhost:12345/northwind.svc  
    ```  
  
     <span data-ttu-id="5d171-116">Isso retorna o documento padrão de serviço, que contém uma lista de conjuntos de entidades que são expostos por esse serviço de dados.</span><span class="sxs-lookup"><span data-stu-id="5d171-116">This returns the default service document, which contains a list of entity sets that are exposed by this data service.</span></span>  
  
### <a name="to-access-entity-set-resources-from-a-web-browser"></a><span data-ttu-id="5d171-117">Para acessar os recursos do conjunto de entidades de um navegador da Web</span><span class="sxs-lookup"><span data-stu-id="5d171-117">To access entity set resources from a Web browser</span></span>  
  
1.  <span data-ttu-id="5d171-118">Na barra de endereços do seu navegador da Web, digite a seguinte URL:</span><span class="sxs-lookup"><span data-stu-id="5d171-118">In the address bar of your Web browser, enter the following URI:</span></span>  
  
    ```  
    http://localhost:12345/northwind.svc/Customers  
    ```  
  
     <span data-ttu-id="5d171-119">Isso retorna um conjunto de todos os clientes no banco de dados de exemplo Northwind.</span><span class="sxs-lookup"><span data-stu-id="5d171-119">This returns a set of all customers in the Northwind sample database.</span></span>  
  
2.  <span data-ttu-id="5d171-120">Na barra de endereços do seu navegador da Web, digite a seguinte URL:</span><span class="sxs-lookup"><span data-stu-id="5d171-120">In the address bar of your Web browser, enter the following URI:</span></span>  
  
    ```  
    http://localhost:12345/northwind.svc/Customers('ALFKI')  
    ```  
  
     <span data-ttu-id="5d171-121">Isso retorna uma instância de entidade para o cliente específico, `ALFKI`.</span><span class="sxs-lookup"><span data-stu-id="5d171-121">This returns an entity instance for the specific customer, `ALFKI`.</span></span>  
  
3.  <span data-ttu-id="5d171-122">Na barra de endereços do seu navegador da Web, digite a seguinte URL:</span><span class="sxs-lookup"><span data-stu-id="5d171-122">In the address bar of your Web browser, enter the following URI:</span></span>  
  
    ```  
    http://localhost:12345/northwind.svc/Customers('ALFKI')/Orders  
    ```  
  
     <span data-ttu-id="5d171-123">Isso percorre a relação entre clientes e pedidos para retornar um conjunto de todos os pedidos para o cliente específico `ALFKI`.</span><span class="sxs-lookup"><span data-stu-id="5d171-123">This traverses the relationship between customers and orders to return a set of all orders for the specific customer `ALFKI`.</span></span>  
  
4.  <span data-ttu-id="5d171-124">Na barra de endereços do seu navegador da Web, digite a seguinte URL:</span><span class="sxs-lookup"><span data-stu-id="5d171-124">In the address bar of your Web browser, enter the following URI:</span></span>  
  
    ```  
    http://localhost:12345/northwind.svc/Customers('ALFKI')/Orders?$filter=OrderID eq 10643  
    ```  
  
     <span data-ttu-id="5d171-125">Isso filtra os pedidos que pertencem ao cliente específico `ALFKI` de modo que somente uma ordem específica seja retornada com base no valor `OrderID` fornecido.</span><span class="sxs-lookup"><span data-stu-id="5d171-125">This filters orders that belong to the specific customer `ALFKI` so that only a specific order is returned based on the supplied `OrderID` value.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="5d171-126">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="5d171-126">Next Steps</span></span>  
 <span data-ttu-id="5d171-127">Você acessou com êxito o [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] de um navegador da Web, com o navegador emitindo solicitações HTTP GET para recursos especificados.</span><span class="sxs-lookup"><span data-stu-id="5d171-127">You have successfully accessed the [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] from a Web browser, with the browser issuing HTTP GET requests to specified resources.</span></span> <span data-ttu-id="5d171-128">Um navegador da Web fornece uma maneira fácil para experimentar a sintaxe de endereçamento de solicitações e exibir os resultados.</span><span class="sxs-lookup"><span data-stu-id="5d171-128">A Web browser provides an easy way to experiment with the addressing syntax of requests and view the results.</span></span> <span data-ttu-id="5d171-129">No entanto, um serviço de dados de produção geralmente não é acessado por esse método.</span><span class="sxs-lookup"><span data-stu-id="5d171-129">However, a production data service is not generally accessed by this method.</span></span> <span data-ttu-id="5d171-130">Normalmente, os aplicativos interagem com o serviço de dados por meio do aplicativo código ou linguagens de script.</span><span class="sxs-lookup"><span data-stu-id="5d171-130">Typically, applications interact with the data service through application code or scripting languages.</span></span> <span data-ttu-id="5d171-131">Em seguida, você criará um aplicativo cliente que usa as bibliotecas de cliente para acessar os recursos do serviço de dados como se fossem objetos common language runtime (CLR):</span><span class="sxs-lookup"><span data-stu-id="5d171-131">Next, you will create a client application that uses client libraries to access data service resources as if they were common language runtime (CLR) objects:</span></span>  
  
 [<span data-ttu-id="5d171-132">Criando o aplicativo cliente do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="5d171-132">Creating the .NET Framework Client Application</span></span>](../../../../docs/framework/data/wcf/creating-the-dotnet-client-application-wcf-data-services-quickstart.md)  
  
## <a name="see-also"></a><span data-ttu-id="5d171-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5d171-133">See Also</span></span>  
 [<span data-ttu-id="5d171-134">Acessando recursos do serviço de dados</span><span class="sxs-lookup"><span data-stu-id="5d171-134">Accessing Data Service Resources</span></span>](../../../../docs/framework/data/wcf/accessing-data-service-resources-wcf-data-services.md)
