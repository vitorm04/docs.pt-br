---
title: Serviço de AJAX com exemplo de JSON e XML
ms.date: 03/30/2017
ms.assetid: 8ea5860d-0c42-4ae9-941a-e07efdd8e29c
ms.openlocfilehash: a93e7bdf8cda88a1e86b59e5c3d37f049bdfcf28
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62002827"
---
# <a name="ajax-service-with-json-and-xml-sample"></a><span data-ttu-id="01bd6-102">Serviço de AJAX com exemplo de JSON e XML</span><span class="sxs-lookup"><span data-stu-id="01bd6-102">AJAX Service with JSON and XML Sample</span></span>
<span data-ttu-id="01bd6-103">Este exemplo demonstra como usar o Windows Communication Foundation (WCF) para criar um serviço de Asynchronous JavaScript and XML (AJAX) que retorna dados de objeto notação JSON (JavaScript) ou XML.</span><span class="sxs-lookup"><span data-stu-id="01bd6-103">This sample demonstrates how to use Windows Communication Foundation (WCF) to create an Asynchronous JavaScript and XML (AJAX) service that returns either JavaScript Object Notation (JSON) or XML data.</span></span> <span data-ttu-id="01bd6-104">Você pode acessar um serviço AJAX usando código JavaScript de um cliente de navegador da Web.</span><span class="sxs-lookup"><span data-stu-id="01bd6-104">You can access an AJAX service by using JavaScript code from a Web browser client.</span></span> <span data-ttu-id="01bd6-105">Este exemplo se baseia a [serviço de AJAX básico](../../../../docs/framework/wcf/samples/basic-ajax-service.md) exemplo.</span><span class="sxs-lookup"><span data-stu-id="01bd6-105">This sample builds on the [Basic AJAX Service](../../../../docs/framework/wcf/samples/basic-ajax-service.md) sample.</span></span>  
  
 <span data-ttu-id="01bd6-106">Ao contrário de outros exemplos de AJAX, este exemplo usa o ASP.NET AJAX e o <xref:System.Web.UI.ScriptManager> controle.</span><span class="sxs-lookup"><span data-stu-id="01bd6-106">Unlike the other AJAX samples, this sample does not use ASP.NET AJAX and the <xref:System.Web.UI.ScriptManager> control.</span></span> <span data-ttu-id="01bd6-107">Com alguma configuração adicional, os serviços WCF AJAX podem ser acessados de qualquer página HTML por meio de JavaScript e este cenário é mostrado aqui.</span><span class="sxs-lookup"><span data-stu-id="01bd6-107">With some additional configuration, WCF AJAX services can be accessed from any HTML page through JavaScript, and this scenario is shown here.</span></span> <span data-ttu-id="01bd6-108">Para obter um exemplo de como usar o WCF com o ASP.NET AJAX, consulte [amostras do AJAX](ajax.md).</span><span class="sxs-lookup"><span data-stu-id="01bd6-108">For an example of using WCF with ASP.NET AJAX, see [AJAX Samples](ajax.md).</span></span>
  
 <span data-ttu-id="01bd6-109">Este exemplo mostra como alternar o tipo de resposta de uma operação entre JSON e XML.</span><span class="sxs-lookup"><span data-stu-id="01bd6-109">This sample shows how to switch the response type of an operation between JSON and XML.</span></span> <span data-ttu-id="01bd6-110">Essa funcionalidade está disponível independentemente do serviço é configurado para ser acessado por ASP.NET AJAX ou por uma página de cliente HTML/JavaScript.</span><span class="sxs-lookup"><span data-stu-id="01bd6-110">This functionality is available regardless of whether the service is configured to be accessed by ASP.NET AJAX or by an HTML/JavaScript client page.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="01bd6-111">As instruções de procedimento e compilação de configuração para este exemplo estão localizadas no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="01bd6-111">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>
  
<span data-ttu-id="01bd6-112">Para habilitar o uso de clientes do ASP.NET AJAX, use <xref:System.ServiceModel.Activation.WebServiceHostFactory> (não <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>) no arquivo. svc.</span><span class="sxs-lookup"><span data-stu-id="01bd6-112">To enable the use of non-ASP.NET AJAX clients, use <xref:System.ServiceModel.Activation.WebServiceHostFactory> (not <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>) in the .svc file.</span></span> <span data-ttu-id="01bd6-113"><xref:System.ServiceModel.Activation.WebServiceHostFactory> Adiciona um <xref:System.ServiceModel.Description.WebHttpEndpoint> ponto de extremidade padrão para o serviço.</span><span class="sxs-lookup"><span data-stu-id="01bd6-113"><xref:System.ServiceModel.Activation.WebServiceHostFactory> adds a <xref:System.ServiceModel.Description.WebHttpEndpoint> standard endpoint to the service.</span></span> <span data-ttu-id="01bd6-114">O ponto de extremidade é configurado em um endereço relativo ao arquivo. svc; em branco Isso significa que o endereço do serviço é `http://localhost/ServiceModelSamples/service.svc`, com nenhum sufixos adicionais que não seja o nome da operação.</span><span class="sxs-lookup"><span data-stu-id="01bd6-114">The endpoint is configured at an empty address relative to the .svc file; this means that the address of the service is `http://localhost/ServiceModelSamples/service.svc`, with no additional suffixes other than the operation name.</span></span>  
  
