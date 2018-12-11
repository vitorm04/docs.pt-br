---
title: Formatação HTTP Web do WCF
ms.date: 03/30/2017
ms.assetid: e2414896-5463-41cd-b0a6-026a713eac2c
ms.openlocfilehash: 3a5164cb6271c8fd1d67b3c59fd35705d997f9fe
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53238436"
---
# <a name="wcf-web-http-formatting"></a>Formatação HTTP Web do WCF
O modelo de programação WCF Web HTTP permite que você determinar dinamicamente o melhor formato para uma operação de serviço retornar a resposta em. Há suporte para dois métodos para determinar um formato apropriado: automático e explícito.  
  
## <a name="automatic-formatting"></a>Formatação automática  
 Quando habilitada, a formatação automática escolhe o melhor formato no qual retornar a resposta. Ele determina o melhor formato, verificando o seguinte, em ordem:  
  
1.  Os tipos de mídia no cabeçalho de aceitação da mensagem de solicitação.  
  
2.  O tipo de conteúdo da mensagem de solicitação.  
  
3.  O formato padrão definindo na operação.  
  
4.  O formato padrão definindo no WebHttpBehavior.  
  
 Se a mensagem de solicitação contiver um cabeçalho Accept a infraestrutura do Windows Communication Foundation (WCF) procura por um tipo que oferece suporte a ele. Se o `Accept` cabeçalho Especifica prioridades para seus tipos de mídia, elas são consideradas. Se nenhum formato adequado for encontrado no `Accept` cabeçalho, o tipo de conteúdo da mensagem de solicitação é usado. Se nenhum tipo de conteúdo adequado for especificado, a configuração para a operação de formato de padrão é usado. O formato padrão é definido com o `ResponseFormat` parâmetro do <xref:System.ServiceModel.Web.WebGetAttribute> e <xref:System.ServiceModel.Web.WebInvokeAttribute> atributos. Se nenhum formato padrão for especificado na operação, o valor da <xref:System.ServiceModel.Description.WebHttpBehavior.DefaultOutgoingResponseFormat%2A> propriedade é usada. Formatação automática depende o <xref:System.ServiceModel.Description.WebHttpBehavior.AutomaticFormatSelectionEnabled%2A> propriedade. Quando essa propriedade é definida como `true`, a infraestrutura WCF determina o melhor formato para usar. Seleção automática de formato com versões anteriores é desabilitada por padrão para compatibilidade. Seleção automática de formato pode ser habilitada programaticamente ou por meio da configuração. O exemplo a seguir mostra como habilitar a seleção automática de formato no código.  
  
```csharp
// This code assumes the service name is MyService and the service contract is IMyContract     
Uri baseAddress = new Uri("http://localhost:8000");  
  
WebServiceHost host = new WebServiceHost(typeof(MyService), baseAddress)  
try  
{  
   ServiceEndpoint sep = host.AddServiceEndpoint(typeof(IMyContract), new WebHttpBinding(), "");  
   // Check it see if the WebHttpBehavior already exists  
   WebHttpBehavior whb = sep.Behaviors.Find<WebHttpBehavior>();  
  
   if (whb != null)  
   {  
      whb.AutomaticFormatSelectionEnabled = true;  
   }  
   else  
   {  
      WebHttpBehavior webBehavior = new WebHttpBehavior();  
      webBehavior.AutomaticFormatSelectionEnabled = true;  
      sep.Behaviors.Add(webBehavior);  
   }  
         // Open host to start listening for messages  
   host.Open();        
  
  // ...  
}  
  catch(CommunicationException ex)  
  {  
     Console.WriteLine("An exception occurred: " + ex.Message());  
  }  
```  
  
 Formatação automática também pode ser habilitada por meio da configuração. Você pode definir as <xref:System.ServiceModel.Description.WebHttpBehavior.AutomaticFormatSelectionEnabled%2A> propriedade diretamente na <xref:System.ServiceModel.Description.WebHttpBehavior> ou usando o <xref:System.ServiceModel.Description.WebHttpEndpoint>. O exemplo a seguir mostra como habilitar a seleção automática de formato no <xref:System.ServiceModel.Description.WebHttpBehavior>.  
  
```xml  
<system.serviceModel>  
  <behaviors>  
    <endpointBehaviors>  
      <behavior>  
        <webHttp automaticFormatSelectionEnabled="true" />  
      </behavior>  
    </endpointBehaviors>  
  </behaviors>  
  <standardEndpoints>  
    <webHttpEndpoint>  
      <!-- the "" standard endpoint is used by WebServiceHost for auto creating a web endpoint. -->  
      <standardEndpoint name="" helpEnabled="true" />  
    </webHttpEndpoint>  
  </standardEndpoints>  
</system.serviceModel>  
```  
  
 O exemplo a seguir mostra como habilitar o uso de seleção automática de formato <xref:System.ServiceModel.Description.WebHttpEndpoint>.  
  
