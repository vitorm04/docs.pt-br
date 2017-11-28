---
title: Pontos de extremidade SOAP e HTTP
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e3c8be75-9dda-4afa-89b6-a82cb3b73cf8
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 9404d304302360b2be590c814d1f94cb46bd5f84
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="soap-and-http-endpoints"></a><span data-ttu-id="b0e87-102">Pontos de extremidade SOAP e HTTP</span><span class="sxs-lookup"><span data-stu-id="b0e87-102">SOAP and HTTP Endpoints</span></span>
<span data-ttu-id="b0e87-103">Este exemplo demonstra como implementar um serviço baseado no RPC e expô-lo no formato SOAP e o "Plain Old XML" (POX) Formatar usando o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] modelo de programação da Web.</span><span class="sxs-lookup"><span data-stu-id="b0e87-103">This sample demonstrates how to implement an RPC-based service and expose it in the SOAP format and the "Plain Old XML" (POX) format using the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Web Programming model.</span></span> <span data-ttu-id="b0e87-104">Consulte o [serviço básico de HTTP](../../../../docs/framework/wcf/samples/basic-http-service.md) exemplo para obter mais detalhes sobre a associação HTTP para o serviço.</span><span class="sxs-lookup"><span data-stu-id="b0e87-104">See the [Basic HTTP Service](../../../../docs/framework/wcf/samples/basic-http-service.md) sample for more details about the HTTP binding for the service.</span></span> <span data-ttu-id="b0e87-105">Este exemplo enfoca os detalhes que pertencem ao expor o mesmo serviço via SOAP e HTTP usando ligações diferentes.</span><span class="sxs-lookup"><span data-stu-id="b0e87-105">This sample focuses on the details that pertain to exposing the same service over SOAP and HTTP using different bindings.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="b0e87-106">Demonstra</span><span class="sxs-lookup"><span data-stu-id="b0e87-106">Demonstrates</span></span>  
 <span data-ttu-id="b0e87-107">Expor um serviço RPC sobre HTTP e SOAP usando [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b0e87-107">Exposing an RPC service over SOAP and HTTP using [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="b0e87-108">Discussão</span><span class="sxs-lookup"><span data-stu-id="b0e87-108">Discussion</span></span>  
 <span data-ttu-id="b0e87-109">Este exemplo consiste em dois componentes: um projeto de aplicativo Web (serviço) que contém um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviço e um aplicativo de console (cliente) que invoca as operações de serviço usando associações HTTP e SOAP.</span><span class="sxs-lookup"><span data-stu-id="b0e87-109">This sample consists of two components: a Web Application project (Service) that contains a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service and a console application (Client) that invokes service operations using SOAP and HTTP bindings.</span></span>  
  
 <span data-ttu-id="b0e87-110">O [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviço expõe 2 operações –`GetData` e `PutData` – que a cadeia de caracteres que foi passada como entrada de eco.</span><span class="sxs-lookup"><span data-stu-id="b0e87-110">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service exposes 2 operations –`GetData` and `PutData` – that echo the string that was passed as input.</span></span> <span data-ttu-id="b0e87-111">As operações de serviço são anotadas com <xref:System.ServiceModel.Web.WebGetAttribute> e <xref:System.ServiceModel.Web.WebInvokeAttribute>.</span><span class="sxs-lookup"><span data-stu-id="b0e87-111">The service operations are annotated with <xref:System.ServiceModel.Web.WebGetAttribute> and <xref:System.ServiceModel.Web.WebInvokeAttribute>.</span></span> <span data-ttu-id="b0e87-112">Esses atributos controlam a projeção de HTTP dessas operações.</span><span class="sxs-lookup"><span data-stu-id="b0e87-112">These attributes control the HTTP projection of these operations.</span></span> <span data-ttu-id="b0e87-113">Além disso, eles são anotados com <xref:System.ServiceModel.OperationContractAttribute>, que permite que eles sejam expostos por associações de SOAP.</span><span class="sxs-lookup"><span data-stu-id="b0e87-113">In addition, they are annotated with <xref:System.ServiceModel.OperationContractAttribute>, which enables them to be exposed over SOAP bindings.</span></span> <span data-ttu-id="b0e87-114">O serviço `PutData` método lança um <xref:System.ServiceModel.Web.WebFaultException>, que é enviado de volta via HTTP usando o código de status HTTP e é enviado pela SOAP como uma falha de SOAP.</span><span class="sxs-lookup"><span data-stu-id="b0e87-114">The service’s `PutData` method throws a <xref:System.ServiceModel.Web.WebFaultException>, which gets sent back over HTTP using the HTTP status code and gets sent back over SOAP as a SOAP fault.</span></span>  
  
 <span data-ttu-id="b0e87-115">O arquivo Web. config configura o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviço com 3 pontos de extremidade:</span><span class="sxs-lookup"><span data-stu-id="b0e87-115">The Web.config file configures the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service with 3 endpoints:</span></span>  
  
-   <span data-ttu-id="b0e87-116">O ponto de extremidade de ~/service.svc/mex que expõe os metadados de serviço para acesso por clientes baseados em SOAP.</span><span class="sxs-lookup"><span data-stu-id="b0e87-116">The ~/service.svc/mex endpoint that exposes the service metadata for access by SOAP-based clients.</span></span>  
  
-   <span data-ttu-id="b0e87-117">O ponto de extremidade de ~/service.svc/http que permite que os clientes acessem o serviço usando a associação HTTP.</span><span class="sxs-lookup"><span data-stu-id="b0e87-117">The ~/service.svc/http endpoint that enables clients to access the service using the HTTP binding.</span></span>  
  
-   <span data-ttu-id="b0e87-118">O ponto de extremidade de ~/service.svc/soap que permite que os clientes acessar o serviço usando o SOAP por associação HTTP.</span><span class="sxs-lookup"><span data-stu-id="b0e87-118">The ~/service.svc/soap endpoint that allows the clients to access the service using the SOAP over HTTP binding.</span></span>  
  
 <span data-ttu-id="b0e87-119">O ponto de extremidade HTTP é configurado com um <`webHttp`> ponto de extremidade padrão que tem `helpEnabled` definido como `true`.</span><span class="sxs-lookup"><span data-stu-id="b0e87-119">The HTTP endpoint is configured with a <`webHttp`> standard endpoint which has `helpEnabled` set to `true`.</span></span> <span data-ttu-id="b0e87-120">Como resultado, o serviço expõe uma página de ajuda XHTML com base em ~/service.svc/http/help que os clientes baseados em HTTP podem usar para acessar o serviço.</span><span class="sxs-lookup"><span data-stu-id="b0e87-120">As a result, the service exposes an XHTML based help page at ~/service.svc/http/help that HTTP-based clients can use to access the service.</span></span>  
  
 <span data-ttu-id="b0e87-121">O projeto cliente demonstra acessando o serviço usando um proxy SOAP (gerados por meio de **adicionar referência de serviço**) e acessar o serviço usando <xref:System.Net.WebClient>.</span><span class="sxs-lookup"><span data-stu-id="b0e87-121">The client project demonstrates accessing the service using a SOAP proxy (generated through **Add Service Reference**) and accessing the service using <xref:System.Net.WebClient>.</span></span>  
  
 <span data-ttu-id="b0e87-122">O exemplo consiste em um serviço hospedado da Web e um aplicativo de console.</span><span class="sxs-lookup"><span data-stu-id="b0e87-122">The sample consists of a Web-hosted service and a console application.</span></span> <span data-ttu-id="b0e87-123">Como o aplicativo de console é executado, o cliente faz solicitações para o serviço e grava as informações pertinentes entre as respostas para a janela do console.</span><span class="sxs-lookup"><span data-stu-id="b0e87-123">As the console application runs, the client makes requests to the service and writes the pertinent information from the responses to the console window.</span></span>  
  
#### <a name="to-run-the-sample"></a><span data-ttu-id="b0e87-124">Para executar a amostra</span><span class="sxs-lookup"><span data-stu-id="b0e87-124">To run the sample</span></span>  
  
1.  <span data-ttu-id="b0e87-125">Abra a solução para o exemplo de pontos de extremidade de HTTP e SOAP.</span><span class="sxs-lookup"><span data-stu-id="b0e87-125">Open the solution for the SOAP and HTTP Endpoints Sample.</span></span>  
  
2.  <span data-ttu-id="b0e87-126">Pressione CTRL+SHIFT+B para criar a solução.</span><span class="sxs-lookup"><span data-stu-id="b0e87-126">Press CTRL+SHIFT+B to build the solution.</span></span>  
  
3.  <span data-ttu-id="b0e87-127">Se ainda não estiver aberta, pressione CTRL + W, S para abrir o **Solution Explorer** janela.</span><span class="sxs-lookup"><span data-stu-id="b0e87-127">If it is not already open, press CTRL+W, S to open the **Solution Explorer** window.</span></span>  
  
4.  <span data-ttu-id="b0e87-128">Do **Gerenciador de soluções** janela, com o botão direito do **serviço** do projeto e coloque o cursor sobre o **depurar** opção de menu de contexto para que o **iniciar nova Instância** menu de contexto é exibido.</span><span class="sxs-lookup"><span data-stu-id="b0e87-128">From the **Solution Explorer** window, right-click the **Service** project and place the cursor over the **Debug** context menu option so that the **Start New Instance** context menu appears.</span></span> <span data-ttu-id="b0e87-129">Clique em **iniciar nova instância**.</span><span class="sxs-lookup"><span data-stu-id="b0e87-129">Click **Start New Instance**.</span></span> <span data-ttu-id="b0e87-130">Isso inicia o ASP.NET development server, que hospeda o serviço.</span><span class="sxs-lookup"><span data-stu-id="b0e87-130">This launches the ASP.NET development server, which hosts the service.</span></span>  
  
5.  <span data-ttu-id="b0e87-131">Na janela Gerenciador de soluções, clique com botão direito no projeto cliente e coloque o cursor sobre o **depurar** opção de menu de contexto para que o **iniciar uma nova instância** menu de contexto é exibido.</span><span class="sxs-lookup"><span data-stu-id="b0e87-131">From the Solution Explorer windows, right-click the Client project and place the cursor over the **Debug** context menu option so that the **Start New Instance** context menu appears.</span></span> <span data-ttu-id="b0e87-132">Clique em **iniciar nova instância**.</span><span class="sxs-lookup"><span data-stu-id="b0e87-132">Click **Start New Instance**.</span></span>  
  
6.  <span data-ttu-id="b0e87-133">A janela de console do cliente é exibida e fornece o URI do serviço em execução e o URI do HTML ajuda a página para o serviço em execução.</span><span class="sxs-lookup"><span data-stu-id="b0e87-133">The client console window appears and provides the URI of the running service and the URI of the HTML help page for the running service.</span></span> <span data-ttu-id="b0e87-134">A qualquer momento, você pode exibir a página de ajuda HTML digitando o URI da página de Ajuda em um navegador.</span><span class="sxs-lookup"><span data-stu-id="b0e87-134">At any point in time you can view the HTML help page by typing the URI of the help page in a browser.</span></span>  
  
7.  <span data-ttu-id="b0e87-135">Como o exemplo é executado, o cliente grava o status da atividade atual.</span><span class="sxs-lookup"><span data-stu-id="b0e87-135">As the sample runs, the client writes the status of the current activity.</span></span>  
  
8.  <span data-ttu-id="b0e87-136">Pressione qualquer tecla para fechar o aplicativo de console de cliente.</span><span class="sxs-lookup"><span data-stu-id="b0e87-136">Press any key to terminate the client console application.</span></span>  
  
9. <span data-ttu-id="b0e87-137">Pressione SHIFT + F5 para parar a depuração de serviço.</span><span class="sxs-lookup"><span data-stu-id="b0e87-137">Press SHIFT+F5 to stop debugging the service.</span></span>  
  
10. <span data-ttu-id="b0e87-138">Na área de notificação do Windows, clique no ícone do servidor de desenvolvimento ASP.NET e selecione **parar** no menu de contexto.</span><span class="sxs-lookup"><span data-stu-id="b0e87-138">In the Windows Notification Area, right-click the ASP.NET development server icon and select **Stop** from the context menu.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="b0e87-139">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="b0e87-139">The samples may already be installed on your machine.</span></span> <span data-ttu-id="b0e87-140">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="b0e87-140">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="b0e87-141">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="b0e87-141">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="b0e87-142">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="b0e87-142">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\SoapAndHttpEndpoints`
