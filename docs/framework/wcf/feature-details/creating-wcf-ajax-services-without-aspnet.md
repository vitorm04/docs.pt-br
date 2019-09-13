---
title: Criando serviços WCF AJAX sem ASP.NET
ms.date: 03/30/2017
ms.assetid: ba4a7d1b-e277-4978-9f62-37684e6dc934
ms.openlocfilehash: 04d2831407f4aa32c72aabbbff0e6fdde769bd23
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/11/2019
ms.locfileid: "70895094"
---
# <a name="creating-wcf-ajax-services-without-aspnet"></a><span data-ttu-id="4f35d-102">Criando serviços WCF AJAX sem ASP.NET</span><span class="sxs-lookup"><span data-stu-id="4f35d-102">Creating WCF AJAX Services without ASP.NET</span></span>
<span data-ttu-id="4f35d-103">Os serviços do Windows Communication Foundation (WCF) AJAX podem ser acessados em qualquer página da Web habilitada para JavaScript, sem a necessidade do AJAX ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="4f35d-103">Windows Communication Foundation (WCF) AJAX services can be accessed from any JavaScript-enabled Web page, without requiring ASP.NET AJAX.</span></span> <span data-ttu-id="4f35d-104">Este tópico descreve como criar um serviço WCF desse tipo.</span><span class="sxs-lookup"><span data-stu-id="4f35d-104">This topic describes how to create such a WCF service.</span></span>  
  
 <span data-ttu-id="4f35d-105">Para obter instruções sobre como usar o WCF com o ASP.NET AJAX, consulte [CREATING WCF Services for ASP.NET AJAX](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md).</span><span class="sxs-lookup"><span data-stu-id="4f35d-105">For instructions on using WCF with ASP.NET AJAX, see [Creating WCF Services for ASP.NET AJAX](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md).</span></span>  
  
 <span data-ttu-id="4f35d-106">Há três partes para criar um serviço WCF AJAX:</span><span class="sxs-lookup"><span data-stu-id="4f35d-106">There are three parts to a creating a WCF AJAX service:</span></span>  
  
- <span data-ttu-id="4f35d-107">Criar um ponto de extremidade AJAX que pode ser acessado no navegador.</span><span class="sxs-lookup"><span data-stu-id="4f35d-107">Creating an AJAX endpoint that can be accessed from the browser.</span></span>  
  
- <span data-ttu-id="4f35d-108">Criando um contrato de serviço compatível com AJAX.</span><span class="sxs-lookup"><span data-stu-id="4f35d-108">Creating an AJAX-compatible service contract.</span></span>  
  
- <span data-ttu-id="4f35d-109">Acessando os serviços WCF AJAX.</span><span class="sxs-lookup"><span data-stu-id="4f35d-109">Accessing WCF AJAX services.</span></span>  
  
## <a name="creating-an-ajax-endpoint"></a><span data-ttu-id="4f35d-110">Criando um ponto de extremidade AJAX</span><span class="sxs-lookup"><span data-stu-id="4f35d-110">Creating an AJAX Endpoint</span></span>  
 <span data-ttu-id="4f35d-111">A maneira mais básica de habilitar o suporte a Ajax em um serviço WCF é usar <xref:System.ServiceModel.Activation.WebServiceHostFactory> o no arquivo. svc associado ao serviço, como no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="4f35d-111">The most basic way to enable AJAX support in a WCF service is to use the <xref:System.ServiceModel.Activation.WebServiceHostFactory> in the .svc file associated with the service, as in the following example.</span></span>  
  
```text
<%ServiceHost   
    language=c#  
    Debug="true"  
    Service="Microsoft.Ajax.Samples.CityService"  
    Factory=System.ServiceModel.Activation.WebServiceHostFactory  
%>  
```  
  
 <span data-ttu-id="4f35d-112">Como alternativa, você também pode usar a configuração para adicionar um ponto de extremidade AJAX.</span><span class="sxs-lookup"><span data-stu-id="4f35d-112">Alternatively, you can also use configuration to add an AJAX endpoint.</span></span> <span data-ttu-id="4f35d-113">Use o <xref:System.ServiceModel.WebHttpBinding> no ponto de extremidade de serviço e configure esse ponto <xref:System.ServiceModel.Description.WebHttpBehavior> de extremidade com o conforme mostrado no trecho de código a seguir.</span><span class="sxs-lookup"><span data-stu-id="4f35d-113">Use the <xref:System.ServiceModel.WebHttpBinding> on the service endpoint and configure that endpoint with the <xref:System.ServiceModel.Description.WebHttpBehavior> as shown in the following code snippet.</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <endpointBehaviors>  
        <behavior name="AjaxBehavior">  
          <webHttp/>  
        </behavior>  
      </endpointBehaviors>  
    </behaviors>  
    <services>  
      <service name="Microsoft.Ajax.Samples.CityService">  
        <endpoint   
          address="ajaxEndpoint"  
          behaviorConfiguration="AjaxBehavior"  
          binding="webHttpBinding"  
          contract="Microsoft.Ajax.Samples.ICityService" />  
      </service>  
    </services>  
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="4f35d-114">Para obter um exemplo funcional, consulte o [serviço AJAX com JSON e XML](../../../../docs/framework/wcf/samples/ajax-service-with-json-and-xml-sample.md).</span><span class="sxs-lookup"><span data-stu-id="4f35d-114">For a working example, see the [AJAX Service with JSON and XML](../../../../docs/framework/wcf/samples/ajax-service-with-json-and-xml-sample.md).</span></span>  
  
