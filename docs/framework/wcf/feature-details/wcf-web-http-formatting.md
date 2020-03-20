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
# <a name="wcf-web-http-formatting"></a><span data-ttu-id="13d52-102">Formatação HTTP da WCF Web</span><span class="sxs-lookup"><span data-stu-id="13d52-102">WCF Web HTTP formatting</span></span>
<span data-ttu-id="13d52-103">O modelo de programação WCF Web HTTP permite determinar dinamicamente o melhor formato para uma operação de serviço retornar sua resposta.</span><span class="sxs-lookup"><span data-stu-id="13d52-103">The WCF Web HTTP programming model allows you to dynamically determine the best format for a service operation to return its response in.</span></span> <span data-ttu-id="13d52-104">Dois métodos para determinar um formato apropriado são suportados: automático e explícito.</span><span class="sxs-lookup"><span data-stu-id="13d52-104">Two methods for determining an appropriate format are supported: automatic and explicit.</span></span>  
  
## <a name="automatic-formatting"></a><span data-ttu-id="13d52-105">Formatação automática</span><span class="sxs-lookup"><span data-stu-id="13d52-105">Automatic formatting</span></span>  
 <span data-ttu-id="13d52-106">Quando ativado, a formatação automática escolhe o melhor formato para retornar a resposta.</span><span class="sxs-lookup"><span data-stu-id="13d52-106">When enabled, automatic formatting chooses the best format in which to return the response.</span></span> <span data-ttu-id="13d52-107">Ele determina o melhor formato verificando o seguinte, em ordem:</span><span class="sxs-lookup"><span data-stu-id="13d52-107">It determines the best format by checking the following, in order:</span></span>  
  
1. <span data-ttu-id="13d52-108">Os tipos de mídia no cabeçalho aceitar da mensagem de solicitação.</span><span class="sxs-lookup"><span data-stu-id="13d52-108">The media types in the request message’s Accept header.</span></span>  
  
2. <span data-ttu-id="13d52-109">O tipo de conteúdo da mensagem de solicitação.</span><span class="sxs-lookup"><span data-stu-id="13d52-109">The content-type of the request message.</span></span>  
  
3. <span data-ttu-id="13d52-110">A configuração de formato padrão na operação.</span><span class="sxs-lookup"><span data-stu-id="13d52-110">The default format setting in the operation.</span></span>  
  
