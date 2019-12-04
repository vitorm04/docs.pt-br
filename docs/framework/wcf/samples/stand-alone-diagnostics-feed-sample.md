---
title: Exemplo de feed de diagnóstico independente
ms.date: 03/30/2017
ms.assetid: d31c6c1f-292c-4d95-8e23-ed8565970ea5
ms.openlocfilehash: 40e7e2b704204278e6a8754134a952b8235ee528
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74716672"
---
# <a name="stand-alone-diagnostics-feed-sample"></a><span data-ttu-id="790ef-102">Exemplo de feed de diagnóstico independente</span><span class="sxs-lookup"><span data-stu-id="790ef-102">Stand-Alone Diagnostics Feed Sample</span></span>
<span data-ttu-id="790ef-103">Este exemplo demonstra como criar um feed RSS/Atom para a distribuição com o Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="790ef-103">This sample demonstrates how to create an RSS/Atom feed for syndication with Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="790ef-104">É um programa "Olá, Mundo" básico que mostra as noções básicas do modelo de objeto e como configurá-lo em um serviço de Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="790ef-104">It is a basic "Hello World" program that shows the basics of the object model and how to set it up on a Windows Communication Foundation (WCF) service.</span></span>  
  
 <span data-ttu-id="790ef-105">Os modelos do WCF são feeds de agregação como operações de serviço que retornam um tipo de dados especial, <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter>.</span><span class="sxs-lookup"><span data-stu-id="790ef-105">WCF models syndication feeds as service operations that return a special data type, <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter>.</span></span> <span data-ttu-id="790ef-106">As instâncias do <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> podem serializar um feed nos formatos RSS 2,0 e Atom 1,0.</span><span class="sxs-lookup"><span data-stu-id="790ef-106">Instances of <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> can serialize a feed into both the RSS 2.0 and Atom 1.0 formats.</span></span> <span data-ttu-id="790ef-107">O código de exemplo a seguir mostra o contrato usado.</span><span class="sxs-lookup"><span data-stu-id="790ef-107">The following sample code shows the contract used.</span></span>  
  
```csharp  
[ServiceContract(Namespace = "")]  
    interface IDiagnosticsService  
    {  
        [OperationContract]  
        //The [WebGet] attribute controls how WCF dispatches  
        //HTTP requests to service operations based on a URI suffix  
        //(the part of the request URI after the endpoint address)  
        //using the HTTP GET method. The UriTemplate specifies a relative  
        //path of 'feed', and specifies that the format is  
        //supplied using a query string.   
        [WebGet(UriTemplate="feed?format={format}")]  
        [ServiceKnownType(typeof(Atom10FeedFormatter))]  
        [ServiceKnownType(typeof(Rss20FeedFormatter))]  
        SyndicationFeedFormatter GetProcesses(string format);  
    }  
```  
  
 <span data-ttu-id="790ef-108">A operação de `GetProcesses` é anotada com o atributo <xref:System.ServiceModel.Web.WebGetAttribute> que permite controlar como o WCF despacha solicitações HTTP GET para operações de serviço e especifica o formato das mensagens enviadas.</span><span class="sxs-lookup"><span data-stu-id="790ef-108">The `GetProcesses` operation is annotated with the <xref:System.ServiceModel.Web.WebGetAttribute> attribute that enables you to control how WCF dispatches HTTP GET requests to service operations and specify the format of the messages sent.</span></span>  
  
 <span data-ttu-id="790ef-109">Como qualquer serviço WCF, os feeds de distribuição podem ser hospedados automaticamente em qualquer aplicativo gerenciado.</span><span class="sxs-lookup"><span data-stu-id="790ef-109">Like any WCF service, syndication feeds can be self hosted in any managed application.</span></span> <span data-ttu-id="790ef-110">Os serviços de distribuição exigem uma associação específica (o <xref:System.ServiceModel.WebHttpBinding>) e um comportamento de ponto de extremidade específico (o <xref:System.ServiceModel.Description.WebHttpBehavior>) para funcionar corretamente.</span><span class="sxs-lookup"><span data-stu-id="790ef-110">Syndication services require a specific binding (the <xref:System.ServiceModel.WebHttpBinding>) and a specific endpoint behavior (the <xref:System.ServiceModel.Description.WebHttpBehavior>) to function correctly.</span></span> <span data-ttu-id="790ef-111">A nova classe <xref:System.ServiceModel.Web.WebServiceHost> fornece uma API conveniente para criar esses pontos de extremidade sem configuração específica.</span><span class="sxs-lookup"><span data-stu-id="790ef-111">The new <xref:System.ServiceModel.Web.WebServiceHost> class provides a convenient API for creating such endpoints without specific configuration.</span></span>  
  
```csharp  
WebServiceHost host = new WebServiceHost(typeof(ProcessService), new Uri("http://localhost:8000/diagnostics"));  
  
            //The WebServiceHost will automatically provide a default endpoint at the base address  
            //using the proper binding (the WebHttpBinding) and endpoint behavior (the WebHttpBehavior)  
```  
  
 <span data-ttu-id="790ef-112">Como alternativa, você pode usar <xref:System.ServiceModel.Activation.WebServiceHostFactory> de dentro de um arquivo. svc hospedado pelo IIS para fornecer funcionalidade equivalente (essa técnica não é demonstrada neste código de exemplo).</span><span class="sxs-lookup"><span data-stu-id="790ef-112">Alternatively, you can use <xref:System.ServiceModel.Activation.WebServiceHostFactory> from within an IIS-hosted .svc file to provide equivalent functionality (this technique is not demonstrated in this sample code).</span></span>  
  