```svc
<%@ServiceHost language="c#" Debug="true" Service="Microsoft.Samples.XmlAjaxService.CalculatorService" Factory="System.ServiceModel.Activation.WebServiceHostFactory" %>  
```  
  
 <span data-ttu-id="01bd6-115">A seção a seguir no Web. config pode ser usada para fazer alterações de configuração adicionais para o ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="01bd6-115">The following section in Web.config can be used to make additional configuration changes to the endpoint.</span></span> <span data-ttu-id="01bd6-116">Ele pode ser removido se nenhuma alteração adicional é necessária.</span><span class="sxs-lookup"><span data-stu-id="01bd6-116">It can be removed if no extra changes are needed.</span></span>  
  
```xml  
<system.serviceModel>  
  <standardEndpoints>  
    <webHttpEndpoint>  
      <!-- Use this element to configure the endpoint -->  
      <standardEndpoint name="" />  
    </webHttpEndpoint>  
  </standardEndpoints>  
</system.serviceModel>  
```  
  
 <span data-ttu-id="01bd6-117">Os dados padrão de formato para <xref:System.ServiceModel.Description.WebHttpEndpoint> é XML, enquanto o formato de dados padrão para <xref:System.ServiceModel.Description.WebScriptEndpoint> é JSON.</span><span class="sxs-lookup"><span data-stu-id="01bd6-117">The default data format for <xref:System.ServiceModel.Description.WebHttpEndpoint> is XML, while the default data format for <xref:System.ServiceModel.Description.WebScriptEndpoint> is JSON.</span></span> <span data-ttu-id="01bd6-118">Para obter mais informações, consulte [criação de serviços do WCF AJAX sem ASP.NET](../../../../docs/framework/wcf/feature-details/creating-wcf-ajax-services-without-aspnet.md).</span><span class="sxs-lookup"><span data-stu-id="01bd6-118">For more information, see [Creating WCF AJAX Services without ASP.NET](../../../../docs/framework/wcf/feature-details/creating-wcf-ajax-services-without-aspnet.md).</span></span>  
  
 <span data-ttu-id="01bd6-119">O serviço no exemplo a seguir é um serviço WCF padrão com duas operações.</span><span class="sxs-lookup"><span data-stu-id="01bd6-119">The service in the following sample is a standard WCF service with two operations.</span></span> <span data-ttu-id="01bd6-120">As duas operações requerem o <xref:System.ServiceModel.Web.WebMessageBodyStyle.Wrapped> estilo de corpo de <xref:System.ServiceModel.Web.WebGetAttribute> ou <xref:System.ServiceModel.Web.WebInvokeAttribute> atributos, que é específico para o `webHttp` comportamento e não tem influência sobre a opção de formato de dados JSON/XML.</span><span class="sxs-lookup"><span data-stu-id="01bd6-120">Both operations require the <xref:System.ServiceModel.Web.WebMessageBodyStyle.Wrapped> body style on the <xref:System.ServiceModel.Web.WebGetAttribute> or <xref:System.ServiceModel.Web.WebInvokeAttribute> attributes, which is specific to the `webHttp` behavior and has no bearing on the JSON/XML data format switch.</span></span>  

```csharp
[OperationContract]  
[WebInvoke(ResponseFormat = WebMessageFormat.Xml, BodyStyle = WebMessageBodyStyle.Wrapped)]  
MathResult DoMathXml(double n1, double n2);  
```

 <span data-ttu-id="01bd6-121">O formato de resposta para a operação é especificado como XML, que é o padrão Configurando para o [ \<webHttp >](../../../../docs/framework/configure-apps/file-schema/wcf/webhttp.md) comportamento.</span><span class="sxs-lookup"><span data-stu-id="01bd6-121">The response format for the operation is specified as XML, which is the default setting for the [\<webHttp>](../../../../docs/framework/configure-apps/file-schema/wcf/webhttp.md) behavior.</span></span> <span data-ttu-id="01bd6-122">No entanto, é recomendável explicitamente especificar o formato da resposta.</span><span class="sxs-lookup"><span data-stu-id="01bd6-122">However, it is good practice explicitly specify the response format.</span></span>  
  
 <span data-ttu-id="01bd6-123">Outra operação usa o `WebInvokeAttribute` de atributos e especifica explicitamente o JSON em vez de XML para a resposta.</span><span class="sxs-lookup"><span data-stu-id="01bd6-123">The other operation uses the `WebInvokeAttribute` attribute and explicitly specifies JSON instead of XML for the response.</span></span>  

