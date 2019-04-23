---
title: Exemplo de feed de diagnóstico independente
ms.date: 03/30/2017
ms.assetid: d31c6c1f-292c-4d95-8e23-ed8565970ea5
ms.openlocfilehash: 2737621a98f6a7e89ef3aee01fd1ad7a2a60f9b5
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59316551"
---
# <a name="stand-alone-diagnostics-feed-sample"></a><span data-ttu-id="bf5e3-102">Exemplo de feed de diagnóstico independente</span><span class="sxs-lookup"><span data-stu-id="bf5e3-102">Stand-Alone Diagnostics Feed Sample</span></span>
<span data-ttu-id="bf5e3-103">Este exemplo demonstra como criar um RSS/Atom feed de sindicalização com o Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="bf5e3-103">This sample demonstrates how to create an RSS/Atom feed for syndication with Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="bf5e3-104">É um programa "Hello World" básico que mostra as Noções básicas do modelo de objeto e como configurá-lo em um serviço do Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="bf5e3-104">It is a basic "Hello World" program that shows the basics of the object model and how to set it up on a Windows Communication Foundation (WCF) service.</span></span>  
  
 <span data-ttu-id="bf5e3-105">WCF modela os feeds de agregação como operações de serviço que retornam um tipo de dados especial <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter>.</span><span class="sxs-lookup"><span data-stu-id="bf5e3-105">WCF models syndication feeds as service operations that return a special data type, <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter>.</span></span> <span data-ttu-id="bf5e3-106">Instâncias de <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> pode serializar um feed em formatos de RSS 2.0 e Atom 1.0.</span><span class="sxs-lookup"><span data-stu-id="bf5e3-106">Instances of <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> can serialize a feed into both the RSS 2.0 and Atom 1.0 formats.</span></span> <span data-ttu-id="bf5e3-107">O código de exemplo a seguir mostra o contrato usado.</span><span class="sxs-lookup"><span data-stu-id="bf5e3-107">The following sample code shows the contract used.</span></span>  
  
```  
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
  
 <span data-ttu-id="bf5e3-108">O `GetProcesses` operação é anotada com a <xref:System.ServiceModel.Web.WebGetAttribute> solicitações de atributo que permite que você controle como o WCF expede HTTP GET a operações de serviço e especificar o formato das mensagens enviadas.</span><span class="sxs-lookup"><span data-stu-id="bf5e3-108">The `GetProcesses` operation is annotated with the <xref:System.ServiceModel.Web.WebGetAttribute> attribute that enables you to control how WCF dispatches HTTP GET requests to service operations and specify the format of the messages sent.</span></span>  
  
 <span data-ttu-id="bf5e3-109">Como qualquer serviço WCF, feeds de agregação podem ser auto-hospedado em qualquer aplicativo gerenciado.</span><span class="sxs-lookup"><span data-stu-id="bf5e3-109">Like any WCF service, syndication feeds can be self hosted in any managed application.</span></span> <span data-ttu-id="bf5e3-110">Serviços de distribuição requerem uma associação específica (o <xref:System.ServiceModel.WebHttpBinding>) e um comportamento de ponto de extremidade específico (o <xref:System.ServiceModel.Description.WebHttpBehavior>) para funcionar corretamente.</span><span class="sxs-lookup"><span data-stu-id="bf5e3-110">Syndication services require a specific binding (the <xref:System.ServiceModel.WebHttpBinding>) and a specific endpoint behavior (the <xref:System.ServiceModel.Description.WebHttpBehavior>) to function correctly.</span></span> <span data-ttu-id="bf5e3-111">O novo <xref:System.ServiceModel.Web.WebServiceHost> classe fornece uma API conveniente para a criação de tais pontos de extremidade sem configuração específica.</span><span class="sxs-lookup"><span data-stu-id="bf5e3-111">The new <xref:System.ServiceModel.Web.WebServiceHost> class provides a convenient API for creating such endpoints without specific configuration.</span></span>  
  
```  
WebServiceHost host = new WebServiceHost(typeof(ProcessService), new Uri("http://localhost:8000/diagnostics"));  
  
            //The WebServiceHost will automatically provide a default endpoint at the base address  
            //using the proper binding (the WebHttpBinding) and endpoint behavior (the WebHttpBehavior)  