```xml  
<system.serviceModel>  
    <standardEndpoints>  
      <webHttpEndpoint>  
        <!-- the "" standard endpoint is used by WebServiceHost for auto creating a web endpoint. -->  
        <standardEndpoint name="" helpEnabled="true" automaticFormatSelectionEnabled="true"  />  
      </webHttpEndpoint>  
    </standardEndpoints>  
  </system.serviceModel>  
```  
  
## <a name="explicit-formatting"></a>Explicit formatação  
 Como o nome implica, o desenvolvedor determina o melhor formato para usar dentro do código de operação na formatação explícita. Se o melhor formato de for XML ou JSON o desenvolvedor define <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A> para um <xref:System.ServiceModel.Web.WebMessageFormat.Xml> ou <xref:System.ServiceModel.Web.WebMessageFormat.Json>. Se o <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A> propriedade não está definida explicitamente, o formato de padrão da operação é usado.  
  
 O exemplo a seguir verifica se o parâmetro de cadeia de caracteres de consulta de formato para um formato a ser usado. Se ele tiver sido especificado, ele define a operação de formato usando <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A>.  
  
```csharp
public class Service : IService  
{  
    [WebGet]  
     public string EchoWithGet(string s)  
    {  
        // if a format query string parameter has been specified, set the response format to that. If no such
        // query string parameter exists the Accept header will be used
        string formatQueryStringValue = WebOperationContext.Current.IncomingRequest.UriTemplateMatch.QueryParameters["format"];  
        if (!string.IsNullOrEmpty(formatQueryStringValue))  
        {  
            if (formatQueryStringValue.Equals("xml", System.StringComparison.OrdinalIgnoreCase))  
            {
                WebOperationContext.Current.OutgoingResponse.Format = WebMessageFormat.Xml;
            }
            else if (formatQueryStringValue.Equals("json", System.StringComparison.OrdinalIgnoreCase))  
            {  
                WebOperationContext.Current.OutgoingResponse.Format = WebMessageFormat.Json;  
            }  
            else  
            {  
                throw new WebFaultException<string>($"Unsupported format '{formatQueryStringValue}'",   HttpStatusCode.BadRequest);
            }  
        }  
        return "You said " + s;  
    }  
```  
  
 Se você precisar dar suporte a formatos diferentes como XML ou JSON, defina sua operação para ter um tipo de retorno <xref:System.ServiceModel.Channels.Message>. Dentro do código de operação, determinar o formato apropriado para usar e, em seguida, criar um <xref:System.ServiceModel.Channels.Message> objeto usando um dos seguintes métodos:  
  
-   `WebOperationContext.CreateAtom10Response`  
  
-   `WebOperationContext.CreateJsonResponse`  
  
-   `WebOperationContext.CreateStreamResponse`  
  
-   `WebOperationContext.CreateTextResponse`  
  
-   `WebOperationContext.CreateXmlResponse`  
  
 Cada um desses métodos leva conteúda e cria uma mensagem com o formato apropriado. O `WebOperationContext.Current.IncomingRequest.GetAcceptHeaderElements` método pode ser usado para obter uma lista dos formatos preferido pelo cliente em ordem decrescente de preferência. O exemplo a seguir mostra como usar `WebOperationContext.Current.IncomingRequest.GetAcceptHeaderElements` para determinar o formato para uso e, em seguida, usa o método de resposta para criar a mensagem de resposta cria apropriado.  
  
```csharp
public class Service : IService  
{  
    public Message EchoListWithGet(string list)  
    {  
        List<string> returnList = new List<string>(list.Split(new char[] { ',' }, StringSplitOptions.RemoveEmptyEntries));  
        IList<ContentType> acceptHeaderElements = WebOperationContext.Current.IncomingRequest.GetAcceptHeaderElements();  
        for (int x = 0; x < acceptHeaderElements.Count; x++)  
        {  
            string normalizedMediaType = acceptHeaderElements[x].MediaType.ToLowerInvariant();  
            switch (normalizedMediaType)  
            {  
                case "image/jpeg": return CreateJpegResponse(returnList);  
                case "application/xhtml+xml": return CreateXhtmlResponse(returnList);  
                case "application/atom+xml": return CreateAtom10Response(returnList);  
                case "application/xml": return CreateXmlResponse(returnList);  
                case "application/json": return CreateJsonResponse(returnList);  
          }  
    }  
  
    // Default response format is XML  
    return CreateXmlResponse(returnList);  
    }  
}  
```  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.UriTemplate>  
 <xref:System.UriTemplateMatch>  
 [Modelo de programação HTTP Web do WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)  
 [UriTemplate e UriTemplateTable](../../../../docs/framework/wcf/feature-details/uritemplate-and-uritemplatetable.md)  
 [Visão geral do modelo de programação HTTP Web do WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model-overview.md)  
 [Modelo de objeto de programação HTTP Web do WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-object-model.md)
