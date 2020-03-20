---
title: Criando serviços WCF AJAX sem ASP.NET
ms.date: 03/30/2017
ms.assetid: ba4a7d1b-e277-4978-9f62-37684e6dc934
ms.openlocfilehash: f4d1d093132c501844aacbaa9cf28ecc3cede442
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185236"
---
# <a name="creating-wcf-ajax-services-without-aspnet"></a><span data-ttu-id="b2d75-102">Criando serviços WCF AJAX sem ASP.NET</span><span class="sxs-lookup"><span data-stu-id="b2d75-102">Creating WCF AJAX Services without ASP.NET</span></span>
<span data-ttu-id="b2d75-103">Os serviços AJAX da Windows Communication Foundation (WCF) podem ser acessados a partir de qualquer página da Web habilitada para JavaScript, sem precisar ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="b2d75-103">Windows Communication Foundation (WCF) AJAX services can be accessed from any JavaScript-enabled Web page, without requiring ASP.NET AJAX.</span></span> <span data-ttu-id="b2d75-104">Este tópico descreve como criar tal serviço WCF.</span><span class="sxs-lookup"><span data-stu-id="b2d75-104">This topic describes how to create such a WCF service.</span></span>  
  
 <span data-ttu-id="b2d75-105">Para obter instruções sobre como usar o WCF com ASP.NET AJAX, consulte [Criando serviços WCF para ASP.NET AJAX](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md).</span><span class="sxs-lookup"><span data-stu-id="b2d75-105">For instructions on using WCF with ASP.NET AJAX, see [Creating WCF Services for ASP.NET AJAX](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md).</span></span>  
  
 <span data-ttu-id="b2d75-106">Existem três partes para criar um serviço WCF AJAX:</span><span class="sxs-lookup"><span data-stu-id="b2d75-106">There are three parts to a creating a WCF AJAX service:</span></span>  
  
- <span data-ttu-id="b2d75-107">Criando um ponto final AJAX que pode ser acessado a partir do navegador.</span><span class="sxs-lookup"><span data-stu-id="b2d75-107">Creating an AJAX endpoint that can be accessed from the browser.</span></span>  
  
- <span data-ttu-id="b2d75-108">Criação de um contrato de serviço compatível com AJAX.</span><span class="sxs-lookup"><span data-stu-id="b2d75-108">Creating an AJAX-compatible service contract.</span></span>  
  
- <span data-ttu-id="b2d75-109">Acessando os serviços WCF AJAX.</span><span class="sxs-lookup"><span data-stu-id="b2d75-109">Accessing WCF AJAX services.</span></span>  
  
## <a name="creating-an-ajax-endpoint"></a><span data-ttu-id="b2d75-110">Criando um ponto final do AJAX</span><span class="sxs-lookup"><span data-stu-id="b2d75-110">Creating an AJAX Endpoint</span></span>  
 <span data-ttu-id="b2d75-111">A maneira mais básica de habilitar o suporte a <xref:System.ServiceModel.Activation.WebServiceHostFactory> AJAX em um serviço WCF é usar o arquivo .svc associado ao serviço, como no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="b2d75-111">The most basic way to enable AJAX support in a WCF service is to use the <xref:System.ServiceModel.Activation.WebServiceHostFactory> in the .svc file associated with the service, as in the following example.</span></span>  
  
```text
<%ServiceHost
    language=c#  
    Debug="true"  
    Service="Microsoft.Ajax.Samples.CityService"  
    Factory=System.ServiceModel.Activation.WebServiceHostFactory  
%>  
```  
  
 <span data-ttu-id="b2d75-112">Alternativamente, você também pode usar a configuração para adicionar um ponto final AJAX.</span><span class="sxs-lookup"><span data-stu-id="b2d75-112">Alternatively, you can also use configuration to add an AJAX endpoint.</span></span> <span data-ttu-id="b2d75-113">Use <xref:System.ServiceModel.WebHttpBinding> o ponto final do serviço e configure esse ponto final com o <xref:System.ServiceModel.Description.WebHttpBehavior> mostrado no trecho de código a seguir.</span><span class="sxs-lookup"><span data-stu-id="b2d75-113">Use the <xref:System.ServiceModel.WebHttpBinding> on the service endpoint and configure that endpoint with the <xref:System.ServiceModel.Description.WebHttpBehavior> as shown in the following code snippet.</span></span>  
  
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
  
 <span data-ttu-id="b2d75-114">Para um exemplo de trabalho, consulte o [Serviço AJAX com JSON e XML](../../../../docs/framework/wcf/samples/ajax-service-with-json-and-xml-sample.md).</span><span class="sxs-lookup"><span data-stu-id="b2d75-114">For a working example, see the [AJAX Service with JSON and XML](../../../../docs/framework/wcf/samples/ajax-service-with-json-and-xml-sample.md).</span></span>  
  
