---
title: Criando serviços WCF AJAX sem ASP.NET
ms.date: 03/30/2017
ms.assetid: ba4a7d1b-e277-4978-9f62-37684e6dc934
ms.openlocfilehash: 77a850408c3d952dbd4f682ea704d3248ae17c3e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33490351"
---
# <a name="creating-wcf-ajax-services-without-aspnet"></a><span data-ttu-id="d10d2-102">Criando serviços WCF AJAX sem ASP.NET</span><span class="sxs-lookup"><span data-stu-id="d10d2-102">Creating WCF AJAX Services without ASP.NET</span></span>
<span data-ttu-id="d10d2-103">Os serviços do Windows Communication Foundation (WCF) AJAX podem ser acessados de qualquer página da Web habilitado para JavaScript, sem a necessidade de ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="d10d2-103">Windows Communication Foundation (WCF) AJAX services can be accessed from any JavaScript-enabled Web page, without requiring ASP.NET AJAX.</span></span> <span data-ttu-id="d10d2-104">Este tópico descreve como criar um serviço WCF.</span><span class="sxs-lookup"><span data-stu-id="d10d2-104">This topic describes how to create such a WCF service.</span></span>  
  
 <span data-ttu-id="d10d2-105">Para obter instruções sobre como usar o WCF com o ASP.NET AJAX, consulte [criando serviços WCF para o ASP.NET AJAX](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md).</span><span class="sxs-lookup"><span data-stu-id="d10d2-105">For instructions on using WCF with ASP.NET AJAX, see [Creating WCF Services for ASP.NET AJAX](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md).</span></span>  
  
 <span data-ttu-id="d10d2-106">Há três partes para criar um serviço WCF AJAX:</span><span class="sxs-lookup"><span data-stu-id="d10d2-106">There are three parts to a creating a WCF AJAX service:</span></span>  
  
-   <span data-ttu-id="d10d2-107">Criar um ponto de extremidade AJAX que pode ser acessado do navegador.</span><span class="sxs-lookup"><span data-stu-id="d10d2-107">Creating an AJAX endpoint that can be accessed from the browser.</span></span>  
  
-   <span data-ttu-id="d10d2-108">Criar um contrato de serviço compatível com AJAX.</span><span class="sxs-lookup"><span data-stu-id="d10d2-108">Creating an AJAX-compatible service contract.</span></span>  
  
-   <span data-ttu-id="d10d2-109">Acessando serviços WCF AJAX.</span><span class="sxs-lookup"><span data-stu-id="d10d2-109">Accessing WCF AJAX services.</span></span>  
  
## <a name="creating-an-ajax-endpoint"></a><span data-ttu-id="d10d2-110">Criar um ponto de extremidade AJAX</span><span class="sxs-lookup"><span data-stu-id="d10d2-110">Creating an AJAX Endpoint</span></span>  
 <span data-ttu-id="d10d2-111">É a maneira mais simples para habilitar o suporte de AJAX em um serviço WCF usar o <xref:System.ServiceModel.Activation.WebServiceHostFactory> no arquivo. svc associado ao serviço, como no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="d10d2-111">The most basic way to enable AJAX support in a WCF service is to use the <xref:System.ServiceModel.Activation.WebServiceHostFactory> in the .svc file associated with the service, as in the following example.</span></span>  
  
```  
<%ServiceHost   
    language=c#  
    Debug="true"  
    Service="Microsoft.Ajax.Samples.CityService"  
    Factory=System.ServiceModel.Activation.WebServiceHostFactory  
%>  
```  
  
 <span data-ttu-id="d10d2-112">Como alternativa, você também pode usar a configuração para adicionar um ponto de extremidade AJAX.</span><span class="sxs-lookup"><span data-stu-id="d10d2-112">Alternatively, you can also use configuration to add an AJAX endpoint.</span></span> <span data-ttu-id="d10d2-113">Use o <xref:System.ServiceModel.WebHttpBinding> no ponto de extremidade de serviço e configurar o ponto de extremidade com o <xref:System.ServiceModel.Description.WebHttpBehavior> conforme mostrado no seguinte trecho de código.</span><span class="sxs-lookup"><span data-stu-id="d10d2-113">Use the <xref:System.ServiceModel.WebHttpBinding> on the service endpoint and configure that endpoint with the <xref:System.ServiceModel.Description.WebHttpBehavior> as shown in the following code snippet.</span></span>  
  
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
  
 <span data-ttu-id="d10d2-114">Para obter um exemplo de funcionamento, consulte o [serviço de AJAX com JSON e XML](../../../../docs/framework/wcf/samples/ajax-service-with-json-and-xml-sample.md).</span><span class="sxs-lookup"><span data-stu-id="d10d2-114">For a working example, see the [AJAX Service with JSON and XML](../../../../docs/framework/wcf/samples/ajax-service-with-json-and-xml-sample.md).</span></span>  
  
