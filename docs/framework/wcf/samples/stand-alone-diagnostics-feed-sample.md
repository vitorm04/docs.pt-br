---
title: "Exemplo de feed de diagnóstico independente"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d31c6c1f-292c-4d95-8e23-ed8565970ea5
caps.latest.revision: "26"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 89de6bcbb44ca70592697ccf891099446b230ce6
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="stand-alone-diagnostics-feed-sample"></a>Exemplo de feed de diagnóstico independente
Este exemplo demonstra como criar um feed de distribuição com RSS/Atom [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]. É um programa "Hello World" básico que mostra os fundamentos de como o modelo de objeto e como configurá-lo em um [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] serviço.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]modelos de feeds de agregação como operações de serviço que retornam um tipo de dados especial <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter>. Instâncias do <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> pode serializar um feed em formatos de RSS 2.0 e Atom 1.0. O código de exemplo a seguir mostra o contrato usado.  
  
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
  
 O `GetProcesses` operação é anotada com a <xref:System.ServiceModel.Web.WebGetAttribute> atributo que permite que você controle como [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] envia solicitações HTTP GET para operações de serviço e especificar o formato das mensagens enviadas.  
  
 Como qualquer [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviço, feeds de agregação podem ser próprio hospedados em qualquer aplicativo gerenciado. Serviços de distribuição exigem uma associação específica (o <xref:System.ServiceModel.WebHttpBinding>) e um comportamento de ponto de extremidade específico (o <xref:System.ServiceModel.Description.WebHttpBehavior>) para funcionar corretamente. O novo <xref:System.ServiceModel.Web.WebServiceHost> classe fornece uma API conveniente para a criação de tais pontos de extremidade sem configuração específica.  
  
```  
WebServiceHost host = new WebServiceHost(typeof(ProcessService), new Uri("http://localhost:8000/diagnostics"));  
  
            //The WebServiceHost will automatically provide a default endpoint at the base address  
            //using the proper binding (the WebHttpBinding) and endpoint behavior (the WebHttpBehavior)  
```  
  
 Como alternativa, você pode usar <xref:System.ServiceModel.Activation.WebServiceHostFactory> de dentro de um arquivo. svc hospedados no IIS para fornecer funcionalidade equivalente (essa técnica não será demonstrada neste código de exemplo).  
  
```  
<%@ ServiceHost Language="C#|VB" Debug="true" Service="ProcessService" %>  
```  
  
 Como este serviço recebe solicitações que usam o padrão HTTP GET, você pode usar qualquer cliente RSS ou ATOM reconhecimento para acessar o serviço. Por exemplo, você pode exibir a saída desse serviço, navegando até o feed/de diagnóstico de http://localhost:8000 /? formato = atom ou feed/de diagnóstico de http://localhost:8000 /? formato = rss em um navegador com suporte a RSS, como o Internet Explorer 7.  
  
 Você também pode usar o [como o WCF Syndication objeto modelo mapeia para Atom e RSS](../../../../docs/framework/wcf/feature-details/how-the-wcf-syndication-object-model-maps-to-atom-and-rss.md) para ler dados distribuídos e processá-la usando o código obrigatório.  
  
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
  
### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1.  Verifique se você tem a permissão de registro de endereço para HTTP e HTTPS no computador, conforme explicado no conjunto de backup instruções [único procedimento de instalação para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Compile a solução.  
  
3.  Execute o aplicativo de console.  
  
4.  Durante a execução do aplicativo de console, navegue até o feed/de diagnóstico de http://localhost:8000 /? formato = atom ou feed/de diagnóstico de http://localhost:8000 /? formato = rss usando um navegador com suporte para RSS.  
  
> [!IMPORTANT]
>  Os exemplos podem mais ser instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Syndication\DiagnosticsFeed`  
  
## <a name="see-also"></a>Consulte também  
 [Modelo de programação WCF Web HTTP](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)  
 [Sindicalização do WCF](../../../../docs/framework/wcf/feature-details/wcf-syndication.md)
