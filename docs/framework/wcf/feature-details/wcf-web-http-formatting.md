---
title: Formatação HTTP Web do WCF
ms.date: 03/30/2017
ms.assetid: e2414896-5463-41cd-b0a6-026a713eac2c
ms.openlocfilehash: abbfc74f33ddb676c8ac85eb712757615a2972ab
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33505161"
---
# <a name="wcf-web-http-formatting"></a>Formatação HTTP Web do WCF
O modelo de programação WCF Web HTTP permite que você determinar dinamicamente o melhor formato para uma operação de serviço retornar a resposta em. Há suporte para dois métodos para determinar um formato apropriado: automática e explícitas.  
  
## <a name="automatic-formatting"></a>Formatação automática  
 Quando habilitada, formatação automática escolhe o melhor formato no qual retornar a resposta. Determina o melhor formato verificando o seguinte, em ordem:  
  
1.  Os tipos de mídia no cabeçalho de aceitação da mensagem de solicitação.  
  
2.  O tipo de conteúdo da mensagem de solicitação.  
  
3.  O formato padrão definindo na operação.  
  
4.  O formato padrão definindo no WebHttpBehavior.  
  
 Se a mensagem de solicitação contiver um cabeçalho Accept a infraestrutura do Windows Communication Foundation (WCF) procura um tipo que oferece suporte a ele. Se o `Accept` cabeçalho Especifica prioridades para seus tipos de mídia, elas são consideradas. Se nenhum formato adequado foi encontrado no `Accept` cabeçalho, o tipo de conteúdo da mensagem de solicitação é usado. Se nenhum tipo de conteúdo adequado for especificado, a configuração para a operação do formato padrão é usado. O formato padrão é definido com o `ResponseFormat` parâmetro o <xref:System.ServiceModel.Web.WebGetAttribute> e <xref:System.ServiceModel.Web.WebInvokeAttribute> atributos. Se nenhum formato padrão é especificado na operação, o valor de <xref:System.ServiceModel.Description.WebHttpBehavior.DefaultOutgoingResponseFormat%2A> propriedade é usada. Formatação automática depende do <xref:System.ServiceModel.Description.WebHttpBehavior.AutomaticFormatSelectionEnabled%2A> propriedade. Quando essa propriedade é definida como `true`, a infraestrutura WCF determina o melhor formato a ser usado. Seleção automática de formato com versões anteriores é desabilitada por padrão para compatibilidade. Seleção automática de formato pode ser habilitada programaticamente ou por meio da configuração. O exemplo a seguir mostra como habilitar a seleção automática de formato no código.  
  
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
  
 Formatação automática também pode ser habilitado por meio da configuração. Você pode definir o <xref:System.ServiceModel.Description.WebHttpBehavior.AutomaticFormatSelectionEnabled%2A> propriedade diretamente no <xref:System.ServiceModel.Description.WebHttpBehavior> ou usando o <xref:System.ServiceModel.Description.WebHttpEndpoint>. O exemplo a seguir mostra como habilitar a seleção automática de formato no <xref:System.ServiceModel.Description.WebHttpBehavior>.  
  
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
  
## <a name="explicit-formatting"></a>Formatação de explícita  
 Como o nome implica, na formatação explícita, o desenvolvedor determina o melhor formato a ser usado dentro do código de operação. Se o melhor formato XML ou JSON define o desenvolvedor <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A> como <xref:System.ServiceModel.Web.WebMessageFormat.Xml> ou <xref:System.ServiceModel.Web.WebMessageFormat.Json>. Se o <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A> propriedade não está definida explicitamente e, em seguida, o formato padrão da operação é usado.  
  
 O exemplo a seguir verifica se o parâmetro de cadeia de caracteres de consulta de formato para um formato a ser usado. Se tiver sido especificado, define a operação Formatar usando <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A>.  
  
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
                 throw new WebFaultException<string>(string.Format("Unsupported format '{0}'", formatQueryStringValue), HttpStatusCode.BadRequest);  
            }  
        }  
        return "You said " + s;  
    }  
```  
  
 Se você precisar oferecer suporte a formatos diferentes de XML ou JSON, defina a operação para ter um tipo de retorno <xref:System.ServiceModel.Channels.Message>. Dentro do código de operação, determinar o formato apropriado para usar e, em seguida, criar um <xref:System.ServiceModel.Channels.Message> objeto usando um dos seguintes métodos:  
  
-   `WebOperationContext.CreateAtom10Response`  
  
-   `WebOperationContext.CreateJsonResponse`  
  
-   `WebOperationContext.CreateStreamResponse`  
  
-   `WebOperationContext.CreateTextResponse`  
  
-   `WebOperationContext.CreateXmlResponse`  
  
 Cada um desses métodos usa conteúda e cria uma mensagem com o formato apropriado. O `WebOperationContext.Current.IncomingRequest.GetAcceptHeaderElements` método pode ser usado para obter uma lista de formatos preferencial pelo cliente em ordem decrescente de preferência. O exemplo a seguir mostra como usar `WebOperationContext.Current.IncomingRequest.GetAcceptHeaderElements` para determinar o formato a ser usado e, em seguida, usa o método de resposta para criar a mensagem de resposta create apropriada.  
  
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