```csharp
[OperationContract]  
[WebInvoke(ResponseFormat = WebMessageFormat.Json, BodyStyle = WebMessageBodyStyle.Wrapped)]  
MathResult DoMathJson(double n1, double n2);  
```

 <span data-ttu-id="01bd6-124">Observe que, em ambos os casos, as operações retornam um tipo complexo, `MathResult`, que é um tipo de contrato de dados padrão do WCF.</span><span class="sxs-lookup"><span data-stu-id="01bd6-124">Note that in both cases the operations return a complex type, `MathResult`, which is a standard WCF data contract type.</span></span>  
  
 <span data-ttu-id="01bd6-125">O cliente XmlAjaxClientPage.htm de página da Web contém código JavaScript que invoca uma das duas operações anteriores quando o usuário clica o **executar o cálculo de (retorno JSON)** ou **executar cálculo (retorno XML)**  botões na página.</span><span class="sxs-lookup"><span data-stu-id="01bd6-125">The client Web page XmlAjaxClientPage.htm contains JavaScript code that invokes one of the preceding two operations when the user clicks the **Perform calculation (return JSON)** or **Perform calculation (return XML)** buttons on the page.</span></span> <span data-ttu-id="01bd6-126">O código para invocar o serviço constrói um corpo JSON e envia-o usando HTTP POST.</span><span class="sxs-lookup"><span data-stu-id="01bd6-126">The code to invoke the service constructs a JSON body and sends it using HTTP POST.</span></span> <span data-ttu-id="01bd6-127">A solicitação é criada manualmente em JavaScript, ao contrário do [serviço básico do AJAX](../../../../docs/framework/wcf/samples/basic-ajax-service.md) exemplo e outros exemplos usando o ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="01bd6-127">The request is created manually in JavaScript, unlike the [Basic AJAX Service](../../../../docs/framework/wcf/samples/basic-ajax-service.md) sample and the other samples using ASP.NET AJAX.</span></span>  

```csharp
// Create HTTP request  
var xmlHttp;  
// Request instantiation code omitted…  
// Result handler code omitted…  
  
// Build the operation URL  
var url = "service.svc/ajaxEndpoint/";  
url = url + operation;  
  
// Build the body of the JSON message  
var body = '{"n1":';  
body = body + document.getElementById("num1").value + ',"n2":';  
body = body + document.getElementById("num2").value + '}';  
  
// Send the HTTP request  
xmlHttp.open("POST", url, true);  
xmlHttp.setRequestHeader("Content-type", "application/json");  
xmlHttp.send(body);  
```

 <span data-ttu-id="01bd6-128">Quando o serviço responde, a resposta é exibida sem nenhum processamento adicional em uma caixa de texto na página.</span><span class="sxs-lookup"><span data-stu-id="01bd6-128">When the service responds, the response is displayed without any further processing in a textbox on the page.</span></span> <span data-ttu-id="01bd6-129">Isso é implementado para fins de demonstração para que você possa observar diretamente os formatos de dados XML e JSON usados.</span><span class="sxs-lookup"><span data-stu-id="01bd6-129">This is implemented for demonstration purposes to allow you to directly observe the XML and JSON data formats used.</span></span>  

```javascript
// Create result handler   
xmlHttp.onreadystatechange=function(){  
     if(xmlHttp.readyState == 4){  
          document.getElementById("result").value = xmlHttp.responseText;  
     }  
}  
```

> [!IMPORTANT]
>  <span data-ttu-id="01bd6-130">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="01bd6-130">The samples may already be installed on your machine.</span></span> <span data-ttu-id="01bd6-131">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="01bd6-131">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="01bd6-132">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="01bd6-132">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="01bd6-133">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="01bd6-133">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\AJAX\XmlAjaxService`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="01bd6-134">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="01bd6-134">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="01bd6-135">Certifique-se de que você tenha executado o [procedimento de configuração de uso único para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="01bd6-135">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="01bd6-136">Compile a solução XmlAjaxService.sln, conforme descrito em [compilando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="01bd6-136">Build the solution XmlAjaxService.sln as described in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="01bd6-137">Navegue até `http://localhost/ServiceModelSamples/XmlAjaxClientPage.htm` (não abrir XmlAjaxClientPage.htm no navegador do diretório do projeto).</span><span class="sxs-lookup"><span data-stu-id="01bd6-137">Navigate to `http://localhost/ServiceModelSamples/XmlAjaxClientPage.htm` (do not open XmlAjaxClientPage.htm in the browser from the project directory).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01bd6-138">Consulte também</span><span class="sxs-lookup"><span data-stu-id="01bd6-138">See also</span></span>

- [<span data-ttu-id="01bd6-139">Serviço AJAX utilizando HTTP POST</span><span class="sxs-lookup"><span data-stu-id="01bd6-139">AJAX Service Using HTTP POST</span></span>](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md)