4. <span data-ttu-id="13d52-111">A configuração de formato padrão na WebHttpBehavior.</span><span class="sxs-lookup"><span data-stu-id="13d52-111">The default format setting in the WebHttpBehavior.</span></span>  
  
 <span data-ttu-id="13d52-112">Se a mensagem de solicitação contiver um cabeçalho Aceitar, a infra-estrutura da Windows Communication Foundation (WCF) procurará um tipo que ele suporta.</span><span class="sxs-lookup"><span data-stu-id="13d52-112">If the request message contains an Accept header the Windows Communication Foundation (WCF) infrastructure searches for a type that it supports.</span></span> <span data-ttu-id="13d52-113">Se `Accept` o cabeçalho especificar prioridades para seus tipos de mídia, eles serão honrados.</span><span class="sxs-lookup"><span data-stu-id="13d52-113">If the `Accept` header specifies priorities for its media types, they are honored.</span></span> <span data-ttu-id="13d52-114">Se nenhum formato adequado `Accept` for encontrado no cabeçalho, o tipo de conteúdo da mensagem de solicitação será usado.</span><span class="sxs-lookup"><span data-stu-id="13d52-114">If no suitable format is found in the `Accept` header, the content-type of the request message is used.</span></span> <span data-ttu-id="13d52-115">Se nenhum tipo de conteúdo adequado for especificado, a configuração de formato padrão para a operação será usada.</span><span class="sxs-lookup"><span data-stu-id="13d52-115">If no suitable content-type is specified, the default format setting for the operation is used.</span></span> <span data-ttu-id="13d52-116">O formato padrão é `ResponseFormat` definido com <xref:System.ServiceModel.Web.WebGetAttribute> <xref:System.ServiceModel.Web.WebInvokeAttribute> o parâmetro dos atributos e.</span><span class="sxs-lookup"><span data-stu-id="13d52-116">The default format is set with the `ResponseFormat` parameter of the <xref:System.ServiceModel.Web.WebGetAttribute> and <xref:System.ServiceModel.Web.WebInvokeAttribute> attributes.</span></span> <span data-ttu-id="13d52-117">Se nenhum formato padrão for especificado na <xref:System.ServiceModel.Description.WebHttpBehavior.DefaultOutgoingResponseFormat%2A> operação, o valor da propriedade será usado.</span><span class="sxs-lookup"><span data-stu-id="13d52-117">If no default format is specified on the operation, the value of the <xref:System.ServiceModel.Description.WebHttpBehavior.DefaultOutgoingResponseFormat%2A> property is used.</span></span> <span data-ttu-id="13d52-118">A formatação automática <xref:System.ServiceModel.Description.WebHttpBehavior.AutomaticFormatSelectionEnabled%2A> depende da propriedade.</span><span class="sxs-lookup"><span data-stu-id="13d52-118">Automatic formatting relies on the <xref:System.ServiceModel.Description.WebHttpBehavior.AutomaticFormatSelectionEnabled%2A> property.</span></span> <span data-ttu-id="13d52-119">Quando esta propriedade `true`é definida como , a infra-estrutura WCF determina o melhor formato a ser usado.</span><span class="sxs-lookup"><span data-stu-id="13d52-119">When this property is set to `true`, the WCF infrastructure determines the best format to use.</span></span> <span data-ttu-id="13d52-120">A seleção automática do formato é desativada por padrão para retrocompatibilidade.</span><span class="sxs-lookup"><span data-stu-id="13d52-120">Automatic format selection is disabled by default for backwards compatibility.</span></span> <span data-ttu-id="13d52-121">A seleção automática do formato pode ser ativada de forma programática ou através da configuração.</span><span class="sxs-lookup"><span data-stu-id="13d52-121">Automatic format selection can be enabled programmatically or through configuration.</span></span> <span data-ttu-id="13d52-122">O exemplo a seguir mostra como ativar a seleção automática de formato em código.</span><span class="sxs-lookup"><span data-stu-id="13d52-122">The following example shows how to enable automatic format selection in code.</span></span>  
  
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
  
 <span data-ttu-id="13d52-123">A formatação automática também pode ser ativada através da configuração.</span><span class="sxs-lookup"><span data-stu-id="13d52-123">Automatic formatting can also be enabled through configuration.</span></span> <span data-ttu-id="13d52-124">Você pode <xref:System.ServiceModel.Description.WebHttpBehavior.AutomaticFormatSelectionEnabled%2A> definir a <xref:System.ServiceModel.Description.WebHttpBehavior> propriedade diretamente <xref:System.ServiceModel.Description.WebHttpEndpoint>no ou usando o .</span><span class="sxs-lookup"><span data-stu-id="13d52-124">You can set the <xref:System.ServiceModel.Description.WebHttpBehavior.AutomaticFormatSelectionEnabled%2A> property directly on the <xref:System.ServiceModel.Description.WebHttpBehavior> or using the <xref:System.ServiceModel.Description.WebHttpEndpoint>.</span></span> <span data-ttu-id="13d52-125">O exemplo a seguir mostra como ativar <xref:System.ServiceModel.Description.WebHttpBehavior>a seleção automática de formato no .</span><span class="sxs-lookup"><span data-stu-id="13d52-125">The following example shows how to enable the automatic format selection on the <xref:System.ServiceModel.Description.WebHttpBehavior>.</span></span>  
  
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
  
 <span data-ttu-id="13d52-126">O exemplo a seguir mostra como <xref:System.ServiceModel.Description.WebHttpEndpoint>ativar a seleção automática de formatos usando .</span><span class="sxs-lookup"><span data-stu-id="13d52-126">The following example shows how to enable automatic format selection using <xref:System.ServiceModel.Description.WebHttpEndpoint>.</span></span>  
  
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
  
