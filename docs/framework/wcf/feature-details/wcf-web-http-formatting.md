---
title: Formatação HTTP da WCF Web
ms.date: 03/30/2017
ms.assetid: e2414896-5463-41cd-b0a6-026a713eac2c
ms.openlocfilehash: b6c9728fe40e26977366b73337e72b1514a12a19
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184194"
---
# <a name="wcf-web-http-formatting"></a>Formatação HTTP da WCF Web
O modelo de programação WCF Web HTTP permite determinar dinamicamente o melhor formato para uma operação de serviço retornar sua resposta. Dois métodos para determinar um formato apropriado são suportados: automático e explícito.  
  
## <a name="automatic-formatting"></a>Formatação automática  
 Quando ativado, a formatação automática escolhe o melhor formato para retornar a resposta. Ele determina o melhor formato verificando o seguinte, em ordem:  
  
1. Os tipos de mídia no cabeçalho aceitar da mensagem de solicitação.  
  
2. O tipo de conteúdo da mensagem de solicitação.  
  
3. A configuração de formato padrão na operação.  
  
4. A configuração de formato padrão na WebHttpBehavior.  
  
 Se a mensagem de solicitação contiver um cabeçalho Aceitar, a infra-estrutura da Windows Communication Foundation (WCF) procurará um tipo que ele suporta. Se `Accept` o cabeçalho especificar prioridades para seus tipos de mídia, eles serão honrados. Se nenhum formato adequado `Accept` for encontrado no cabeçalho, o tipo de conteúdo da mensagem de solicitação será usado. Se nenhum tipo de conteúdo adequado for especificado, a configuração de formato padrão para a operação será usada. O formato padrão é `ResponseFormat` definido com <xref:System.ServiceModel.Web.WebGetAttribute> <xref:System.ServiceModel.Web.WebInvokeAttribute> o parâmetro dos atributos e. Se nenhum formato padrão for especificado na <xref:System.ServiceModel.Description.WebHttpBehavior.DefaultOutgoingResponseFormat%2A> operação, o valor da propriedade será usado. A formatação automática <xref:System.ServiceModel.Description.WebHttpBehavior.AutomaticFormatSelectionEnabled%2A> depende da propriedade. Quando esta propriedade `true`é definida como , a infra-estrutura WCF determina o melhor formato a ser usado. A seleção automática do formato é desativada por padrão para retrocompatibilidade. A seleção automática do formato pode ser ativada de forma programática ou através da configuração. O exemplo a seguir mostra como ativar a seleção automática de formato em código.  
  
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
  
 A formatação automática também pode ser ativada através da configuração. Você pode <xref:System.ServiceModel.Description.WebHttpBehavior.AutomaticFormatSelectionEnabled%2A> definir a <xref:System.ServiceModel.Description.WebHttpBehavior> propriedade diretamente <xref:System.ServiceModel.Description.WebHttpEndpoint>no ou usando o . O exemplo a seguir mostra como ativar <xref:System.ServiceModel.Description.WebHttpBehavior>a seleção automática de formato no .  
  
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
  
 O exemplo a seguir mostra como <xref:System.ServiceModel.Description.WebHttpEndpoint>ativar a seleção automática de formatos usando .  
  
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
  
## <a name="explicit-formatting"></a>Formatação explícita  
 Como o nome indica, na formatação explícita o desenvolvedor determina o melhor formato a ser usado dentro do código de operação. Se o melhor formato for XML ou <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A> JSON, o desenvolvedor definirá para ou <xref:System.ServiceModel.Web.WebMessageFormat.Xml> . <xref:System.ServiceModel.Web.WebMessageFormat.Json> Se <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A> a propriedade não estiver explicitamente definida, o formato padrão da operação será usado.  
  
 O exemplo a seguir verifica o parâmetro de seqüência de string de consulta de formato para um formato a ser usado. Se tiver sido especificado, ele define o <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A>formato da operação usando .  
  
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
  
 Se você precisar de suporte a formatos diferentes de XML ou <xref:System.ServiceModel.Channels.Message>JSON, defina sua operação para ter um tipo de retorno de . Dentro do código de operação, determine o <xref:System.ServiceModel.Channels.Message> formato apropriado para usar e, em seguida, crie um objeto usando um dos seguintes métodos:  
  
- `WebOperationContext.CreateAtom10Response`  
  
- `WebOperationContext.CreateJsonResponse`  
  
- `WebOperationContext.CreateStreamResponse`  
  
- `WebOperationContext.CreateTextResponse`  
  
- `WebOperationContext.CreateXmlResponse`  
  
 Cada um desses métodos pega conteúdo e cria uma mensagem com o formato apropriado. O `WebOperationContext.Current.IncomingRequest.GetAcceptHeaderElements` método pode ser usado para obter uma lista de formatos preferidos pelo cliente, a fim de diminuir a preferência. O exemplo a seguir `WebOperationContext.Current.IncomingRequest.GetAcceptHeaderElements` mostra como usar para determinar o formato a ser usado e, em seguida, usa o método de resposta de criação apropriado para criar a mensagem de resposta.  
  
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
  
## <a name="see-also"></a>Confira também

- <xref:System.UriTemplate>
- <xref:System.UriTemplateMatch>
- [Modelo de programação WCF Web HTTP](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
- [UriTemplate and UriTemplateTable](../../../../docs/framework/wcf/feature-details/uritemplate-and-uritemplatetable.md)
- [Visão geral do modelo de programação HTTP Web do WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model-overview.md)
- [Modelo de objeto de programação HTTP Web do WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-object-model.md)