```  
  
 <span data-ttu-id="bf5e3-112">Como alternativa, você pode usar <xref:System.ServiceModel.Activation.WebServiceHostFactory> de dentro de um arquivo. svc de hospedados no IIS para fornecer funcionalidade equivalente (essa técnica não é demonstrada neste código de exemplo).</span><span class="sxs-lookup"><span data-stu-id="bf5e3-112">Alternatively, you can use <xref:System.ServiceModel.Activation.WebServiceHostFactory> from within an IIS-hosted .svc file to provide equivalent functionality (this technique is not demonstrated in this sample code).</span></span>  
  
```  
<%@ ServiceHost Language="C#|VB" Debug="true" Service="ProcessService" %>  
```  
  
 <span data-ttu-id="bf5e3-113">Como esse serviço recebe solicitações que usam o HTTP padrão GET, você pode usar qualquer cliente RSS ou reconhecimento do ATOM para acessar o serviço.</span><span class="sxs-lookup"><span data-stu-id="bf5e3-113">Because this service receives requests using the standard HTTP GET, you can use any RSS or ATOM-aware client to access the service.</span></span> <span data-ttu-id="bf5e3-114">Por exemplo, você pode exibir a saída desse serviço, navegando até `http://localhost:8000/diagnostics/feed/?format=atom` ou `http://localhost:8000/diagnostics/feed/?format=rss` em um navegador com suporte a RSS.</span><span class="sxs-lookup"><span data-stu-id="bf5e3-114">For example, you can view the output of this service by navigating to `http://localhost:8000/diagnostics/feed/?format=atom` or `http://localhost:8000/diagnostics/feed/?format=rss` in an RSS-aware browser.</span></span>
  
 <span data-ttu-id="bf5e3-115">Você também pode usar o [como o WCF Sindicalização objeto modelo é mapeado para Atom e RSS](../../../../docs/framework/wcf/feature-details/how-the-wcf-syndication-object-model-maps-to-atom-and-rss.md) para ler dados agregados e processá-lo usando o código obrigatório.</span><span class="sxs-lookup"><span data-stu-id="bf5e3-115">You can also use the [How the WCF Syndication Object Model Maps to Atom and RSS](../../../../docs/framework/wcf/feature-details/how-the-wcf-syndication-object-model-maps-to-atom-and-rss.md) to read syndicated data and process it using imperative code.</span></span>  
  
```  
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
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="bf5e3-116">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="bf5e3-116">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="bf5e3-117">Certifique-se de que você tenha a permissão de registro de endereço à direita para HTTP e HTTPS no computador, conforme explicado no conjunto de instruções em [procedimento de configuração de uso único para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="bf5e3-117">Ensure that you have the right address registration permission for HTTP and HTTPS on the computer as explained in the set up instructions in [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="bf5e3-118">Compile a solução.</span><span class="sxs-lookup"><span data-stu-id="bf5e3-118">Build the solution.</span></span>  
  
3. <span data-ttu-id="bf5e3-119">Execute o aplicativo de console.</span><span class="sxs-lookup"><span data-stu-id="bf5e3-119">Run the console application.</span></span>  
  
4. <span data-ttu-id="bf5e3-120">Durante a execução do aplicativo de console, navegue até `http://localhost:8000/diagnostics/feed/?format=atom` ou `http://localhost:8000/diagnostics/feed/?format=rss` usando um navegador com suporte a RSS.</span><span class="sxs-lookup"><span data-stu-id="bf5e3-120">While the console application is running, navigate to `http://localhost:8000/diagnostics/feed/?format=atom` or `http://localhost:8000/diagnostics/feed/?format=rss` using an RSS-aware browser.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="bf5e3-121">Os exemplos podem mais ser instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="bf5e3-121">The samples may already be installed on your computer.</span></span> <span data-ttu-id="bf5e3-122">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="bf5e3-122">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="bf5e3-123">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="bf5e3-123">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="bf5e3-124">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="bf5e3-124">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Syndication\DiagnosticsFeed`  
  
## <a name="see-also"></a><span data-ttu-id="bf5e3-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bf5e3-125">See also</span></span>

- [<span data-ttu-id="bf5e3-126">Modelo de programação HTTP Web do WCF</span><span class="sxs-lookup"><span data-stu-id="bf5e3-126">WCF Web HTTP Programming Model</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
- [<span data-ttu-id="bf5e3-127">Sindicalização do WCF</span><span class="sxs-lookup"><span data-stu-id="bf5e3-127">WCF Syndication</span></span>](../../../../docs/framework/wcf/feature-details/wcf-syndication.md)