## <a name="creating-an-ajax-compatible-service-contract"></a><span data-ttu-id="4f35d-115">Criando um contrato de serviço compatível com AJAX</span><span class="sxs-lookup"><span data-stu-id="4f35d-115">Creating an AJAX-Compatible Service Contract</span></span>  
 <span data-ttu-id="4f35d-116">Por padrão, os contratos de serviço expostos em um ponto de extremidade AJAX retornam dados no formato XML.</span><span class="sxs-lookup"><span data-stu-id="4f35d-116">By default, service contracts exposed over an AJAX endpoint return data in the XML format.</span></span> <span data-ttu-id="4f35d-117">Além disso, por padrão, as operações de serviço são acessíveis por meio de solicitações HTTP POST para URLs que incluem o endereço do ponto de extremidade seguido pelo nome da operação, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="4f35d-117">Also, by default service operations are accessible through HTTP POST requests to URLs that include the endpoint address followed by the operation name, as shown in the following example.</span></span>  
  
```csharp
[OperationContract]  
string[] GetCities(string firstLetters);  
```  
  
 <span data-ttu-id="4f35d-118">Essa operação pode ser acessada usando um `http://serviceaddress/endpointaddress/GetCities` http post para e retornar uma mensagem XML.</span><span class="sxs-lookup"><span data-stu-id="4f35d-118">This operation is accessible using an HTTP POST to `http://serviceaddress/endpointaddress/GetCities` and return an XML message.</span></span>  
  
 <span data-ttu-id="4f35d-119">Você pode usar o modelo de programação da Web completo para personalizar esses aspectos básicos.</span><span class="sxs-lookup"><span data-stu-id="4f35d-119">You can use the full Web Programming Model to customize these basic aspects.</span></span> <span data-ttu-id="4f35d-120">Por exemplo, você pode usar os <xref:System.ServiceModel.Web.WebGetAttribute> atributos <xref:System.ServiceModel.Web.WebInvokeAttribute> ou para controlar o verbo HTTP para o qual a operação responde ou usa `UriTemplate` a propriedade desses respectivos atributos para especificar URIs personalizados.</span><span class="sxs-lookup"><span data-stu-id="4f35d-120">For example, you can use the <xref:System.ServiceModel.Web.WebGetAttribute> or <xref:System.ServiceModel.Web.WebInvokeAttribute> attributes to control the HTTP verb to which the operation responds or use the `UriTemplate` property of these respective attributes to specify custom URIs.</span></span> <span data-ttu-id="4f35d-121">Para obter mais informações, consulte o tópico [modelo de programação Web http do WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md) .</span><span class="sxs-lookup"><span data-stu-id="4f35d-121">For more information, see the [WCF Web HTTP Programming Model](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md) topic.</span></span>  
  
 <span data-ttu-id="4f35d-122">O formato de dados JSON é geralmente usado em serviços AJAX.</span><span class="sxs-lookup"><span data-stu-id="4f35d-122">The JSON data format is often used in AJAX services.</span></span> <span data-ttu-id="4f35d-123">Para criar uma operação que retorne JSON em vez de XML, <xref:System.ServiceModel.Web.WebGetAttribute.ResponseFormat%2A> defina a propriedade <xref:System.ServiceModel.Web.WebInvokeAttribute.ResponseFormat%2A>(ou) <xref:System.ServiceModel.Web.WebMessageFormat.Json>como.</span><span class="sxs-lookup"><span data-stu-id="4f35d-123">To create an operation that returns JSON instead of XML, set the <xref:System.ServiceModel.Web.WebGetAttribute.ResponseFormat%2A> (or the <xref:System.ServiceModel.Web.WebInvokeAttribute.ResponseFormat%2A>) property to <xref:System.ServiceModel.Web.WebMessageFormat.Json>.</span></span> <span data-ttu-id="4f35d-124">O tópico de [SERIALIZAÇÃO JSON](../../../../docs/framework/wcf/feature-details/stand-alone-json-serialization.md) autônoma mostra como os tipos .net internos e os tipos de contrato de dados são mapeados para JSON.</span><span class="sxs-lookup"><span data-stu-id="4f35d-124">The [Stand-Alone JSON Serialization](../../../../docs/framework/wcf/feature-details/stand-alone-json-serialization.md) topic shows how built-in .NET types and data contract types map to JSON.</span></span>  
  
 <span data-ttu-id="4f35d-125">Normalmente, as solicitações e respostas JSON consistem em apenas um item.</span><span class="sxs-lookup"><span data-stu-id="4f35d-125">Normally, JSON requests and responses consist of just one item.</span></span> <span data-ttu-id="4f35d-126">Para a operação `GetCities` anterior, a solicitação é semelhante à instrução a seguir.</span><span class="sxs-lookup"><span data-stu-id="4f35d-126">For the preceding `GetCities` operation, the request resembles the following statement.</span></span>  
  