## <a name="creating-an-ajax-compatible-service-contract"></a><span data-ttu-id="b2d75-115">Criando um contrato de serviço compatível com AJAX</span><span class="sxs-lookup"><span data-stu-id="b2d75-115">Creating an AJAX-Compatible Service Contract</span></span>  
 <span data-ttu-id="b2d75-116">Por padrão, os contratos de serviço expostos sobre os dados de retorno de ponto final do AJAX no formato XML.</span><span class="sxs-lookup"><span data-stu-id="b2d75-116">By default, service contracts exposed over an AJAX endpoint return data in the XML format.</span></span> <span data-ttu-id="b2d75-117">Além disso, as operações de serviço padrão são acessíveis através de solicitações HTTP POST para URLs que incluem o endereço de ponto final seguido pelo nome da operação, como mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="b2d75-117">Also, by default service operations are accessible through HTTP POST requests to URLs that include the endpoint address followed by the operation name, as shown in the following example.</span></span>  
  
```csharp
[OperationContract]  
string[] GetCities(string firstLetters);  
```  
  
 <span data-ttu-id="b2d75-118">Esta operação é acessível `http://serviceaddress/endpointaddress/GetCities` usando um POST HTTP para e retornar uma mensagem XML.</span><span class="sxs-lookup"><span data-stu-id="b2d75-118">This operation is accessible using an HTTP POST to `http://serviceaddress/endpointaddress/GetCities` and return an XML message.</span></span>  
  
 <span data-ttu-id="b2d75-119">Você pode usar o modelo completo de programação da Web para personalizar esses aspectos básicos.</span><span class="sxs-lookup"><span data-stu-id="b2d75-119">You can use the full Web Programming Model to customize these basic aspects.</span></span> <span data-ttu-id="b2d75-120">Por exemplo, você <xref:System.ServiceModel.Web.WebGetAttribute> pode <xref:System.ServiceModel.Web.WebInvokeAttribute> usar o ou atributos para controlar o `UriTemplate` verbo HTTP ao qual a operação responde ou usar a propriedade desses respectivos atributos para especificar URIs personalizados.</span><span class="sxs-lookup"><span data-stu-id="b2d75-120">For example, you can use the <xref:System.ServiceModel.Web.WebGetAttribute> or <xref:System.ServiceModel.Web.WebInvokeAttribute> attributes to control the HTTP verb to which the operation responds or use the `UriTemplate` property of these respective attributes to specify custom URIs.</span></span> <span data-ttu-id="b2d75-121">Para obter mais informações, consulte o tópico [WCF Web HTTP Programming Model.](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)</span><span class="sxs-lookup"><span data-stu-id="b2d75-121">For more information, see the [WCF Web HTTP Programming Model](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md) topic.</span></span>  
  
 <span data-ttu-id="b2d75-122">O formato de dados JSON é frequentemente usado em serviços AJAX.</span><span class="sxs-lookup"><span data-stu-id="b2d75-122">The JSON data format is often used in AJAX services.</span></span> <span data-ttu-id="b2d75-123">Para criar uma operação que devolva json em vez de XML, defina a <xref:System.ServiceModel.Web.WebGetAttribute.ResponseFormat%2A> propriedade (ou a) <xref:System.ServiceModel.Web.WebInvokeAttribute.ResponseFormat%2A>para <xref:System.ServiceModel.Web.WebMessageFormat.Json>.</span><span class="sxs-lookup"><span data-stu-id="b2d75-123">To create an operation that returns JSON instead of XML, set the <xref:System.ServiceModel.Web.WebGetAttribute.ResponseFormat%2A> (or the <xref:System.ServiceModel.Web.WebInvokeAttribute.ResponseFormat%2A>) property to <xref:System.ServiceModel.Web.WebMessageFormat.Json>.</span></span> <span data-ttu-id="b2d75-124">O [tópico De serialização JSON autônomo](../../../../docs/framework/wcf/feature-details/stand-alone-json-serialization.md) mostra como os tipos de .NET incorporados e os tipos de contrato de dados mapeiam para JSON.</span><span class="sxs-lookup"><span data-stu-id="b2d75-124">The [Stand-Alone JSON Serialization](../../../../docs/framework/wcf/feature-details/stand-alone-json-serialization.md) topic shows how built-in .NET types and data contract types map to JSON.</span></span>  
  
 <span data-ttu-id="b2d75-125">Normalmente, as solicitações e respostas do JSON consistem em apenas um item.</span><span class="sxs-lookup"><span data-stu-id="b2d75-125">Normally, JSON requests and responses consist of just one item.</span></span> <span data-ttu-id="b2d75-126">Para a `GetCities` operação anterior, a solicitação se assemelha à seguinte declaração.</span><span class="sxs-lookup"><span data-stu-id="b2d75-126">For the preceding `GetCities` operation, the request resembles the following statement.</span></span>  
  
