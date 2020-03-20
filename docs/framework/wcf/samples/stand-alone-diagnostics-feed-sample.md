---
title: Exemplo de feed de diagnóstico independente
ms.date: 03/30/2017
ms.assetid: d31c6c1f-292c-4d95-8e23-ed8565970ea5
ms.openlocfilehash: 29d8caee48925040db9f1812f015870e3a1272bc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144000"
---
# <a name="stand-alone-diagnostics-feed-sample"></a>Exemplo de feed de diagnóstico independente
Esta amostra demonstra como criar um feed RSS/Atom para sindicância com a Windows Communication Foundation (WCF). É um programa básico "Hello World" que mostra o básico do modelo de objeto e como configurá-lo em um serviço da Windows Communication Foundation (WCF).  
  
 Os modelos wcf alimentam-se como operações de <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter>serviço que retornam um tipo de dados especial, . As <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> instâncias de pode serializar um feed nos formatos RSS 2.0 e Atom 1.0. O seguinte código de amostra mostra o contrato utilizado.  
  
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
  
 A `GetProcesses` operação é anotada <xref:System.ServiceModel.Web.WebGetAttribute> com o atributo que permite controlar como o WCF despacha as solicitações HTTP GET para operações de serviço e especificar o formato das mensagens enviadas.  
  
 Como qualquer serviço WCF, os feeds de sindicância podem ser auto-hospedados em qualquer aplicativo gerenciado. Os serviços de sindicalização exigem <xref:System.ServiceModel.WebHttpBinding>uma vinculação específica (o ) e um comportamento específico de ponto final (o <xref:System.ServiceModel.Description.WebHttpBehavior>) para funcionar corretamente. A <xref:System.ServiceModel.Web.WebServiceHost> nova classe fornece uma API conveniente para criar tais pontos finais sem configuração específica.  
  
```csharp  
WebServiceHost host = new WebServiceHost(typeof(ProcessService), new Uri("http://localhost:8000/diagnostics"));  
  
            //The WebServiceHost will automatically provide a default endpoint at the base address  
            //using the proper binding (the WebHttpBinding) and endpoint behavior (the WebHttpBehavior)  
```  
  
 Alternativamente, você <xref:System.ServiceModel.Activation.WebServiceHostFactory> pode usar a partir de um arquivo .svc hospedado pelo IIS para fornecer funcionalidade equivalente (essa técnica não é demonstrada neste código de amostra).  
  
```xml
<%@ ServiceHost Language="C#|VB" Debug="true" Service="ProcessService" %>
```
  
 Como este serviço recebe solicitações usando o HTTP GET padrão, você pode usar qualquer cliente consciente de RSS ou ATOM para acessar o serviço. Por exemplo, você pode visualizar a saída `http://localhost:8000/diagnostics/feed/?format=atom` deste `http://localhost:8000/diagnostics/feed/?format=rss` serviço navegando para ou em um navegador com reconhecimento RSS.
  
 Você também pode usar o [Modelo de Objeto de Sindicância WCF para Átomo e RSS](../../../../docs/framework/wcf/feature-details/how-the-wcf-syndication-object-model-maps-to-atom-and-rss.md) para ler dados sindicalizados e processá-los usando código imperativo.  
  
```csharp
XmlReader reader = XmlReader.Create( "http://localhost:8000/diagnostics/feed/?format=rss",
    new XmlReaderSettings()
    {
        //MaxCharactersInDocument can be used to control the maximum amount of data
        //read from the reader and helps prevent OutOfMemoryException
        MaxCharactersInDocument = 1024 * 64
    } );

SyndicationFeed feed = SyndicationFeed.Load(reader);

foreach (SyndicationItem i in feed.Items)
{
    XmlSyndicationContent content = i.Content as XmlSyndicationContent;
    ProcessData pd = content.ReadContent<ProcessData>();

    Console.WriteLine(i.Title.Text);
    Console.WriteLine(pd.ToString());
}
```
  
## <a name="set-up-build-and-run-the-sample"></a>Configurar, construir e executar a amostra
  
1. Certifique-se de que você tem a permissão de registro de endereço certa para HTTP e HTTPS no computador, conforme explicado nas instruções de configuração no [Procedimento de Configuração Única para as Amostras da Fundação de Comunicação do Windows](one-time-setup-procedure-for-the-wcf-samples.md).

2. Compile a solução.

3. Execute o aplicativo de console.

4. Enquanto o aplicativo do `http://localhost:8000/diagnostics/feed/?format=atom` console `http://localhost:8000/diagnostics/feed/?format=rss` estiver em execução, navegue para ou usando um navegador com reconhecimento RSS.

> [!IMPORTANT]
> Os exemplos podem mais ser instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation). Este exemplo está localizado no seguinte diretório.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Syndication\DiagnosticsFeed`

## <a name="see-also"></a>Confira também

- [Modelo de programação WCF Web HTTP](../feature-details/wcf-web-http-programming-model.md)
- [Sindicalização do WCF](../feature-details/wcf-syndication.md)