```  
<%@ ServiceHost Language="C#|VB" Debug="true" Service="ProcessService" %>  
```  
  
 <span data-ttu-id="790ef-113">Como esse serviço recebe solicitações usando o HTTP GET padrão, você pode usar qualquer cliente com reconhecimento de RSS ou ATOM para acessar o serviço.</span><span class="sxs-lookup"><span data-stu-id="790ef-113">Because this service receives requests using the standard HTTP GET, you can use any RSS or ATOM-aware client to access the service.</span></span> <span data-ttu-id="790ef-114">Por exemplo, você pode exibir a saída desse serviço navegando até `http://localhost:8000/diagnostics/feed/?format=atom` ou `http://localhost:8000/diagnostics/feed/?format=rss` em um navegador com reconhecimento de RSS.</span><span class="sxs-lookup"><span data-stu-id="790ef-114">For example, you can view the output of this service by navigating to `http://localhost:8000/diagnostics/feed/?format=atom` or `http://localhost:8000/diagnostics/feed/?format=rss` in an RSS-aware browser.</span></span>
  
 <span data-ttu-id="790ef-115">Você também pode usar a [forma como o modelo de objeto de distribuição do WCF mapeia para Atom e RSS](../../../../docs/framework/wcf/feature-details/how-the-wcf-syndication-object-model-maps-to-atom-and-rss.md) para ler dados agregados e processá-los usando código imperativo.</span><span class="sxs-lookup"><span data-stu-id="790ef-115">You can also use the [How the WCF Syndication Object Model Maps to Atom and RSS](../../../../docs/framework/wcf/feature-details/how-the-wcf-syndication-object-model-maps-to-atom-and-rss.md) to read syndicated data and process it using imperative code.</span></span>  
  
```csharp  
XmlReader reader = XmlReader.Create( "http://localhost:8000/diagnostics/feed/?format=rss",  
new XmlReaderSettings()  
{  
//MaxCharactersInDocument can be used to control the maximum amount of data   
//read from the reader and helps prevent OutOfMemoryException  
MaxCharactersInDocument = 1024 * 64  
} );  
  
SyndicationFeed feed = SyndicationFeed.Load( reader );  
  
foreach (SyndicationItem i in feed.Items)  
{  
        XmlSyndicationContent content = i.Content as XmlSyndicationContent;  
        ProcessData pd = content.ReadContent<ProcessData>();  
  
        Console.WriteLine(i.Title.Text);  
        Console.WriteLine(pd.ToString());  
}  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="790ef-116">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="790ef-116">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="790ef-117">Verifique se você tem a permissão de registro de endereço correta para HTTP e HTTPS no computador, conforme explicado no procedimento configurar instruções no [processo de configuração única para os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="790ef-117">Ensure that you have the right address registration permission for HTTP and HTTPS on the computer as explained in the set up instructions in [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="790ef-118">{1&gt;Compile a solução.&lt;1}</span><span class="sxs-lookup"><span data-stu-id="790ef-118">Build the solution.</span></span>  
  
3. <span data-ttu-id="790ef-119">Execute o aplicativo de console.</span><span class="sxs-lookup"><span data-stu-id="790ef-119">Run the console application.</span></span>  
  
4. <span data-ttu-id="790ef-120">Enquanto o aplicativo de console estiver em execução, navegue até `http://localhost:8000/diagnostics/feed/?format=atom` ou `http://localhost:8000/diagnostics/feed/?format=rss` usando um navegador com reconhecimento de RSS.</span><span class="sxs-lookup"><span data-stu-id="790ef-120">While the console application is running, navigate to `http://localhost:8000/diagnostics/feed/?format=atom` or `http://localhost:8000/diagnostics/feed/?format=rss` using an RSS-aware browser.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="790ef-121">Os exemplos podem mais ser instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="790ef-121">The samples may already be installed on your computer.</span></span> <span data-ttu-id="790ef-122">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="790ef-122">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="790ef-123">Se esse diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos de Windows Workflow Foundation (WF) para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] amostras.</span><span class="sxs-lookup"><span data-stu-id="790ef-123">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="790ef-124">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="790ef-124">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Syndication\DiagnosticsFeed`  
  
## <a name="see-also"></a><span data-ttu-id="790ef-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="790ef-125">See also</span></span>

- [<span data-ttu-id="790ef-126">Modelo de programação HTTP Web do WCF</span><span class="sxs-lookup"><span data-stu-id="790ef-126">WCF Web HTTP Programming Model</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
- [<span data-ttu-id="790ef-127">Sindicalização do WCF</span><span class="sxs-lookup"><span data-stu-id="790ef-127">WCF Syndication</span></span>](../../../../docs/framework/wcf/feature-details/wcf-syndication.md)