```json
"na"  
```  
  
 <span data-ttu-id="b2d75-127">A resposta a esse pedido se assemelha à seguinte declaração.</span><span class="sxs-lookup"><span data-stu-id="b2d75-127">The response to that request resembles the following statement.</span></span>  
  
```json
["Nairobi", "Naples", "Nashville"]  
```  
  
 <span data-ttu-id="b2d75-128">Se a operação tomar um parâmetro extra, o estilo de solicitação deve ser embrulhado para envolver ambos os parâmetros em um único objeto JSON.</span><span class="sxs-lookup"><span data-stu-id="b2d75-128">If the operation takes an extra parameter, the request style must be wrapped to wrap both parameters in a single JSON object.</span></span> <span data-ttu-id="b2d75-129">Um exemplo dessa mensagem JSON de estilo está no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="b2d75-129">An example of this style JSON message is in the following example.</span></span>  
  
```json  
{"firstLetters": "na", "maxNumber": 2}  
```  
  
 <span data-ttu-id="b2d75-130">O contrato a seguir aceita esta mensagem.</span><span class="sxs-lookup"><span data-stu-id="b2d75-130">The following contract accepts this message.</span></span>  
  
```csharp
[WebInvoke(BodyStyle=WebMessageBodyStyle.WrappedRequest, ResponseFormat=WebMessageFormat.Json)]  
[OperationContract]  
string[] GetCities(string firstLetters, int maxNumber);  
```  
  
## <a name="accessing-ajax-services"></a><span data-ttu-id="b2d75-131">Acessando os serviços AJAX</span><span class="sxs-lookup"><span data-stu-id="b2d75-131">Accessing AJAX Services</span></span>  
 <span data-ttu-id="b2d75-132">Os pontos finais do WCF AJAX sempre aceitam solicitações JSON e XML.</span><span class="sxs-lookup"><span data-stu-id="b2d75-132">WCF AJAX endpoints always accept both JSON and XML requests.</span></span>  
  
 <span data-ttu-id="b2d75-133">As solicitações HTTP POST com um tipo de conteúdo de "application/json" são tratadas como JSON, e aquelas com tipo de conteúdo que indicam XML (por exemplo, "text/xml") são tratadas como XML.</span><span class="sxs-lookup"><span data-stu-id="b2d75-133">HTTP POST requests with a content-type of "application/json" are treated as JSON, and those with content-type that indicate XML (for example, "text/xml") are treated as XML.</span></span>  
  
 <span data-ttu-id="b2d75-134">As solicitações HTTP GET contêm todos os parâmetros de solicitação na própria URL.</span><span class="sxs-lookup"><span data-stu-id="b2d75-134">HTTP GET requests contain all the request parameters in the URL itself.</span></span>  
  
 <span data-ttu-id="b2d75-135">Cabe ao usuário decidir como criar a solicitação HTTP até o ponto final.</span><span class="sxs-lookup"><span data-stu-id="b2d75-135">It is up to the user to decide how to create the HTTP request to the endpoint.</span></span> <span data-ttu-id="b2d75-136">Além disso, o usuário tem total controle sobre a construção do JSON que forma o corpo da solicitação.</span><span class="sxs-lookup"><span data-stu-id="b2d75-136">Also, the user has full control over constructing the JSON that forms the body of the request.</span></span> <span data-ttu-id="b2d75-137">Para um exemplo de criação de uma solicitação do JavaScript, consulte o [Serviço AJAX com JSON e XML](../../../../docs/framework/wcf/samples/ajax-service-with-json-and-xml-sample.md).</span><span class="sxs-lookup"><span data-stu-id="b2d75-137">For an example of creating a request from JavaScript, see the [AJAX Service with JSON and XML](../../../../docs/framework/wcf/samples/ajax-service-with-json-and-xml-sample.md).</span></span>
