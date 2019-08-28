---
title: Serviço de AJAX com exemplo de JSON e XML
ms.date: 03/30/2017
ms.assetid: 8ea5860d-0c42-4ae9-941a-e07efdd8e29c
ms.openlocfilehash: 62c573a844ce5382308814342330f778fa041a69
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70045200"
---
# <a name="ajax-service-with-json-and-xml-sample"></a><span data-ttu-id="f66c2-102">Serviço de AJAX com exemplo de JSON e XML</span><span class="sxs-lookup"><span data-stu-id="f66c2-102">AJAX Service with JSON and XML Sample</span></span>

<span data-ttu-id="f66c2-103">Este exemplo demonstra como usar o Windows Communication Foundation (WCF) para criar um serviço de JavaScript e XML (AJAX) assíncrono que retorna dados de JavaScript Object Notation (JSON) ou XML.</span><span class="sxs-lookup"><span data-stu-id="f66c2-103">This sample demonstrates how to use Windows Communication Foundation (WCF) to create an Asynchronous JavaScript and XML (AJAX) service that returns either JavaScript Object Notation (JSON) or XML data.</span></span> <span data-ttu-id="f66c2-104">Você pode acessar um serviço AJAX usando o código JavaScript de um cliente de navegador da Web.</span><span class="sxs-lookup"><span data-stu-id="f66c2-104">You can access an AJAX service by using JavaScript code from a Web browser client.</span></span> <span data-ttu-id="f66c2-105">Este exemplo baseia-se no exemplo de [serviço básico Ajax](../../../../docs/framework/wcf/samples/basic-ajax-service.md) .</span><span class="sxs-lookup"><span data-stu-id="f66c2-105">This sample builds on the [Basic AJAX Service](../../../../docs/framework/wcf/samples/basic-ajax-service.md) sample.</span></span>

<span data-ttu-id="f66c2-106">Ao contrário dos outros exemplos do Ajax, este exemplo não usa o ASP.NET AJAX <xref:System.Web.UI.ScriptManager> e o controle.</span><span class="sxs-lookup"><span data-stu-id="f66c2-106">Unlike the other AJAX samples, this sample does not use ASP.NET AJAX and the <xref:System.Web.UI.ScriptManager> control.</span></span> <span data-ttu-id="f66c2-107">Com algumas configurações adicionais, os serviços WCF AJAX podem ser acessados de qualquer página HTML por meio de JavaScript, e esse cenário é mostrado aqui.</span><span class="sxs-lookup"><span data-stu-id="f66c2-107">With some additional configuration, WCF AJAX services can be accessed from any HTML page through JavaScript, and this scenario is shown here.</span></span> <span data-ttu-id="f66c2-108">Para obter um exemplo de como usar o WCF com o ASP.NET AJAX, consulte [exemplos de AJAX](ajax.md).</span><span class="sxs-lookup"><span data-stu-id="f66c2-108">For an example of using WCF with ASP.NET AJAX, see [AJAX Samples](ajax.md).</span></span>

<span data-ttu-id="f66c2-109">Este exemplo mostra como alternar o tipo de resposta de uma operação entre JSON e XML.</span><span class="sxs-lookup"><span data-stu-id="f66c2-109">This sample shows how to switch the response type of an operation between JSON and XML.</span></span> <span data-ttu-id="f66c2-110">Essa funcionalidade está disponível independentemente de o serviço estar configurado para ser acessado pelo ASP.NET AJAX ou por uma página de cliente HTML/JavaScript.</span><span class="sxs-lookup"><span data-stu-id="f66c2-110">This functionality is available regardless of whether the service is configured to be accessed by ASP.NET AJAX or by an HTML/JavaScript client page.</span></span>

> [!NOTE]
> <span data-ttu-id="f66c2-111">O procedimento de instalação e as instruções de Build para este exemplo estão localizados no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="f66c2-111">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

<span data-ttu-id="f66c2-112">Para habilitar o uso de clientes non-ASP.NET AJAX, use <xref:System.ServiceModel.Activation.WebServiceHostFactory> (não <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>) no arquivo. svc.</span><span class="sxs-lookup"><span data-stu-id="f66c2-112">To enable the use of non-ASP.NET AJAX clients, use <xref:System.ServiceModel.Activation.WebServiceHostFactory> (not <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>) in the .svc file.</span></span> <span data-ttu-id="f66c2-113"><xref:System.ServiceModel.Activation.WebServiceHostFactory>Adiciona um <xref:System.ServiceModel.Description.WebHttpEndpoint> ponto de extremidade padrão ao serviço.</span><span class="sxs-lookup"><span data-stu-id="f66c2-113"><xref:System.ServiceModel.Activation.WebServiceHostFactory> adds a <xref:System.ServiceModel.Description.WebHttpEndpoint> standard endpoint to the service.</span></span> <span data-ttu-id="f66c2-114">O ponto de extremidade está configurado em um endereço vazio relativo ao arquivo. svc; Isso significa que o endereço do serviço é `http://localhost/ServiceModelSamples/service.svc`, sem nenhum sufixo adicional além do nome da operação.</span><span class="sxs-lookup"><span data-stu-id="f66c2-114">The endpoint is configured at an empty address relative to the .svc file; this means that the address of the service is `http://localhost/ServiceModelSamples/service.svc`, with no additional suffixes other than the operation name.</span></span>