## <a name="creating-an-ajax-compatible-service-contract"></a><span data-ttu-id="d10d2-115">Criar um contrato de serviço compatível com o AJAX</span><span class="sxs-lookup"><span data-stu-id="d10d2-115">Creating an AJAX-Compatible Service Contract</span></span>  
 <span data-ttu-id="d10d2-116">Por padrão, os contratos de serviço exposta em dados de retorno um ponto de extremidade AJAX no formato XML.</span><span class="sxs-lookup"><span data-stu-id="d10d2-116">By default, service contracts exposed over an AJAX endpoint return data in the XML format.</span></span> <span data-ttu-id="d10d2-117">Além disso, por padrão, as operações de serviço são acessíveis por meio de solicitações HTTP POST para URLs que incluem o endereço de ponto de extremidade, seguido pelo nome da operação, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="d10d2-117">Also, by default service operations are accessible through HTTP POST requests to URLs that include the endpoint address followed by the operation name, as shown in the following example.</span></span>  
  
```  
[OperationContract]  
string[] GetCities(string firstLetters);  
```  
  
 <span data-ttu-id="d10d2-118">Esta operação é acessível por meio de um HTTP POST para `http://serviceaddress/endpointaddress/GetCities` e retornar uma mensagem XML.</span><span class="sxs-lookup"><span data-stu-id="d10d2-118">This operation is accessible using an HTTP POST to `http://serviceaddress/endpointaddress/GetCities` and return an XML message.</span></span>  
  
 <span data-ttu-id="d10d2-119">Você pode usar o modelo de programação da Web completa para personalizar esses aspectos básicos.</span><span class="sxs-lookup"><span data-stu-id="d10d2-119">You can use the full Web Programming Model to customize these basic aspects.</span></span> <span data-ttu-id="d10d2-120">Por exemplo, você pode usar o <xref:System.ServiceModel.Web.WebGetAttribute> ou <xref:System.ServiceModel.Web.WebInvokeAttribute> atributos para controlar o verbo HTTP para o qual a operação responde ou usar o `UriTemplate` propriedade desses respectivos atributos para especificar os URIs personalizado.</span><span class="sxs-lookup"><span data-stu-id="d10d2-120">For example, you can use the <xref:System.ServiceModel.Web.WebGetAttribute> or <xref:System.ServiceModel.Web.WebInvokeAttribute> attributes to control the HTTP verb to which the operation responds or use the `UriTemplate` property of these respective attributes to specify custom URIs.</span></span> <span data-ttu-id="d10d2-121">Para obter mais informações, consulte o [modelo de programação do WCF Web HTTP](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md) tópico.</span><span class="sxs-lookup"><span data-stu-id="d10d2-121">For more information, see the [WCF Web HTTP Programming Model](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md) topic.</span></span>  
  
 <span data-ttu-id="d10d2-122">O formato de dados JSON é geralmente usado em serviços AJAX.</span><span class="sxs-lookup"><span data-stu-id="d10d2-122">The JSON data format is often used in AJAX services.</span></span> <span data-ttu-id="d10d2-123">Para criar uma operação que retorna JSON em vez de XML, defina o <xref:System.ServiceModel.Web.WebGetAttribute.ResponseFormat%2A> (ou o <xref:System.ServiceModel.Web.WebInvokeAttribute.ResponseFormat%2A>) propriedade <xref:System.ServiceModel.Web.WebMessageFormat.Json>.</span><span class="sxs-lookup"><span data-stu-id="d10d2-123">To create an operation that returns JSON instead of XML, set the <xref:System.ServiceModel.Web.WebGetAttribute.ResponseFormat%2A> (or the <xref:System.ServiceModel.Web.WebInvokeAttribute.ResponseFormat%2A>) property to <xref:System.ServiceModel.Web.WebMessageFormat.Json>.</span></span> <span data-ttu-id="d10d2-124">O [a serialização JSON autônoma](../../../../docs/framework/wcf/feature-details/stand-alone-json-serialization.md) tópico mostra como internos .NET dados e tipos de contrato tipos mapa em JSON.</span><span class="sxs-lookup"><span data-stu-id="d10d2-124">The [Stand-Alone JSON Serialization](../../../../docs/framework/wcf/feature-details/stand-alone-json-serialization.md) topic shows how built-in .NET types and data contract types map to JSON.</span></span>  
  
 <span data-ttu-id="d10d2-125">Normalmente, solicitações JSON e respostas consistem apenas um item.</span><span class="sxs-lookup"><span data-stu-id="d10d2-125">Normally, JSON requests and responses consist of just one item.</span></span> <span data-ttu-id="d10d2-126">Para o anterior `GetCities` operação, a solicitação é semelhante a instrução a seguir.</span><span class="sxs-lookup"><span data-stu-id="d10d2-126">For the preceding `GetCities` operation, the request resembles the following statement.</span></span>  
  