## <a name="explicit-formatting"></a><span data-ttu-id="13d52-127">Formatação explícita</span><span class="sxs-lookup"><span data-stu-id="13d52-127">Explicit formatting</span></span>  
 <span data-ttu-id="13d52-128">Como o nome indica, na formatação explícita o desenvolvedor determina o melhor formato a ser usado dentro do código de operação.</span><span class="sxs-lookup"><span data-stu-id="13d52-128">As the name implies, in explicit formatting the developer determines the best format to use within the operation code.</span></span> <span data-ttu-id="13d52-129">Se o melhor formato for XML ou <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A> JSON, o desenvolvedor definirá para ou <xref:System.ServiceModel.Web.WebMessageFormat.Xml> . <xref:System.ServiceModel.Web.WebMessageFormat.Json></span><span class="sxs-lookup"><span data-stu-id="13d52-129">If the best format is XML or JSON the developer sets <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A> to either <xref:System.ServiceModel.Web.WebMessageFormat.Xml> or <xref:System.ServiceModel.Web.WebMessageFormat.Json>.</span></span> <span data-ttu-id="13d52-130">Se <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A> a propriedade não estiver explicitamente definida, o formato padrão da operação será usado.</span><span class="sxs-lookup"><span data-stu-id="13d52-130">If the <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A> property is not explicitly set, then the operation’s default format is used.</span></span>  
  
 <span data-ttu-id="13d52-131">O exemplo a seguir verifica o parâmetro de seqüência de string de consulta de formato para um formato a ser usado.</span><span class="sxs-lookup"><span data-stu-id="13d52-131">The following example checks the format query string parameter for a format to use.</span></span> <span data-ttu-id="13d52-132">Se tiver sido especificado, ele define o <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A>formato da operação usando .</span><span class="sxs-lookup"><span data-stu-id="13d52-132">If it has been specified, it sets the operation’s format using <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A>.</span></span>  
  
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
  
 <span data-ttu-id="13d52-133">Se você precisar de suporte a formatos diferentes de XML ou <xref:System.ServiceModel.Channels.Message>JSON, defina sua operação para ter um tipo de retorno de .</span><span class="sxs-lookup"><span data-stu-id="13d52-133">If you need to support formats other than XML or JSON, define your operation to have a return type of <xref:System.ServiceModel.Channels.Message>.</span></span> <span data-ttu-id="13d52-134">Dentro do código de operação, determine o <xref:System.ServiceModel.Channels.Message> formato apropriado para usar e, em seguida, crie um objeto usando um dos seguintes métodos:</span><span class="sxs-lookup"><span data-stu-id="13d52-134">Within the operation code, determine the appropriate format to use and then create a <xref:System.ServiceModel.Channels.Message> object using one of the following methods:</span></span>  
  
- `WebOperationContext.CreateAtom10Response`  
  
- `WebOperationContext.CreateJsonResponse`  
  
- `WebOperationContext.CreateStreamResponse`  
  
- `WebOperationContext.CreateTextResponse`  
  
- `WebOperationContext.CreateXmlResponse`  
  
 <span data-ttu-id="13d52-135">Cada um desses métodos pega conteúdo e cria uma mensagem com o formato apropriado.</span><span class="sxs-lookup"><span data-stu-id="13d52-135">Each of these methods takes content and creates a message with the appropriate format.</span></span> <span data-ttu-id="13d52-136">O `WebOperationContext.Current.IncomingRequest.GetAcceptHeaderElements` método pode ser usado para obter uma lista de formatos preferidos pelo cliente, a fim de diminuir a preferência.</span><span class="sxs-lookup"><span data-stu-id="13d52-136">The `WebOperationContext.Current.IncomingRequest.GetAcceptHeaderElements` method can be used to get a list of formats preferred by the client in order of decreasing preference.</span></span> <span data-ttu-id="13d52-137">O exemplo a seguir `WebOperationContext.Current.IncomingRequest.GetAcceptHeaderElements` mostra como usar para determinar o formato a ser usado e, em seguida, usa o método de resposta de criação apropriado para criar a mensagem de resposta.</span><span class="sxs-lookup"><span data-stu-id="13d52-137">The following example shows how to use `WebOperationContext.Current.IncomingRequest.GetAcceptHeaderElements` to determine the format to use and then uses the appropriate create response method to create the response message.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="13d52-138">Confira também</span><span class="sxs-lookup"><span data-stu-id="13d52-138">See also</span></span>

- <xref:System.UriTemplate>
- <xref:System.UriTemplateMatch>
- [<span data-ttu-id="13d52-139">Modelo de programação WCF Web HTTP</span><span class="sxs-lookup"><span data-stu-id="13d52-139">WCF Web HTTP Programming Model</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
- [<span data-ttu-id="13d52-140">UriTemplate and UriTemplateTable</span><span class="sxs-lookup"><span data-stu-id="13d52-140">UriTemplate and UriTemplateTable</span></span>](../../../../docs/framework/wcf/feature-details/uritemplate-and-uritemplatetable.md)
- [<span data-ttu-id="13d52-141">Visão geral do modelo de programação HTTP Web do WCF</span><span class="sxs-lookup"><span data-stu-id="13d52-141">WCF Web HTTP Programming Model Overview</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model-overview.md)
- [<span data-ttu-id="13d52-142">Modelo de objeto de programação HTTP Web do WCF</span><span class="sxs-lookup"><span data-stu-id="13d52-142">WCF Web HTTP Programming Object Model</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-object-model.md)