```svc
<%@ServiceHost language="c#" Debug="true" Service="Microsoft.Samples.XmlAjaxService.CalculatorService" Factory="System.ServiceModel.Activation.WebServiceHostFactory" %>
```

<span data-ttu-id="f66c2-115">A seção a seguir no Web. config pode ser usada para fazer alterações de configuração adicionais no ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="f66c2-115">The following section in Web.config can be used to make additional configuration changes to the endpoint.</span></span> <span data-ttu-id="f66c2-116">Ela poderá ser removida se nenhuma alteração extra for necessária.</span><span class="sxs-lookup"><span data-stu-id="f66c2-116">It can be removed if no extra changes are needed.</span></span>

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

<span data-ttu-id="f66c2-117">O formato de dados padrão <xref:System.ServiceModel.Description.WebHttpEndpoint> para o é XML, enquanto o formato de <xref:System.ServiceModel.Description.WebScriptEndpoint> dados padrão para é JSON.</span><span class="sxs-lookup"><span data-stu-id="f66c2-117">The default data format for <xref:System.ServiceModel.Description.WebHttpEndpoint> is XML, while the default data format for <xref:System.ServiceModel.Description.WebScriptEndpoint> is JSON.</span></span> <span data-ttu-id="f66c2-118">Para obter mais informações, consulte [CREATING WCF Ajax Services with ASP.net](../../../../docs/framework/wcf/feature-details/creating-wcf-ajax-services-without-aspnet.md).</span><span class="sxs-lookup"><span data-stu-id="f66c2-118">For more information, see [Creating WCF AJAX Services without ASP.NET](../../../../docs/framework/wcf/feature-details/creating-wcf-ajax-services-without-aspnet.md).</span></span>

<span data-ttu-id="f66c2-119">O serviço no exemplo a seguir é um serviço padrão do WCF com duas operações.</span><span class="sxs-lookup"><span data-stu-id="f66c2-119">The service in the following sample is a standard WCF service with two operations.</span></span> <span data-ttu-id="f66c2-120">Ambas as operações exigem <xref:System.ServiceModel.Web.WebMessageBodyStyle.Wrapped> o estilo do corpo <xref:System.ServiceModel.Web.WebGetAttribute> nos <xref:System.ServiceModel.Web.WebInvokeAttribute> atributos ou, que são específicos do `webHttp` comportamento e não têm nenhuma influência sobre a opção de formato de dados JSON/XML.</span><span class="sxs-lookup"><span data-stu-id="f66c2-120">Both operations require the <xref:System.ServiceModel.Web.WebMessageBodyStyle.Wrapped> body style on the <xref:System.ServiceModel.Web.WebGetAttribute> or <xref:System.ServiceModel.Web.WebInvokeAttribute> attributes, which is specific to the `webHttp` behavior and has no bearing on the JSON/XML data format switch.</span></span>

```csharp
[OperationContract]
[WebInvoke(ResponseFormat = WebMessageFormat.Xml, BodyStyle = WebMessageBodyStyle.Wrapped)]
MathResult DoMathXml(double n1, double n2);
```

<span data-ttu-id="f66c2-121">O formato de resposta para a operação é especificado como XML, que é a configuração padrão para o comportamento de [ \<> Webhttp](../../../../docs/framework/configure-apps/file-schema/wcf/webhttp.md) .</span><span class="sxs-lookup"><span data-stu-id="f66c2-121">The response format for the operation is specified as XML, which is the default setting for the [\<webHttp>](../../../../docs/framework/configure-apps/file-schema/wcf/webhttp.md) behavior.</span></span> <span data-ttu-id="f66c2-122">No entanto, é uma prática recomendada especificar explicitamente o formato de resposta.</span><span class="sxs-lookup"><span data-stu-id="f66c2-122">However, it is good practice explicitly specify the response format.</span></span>