```  
"na"  
```  
  
 <span data-ttu-id="d10d2-127">A resposta para essa solicitação é semelhante a instrução a seguir.</span><span class="sxs-lookup"><span data-stu-id="d10d2-127">The response to that request resembles the following statement.</span></span>  
  
```  
["Nairobi", "Naples", "Nashville"]  
```  
  
 <span data-ttu-id="d10d2-128">Se a operação aceita um parâmetro extra, o estilo de solicitação deve ser encapsulado para encapsular ambos os parâmetros em um único objeto JSON.</span><span class="sxs-lookup"><span data-stu-id="d10d2-128">If the operation takes an extra parameter, the request style must be wrapped to wrap both parameters in a single JSON object.</span></span> <span data-ttu-id="d10d2-129">É um exemplo dessa mensagem de JSON de estilo no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="d10d2-129">An example of this style JSON message is in the following example.</span></span>  
  
```json  
{"firstLetters": "na", "maxNumber": 2}  
```  
  
 <span data-ttu-id="d10d2-130">O contrato a seguir aceita essa mensagem.</span><span class="sxs-lookup"><span data-stu-id="d10d2-130">The following contract accepts this message.</span></span>  
  
```  
[WebInvoke(BodyStyle=WebMessageBodyStyle.WrappedRequest, ResponseFormat=WebMessageFormat.Json)]  
[OperationContract]  
string[] GetCities(string firstLetters, int maxNumber);  
```  
  
## <a name="accessing-ajax-services"></a><span data-ttu-id="d10d2-131">Acessando serviços AJAX</span><span class="sxs-lookup"><span data-stu-id="d10d2-131">Accessing AJAX Services</span></span>  
 <span data-ttu-id="d10d2-132">Pontos de extremidade WCF AJAX sempre aceitam solicitações JSON e XML.</span><span class="sxs-lookup"><span data-stu-id="d10d2-132">WCF AJAX endpoints always accept both JSON and XML requests.</span></span>  
  
 <span data-ttu-id="d10d2-133">Solicitações HTTP POST com um tipo de conteúdo de "application/json" são tratadas como JSON, e aqueles com o tipo de conteúdo que indicam XML (por exemplo, "text/xml") são tratados como XML.</span><span class="sxs-lookup"><span data-stu-id="d10d2-133">HTTP POST requests with a content-type of "application/json" are treated as JSON, and those with content-type that indicate XML (for example, "text/xml") are treated as XML.</span></span>  
  
 <span data-ttu-id="d10d2-134">Solicitações HTTP GET contém todos os parâmetros de solicitação na URL em si.</span><span class="sxs-lookup"><span data-stu-id="d10d2-134">HTTP GET requests contain all the request parameters in the URL itself.</span></span>  
  
 <span data-ttu-id="d10d2-135">Cabe ao usuário decidir como criar a solicitação HTTP para o ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="d10d2-135">It is up to the user to decide how to create the HTTP request to the endpoint.</span></span> <span data-ttu-id="d10d2-136">Além disso, o usuário tem controle total sobre a construção JSON que forma o corpo da solicitação.</span><span class="sxs-lookup"><span data-stu-id="d10d2-136">Also, the user has full control over constructing the JSON that forms the body of the request.</span></span> <span data-ttu-id="d10d2-137">Para obter um exemplo de criação de uma solicitação de JavaScript, consulte o [serviço de AJAX com JSON e XML](../../../../docs/framework/wcf/samples/ajax-service-with-json-and-xml-sample.md).</span><span class="sxs-lookup"><span data-stu-id="d10d2-137">For an example of creating a request from JavaScript, see the [AJAX Service with JSON and XML](../../../../docs/framework/wcf/samples/ajax-service-with-json-and-xml-sample.md).</span></span>