```json
"na"  
```  
  
 <span data-ttu-id="4f35d-127">A resposta a essa solicitação é semelhante à instrução a seguir.</span><span class="sxs-lookup"><span data-stu-id="4f35d-127">The response to that request resembles the following statement.</span></span>  
  
```json
["Nairobi", "Naples", "Nashville"]  
```  
  
 <span data-ttu-id="4f35d-128">Se a operação usar um parâmetro extra, o estilo da solicitação deverá ser encapsulado para encapsular ambos os parâmetros em um único objeto JSON.</span><span class="sxs-lookup"><span data-stu-id="4f35d-128">If the operation takes an extra parameter, the request style must be wrapped to wrap both parameters in a single JSON object.</span></span> <span data-ttu-id="4f35d-129">Um exemplo dessa mensagem de estilo JSON está no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="4f35d-129">An example of this style JSON message is in the following example.</span></span>  
  
```json  
{"firstLetters": "na", "maxNumber": 2}  
```  
  
 <span data-ttu-id="4f35d-130">O contrato a seguir aceita esta mensagem.</span><span class="sxs-lookup"><span data-stu-id="4f35d-130">The following contract accepts this message.</span></span>  
  
```csharp
[WebInvoke(BodyStyle=WebMessageBodyStyle.WrappedRequest, ResponseFormat=WebMessageFormat.Json)]  
[OperationContract]  
string[] GetCities(string firstLetters, int maxNumber);  
```  
  
## <a name="accessing-ajax-services"></a><span data-ttu-id="4f35d-131">Acessando serviços AJAX</span><span class="sxs-lookup"><span data-stu-id="4f35d-131">Accessing AJAX Services</span></span>  
 <span data-ttu-id="4f35d-132">Os pontos de extremidade do WCF AJAX sempre aceitam solicitações JSON e XML.</span><span class="sxs-lookup"><span data-stu-id="4f35d-132">WCF AJAX endpoints always accept both JSON and XML requests.</span></span>  
  
 <span data-ttu-id="4f35d-133">As solicitações HTTP POST com um tipo de conteúdo de "Application/JSON" são tratadas como JSON, e aquelas com Content-Type que indicam XML (por exemplo, "text/xml") são tratadas como XML.</span><span class="sxs-lookup"><span data-stu-id="4f35d-133">HTTP POST requests with a content-type of "application/json" are treated as JSON, and those with content-type that indicate XML (for example, "text/xml") are treated as XML.</span></span>  
  
 <span data-ttu-id="4f35d-134">As solicitações HTTP GET contêm todos os parâmetros de solicitação na própria URL.</span><span class="sxs-lookup"><span data-stu-id="4f35d-134">HTTP GET requests contain all the request parameters in the URL itself.</span></span>  
  
 <span data-ttu-id="4f35d-135">Cabe ao usuário decidir como criar a solicitação HTTP para o ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="4f35d-135">It is up to the user to decide how to create the HTTP request to the endpoint.</span></span> <span data-ttu-id="4f35d-136">Além disso, o usuário tem controle total sobre a construção do JSON que forma o corpo da solicitação.</span><span class="sxs-lookup"><span data-stu-id="4f35d-136">Also, the user has full control over constructing the JSON that forms the body of the request.</span></span> <span data-ttu-id="4f35d-137">Para obter um exemplo de como criar uma solicitação do JavaScript, consulte o [serviço AJAX com JSON e XML](../../../../docs/framework/wcf/samples/ajax-service-with-json-and-xml-sample.md).</span><span class="sxs-lookup"><span data-stu-id="4f35d-137">For an example of creating a request from JavaScript, see the [AJAX Service with JSON and XML](../../../../docs/framework/wcf/samples/ajax-service-with-json-and-xml-sample.md).</span></span>