<span data-ttu-id="f66c2-123">A outra operação usa o `WebInvokeAttribute` atributo e especifica explicitamente JSON em vez de XML para a resposta.</span><span class="sxs-lookup"><span data-stu-id="f66c2-123">The other operation uses the `WebInvokeAttribute` attribute and explicitly specifies JSON instead of XML for the response.</span></span>

```csharp
[OperationContract]
[WebInvoke(ResponseFormat = WebMessageFormat.Json, BodyStyle = WebMessageBodyStyle.Wrapped)]
MathResult DoMathJson(double n1, double n2);
```

<span data-ttu-id="f66c2-124">Observe que em ambos os casos as operações retornam um tipo `MathResult`complexo,, que é um tipo de contrato de dados padrão do WCF.</span><span class="sxs-lookup"><span data-stu-id="f66c2-124">Note that in both cases the operations return a complex type, `MathResult`, which is a standard WCF data contract type.</span></span>

<span data-ttu-id="f66c2-125">A página da Web do cliente XmlAjaxClientPage. htm contém o código JavaScript que invoca uma das duas operações anteriores quando o usuário clica nos botões **executar cálculo (retornar JSON)** ou **executar cálculo (XML de retorno)** na página.</span><span class="sxs-lookup"><span data-stu-id="f66c2-125">The client Web page XmlAjaxClientPage.htm contains JavaScript code that invokes one of the preceding two operations when the user clicks the **Perform calculation (return JSON)** or **Perform calculation (return XML)** buttons on the page.</span></span> <span data-ttu-id="f66c2-126">O código para invocar o serviço constrói um corpo JSON e o envia usando HTTP POST.</span><span class="sxs-lookup"><span data-stu-id="f66c2-126">The code to invoke the service constructs a JSON body and sends it using HTTP POST.</span></span> <span data-ttu-id="f66c2-127">A solicitação é criada manualmente em JavaScript, diferentemente do exemplo de [serviço AJAX básico](../../../../docs/framework/wcf/samples/basic-ajax-service.md) e de outros exemplos usando o ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="f66c2-127">The request is created manually in JavaScript, unlike the [Basic AJAX Service](../../../../docs/framework/wcf/samples/basic-ajax-service.md) sample and the other samples using ASP.NET AJAX.</span></span>

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

<span data-ttu-id="f66c2-128">Quando o serviço responde, a resposta é exibida sem nenhum processamento adicional em uma caixa de texto na página.</span><span class="sxs-lookup"><span data-stu-id="f66c2-128">When the service responds, the response is displayed without any further processing in a textbox on the page.</span></span> <span data-ttu-id="f66c2-129">Isso é implementado para fins de demonstração para permitir que você observe diretamente os formatos de dados XML e JSON usados.</span><span class="sxs-lookup"><span data-stu-id="f66c2-129">This is implemented for demonstration purposes to allow you to directly observe the XML and JSON data formats used.</span></span>

```javascript
// Create result handler
xmlHttp.onreadystatechange=function(){
     if(xmlHttp.readyState == 4){
          document.getElementById("result").value = xmlHttp.responseText;
     }
}
```

> [!IMPORTANT]
> <span data-ttu-id="f66c2-130">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="f66c2-130">The samples may already be installed on your machine.</span></span> <span data-ttu-id="f66c2-131">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="f66c2-131">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="f66c2-132">Se esse diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos de Windows Workflow Foundation (WF) para .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) [!INCLUDE[wf1](../../../../includes/wf1-md.md)] e exemplos.</span><span class="sxs-lookup"><span data-stu-id="f66c2-132">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="f66c2-133">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="f66c2-133">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\AJAX\XmlAjaxService`

#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="f66c2-134">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="f66c2-134">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="f66c2-135">Verifique se você executou o [procedimento de configuração única para os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="f66c2-135">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="f66c2-136">Crie a solução XmlAjaxService. sln, conforme descrito em [criando os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="f66c2-136">Build the solution XmlAjaxService.sln as described in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

3. <span data-ttu-id="f66c2-137">Navegue até `http://localhost/ServiceModelSamples/XmlAjaxClientPage.htm` (não abra XmlAjaxClientPage. htm no navegador do diretório do projeto).</span><span class="sxs-lookup"><span data-stu-id="f66c2-137">Navigate to `http://localhost/ServiceModelSamples/XmlAjaxClientPage.htm` (do not open XmlAjaxClientPage.htm in the browser from the project directory).</span></span>

## <a name="see-also"></a><span data-ttu-id="f66c2-138">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f66c2-138">See also</span></span>

- [<span data-ttu-id="f66c2-139">Serviço AJAX utilizando HTTP POST</span><span class="sxs-lookup"><span data-stu-id="f66c2-139">AJAX Service Using HTTP POST</span></span>](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md)
