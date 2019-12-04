---
title: Serviço AJAX básico
ms.date: 03/30/2017
ms.assetid: d66d0c91-0109-45a0-a901-f3e4667c2465
ms.openlocfilehash: 334cc9e53d7d9746c204abe37e7c30d00baa824b
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74716121"
---
# <a name="basic-ajax-service"></a><span data-ttu-id="2fef9-102">Serviço AJAX básico</span><span class="sxs-lookup"><span data-stu-id="2fef9-102">Basic AJAX Service</span></span>

<span data-ttu-id="2fef9-103">Este exemplo demonstra como usar o Windows Communication Foundation (WCF) para criar um serviço básico de JavaScript e XML (AJAX) ASP.NET assíncrono (um serviço que você pode acessar usando código JavaScript de um cliente de navegador da Web).</span><span class="sxs-lookup"><span data-stu-id="2fef9-103">This sample demonstrates how to use Windows Communication Foundation (WCF) to create a basic ASP.NET Asynchronous JavaScript and XML (AJAX) service (a service that you can access using JavaScript code from a Web browser client).</span></span> <span data-ttu-id="2fef9-104">O serviço usa o atributo <xref:System.ServiceModel.Web.WebGetAttribute> para garantir que o serviço responda às solicitações HTTP GET e esteja configurado para usar o formato de dados JavaScript Object Notation (JSON) para respostas.</span><span class="sxs-lookup"><span data-stu-id="2fef9-104">The service uses the <xref:System.ServiceModel.Web.WebGetAttribute> attribute to ensure that the service responds to HTTP GET requests and is configured to use the JavaScript Object Notation (JSON) data format for responses.</span></span>

<span data-ttu-id="2fef9-105">O suporte ao AJAX no WCF é otimizado para uso com o ASP.NET AJAX por meio do controle de `ScriptManager`.</span><span class="sxs-lookup"><span data-stu-id="2fef9-105">AJAX support in WCF is optimized for use with ASP.NET AJAX through the `ScriptManager` control.</span></span> <span data-ttu-id="2fef9-106">Para obter um exemplo de como usar o WCF com o ASP.NET AJAX, consulte os [exemplos do AJAX](ajax.md).</span><span class="sxs-lookup"><span data-stu-id="2fef9-106">For an example of using WCF with ASP.NET AJAX, see the [AJAX Samples](ajax.md).</span></span>

> [!NOTE]
> <span data-ttu-id="2fef9-107">Os procedimentos de instalação e as instruções de compilação para esse exemplo estão localizadas no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="2fef9-107">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>

<span data-ttu-id="2fef9-108">No código a seguir, o atributo <xref:System.ServiceModel.Web.WebGetAttribute> é aplicado à operação `Add` para garantir que o serviço responda às solicitações HTTP GET.</span><span class="sxs-lookup"><span data-stu-id="2fef9-108">In the following code, the <xref:System.ServiceModel.Web.WebGetAttribute> attribute is applied to the `Add` operation to ensure that the service responds to HTTP GET requests.</span></span> <span data-ttu-id="2fef9-109">O código usa GET para simplificação (você pode construir uma solicitação HTTP GET de qualquer navegador da Web).</span><span class="sxs-lookup"><span data-stu-id="2fef9-109">The code uses GET for simplicity (you can construct an HTTP GET request from any Web browser).</span></span> <span data-ttu-id="2fef9-110">Você também pode usar GET para habilitar o Caching.</span><span class="sxs-lookup"><span data-stu-id="2fef9-110">You can also use GET to enable caching.</span></span> <span data-ttu-id="2fef9-111">HTTP POST é o padrão na ausência do atributo `WebGetAttribute`.</span><span class="sxs-lookup"><span data-stu-id="2fef9-111">HTTP POST is the default in the absence of the `WebGetAttribute` attribute.</span></span>

```csharp
[ServiceContract(Namespace = "SimpleAjaxService")]
public interface ICalculator
{
    [WebGet]
    double Add(double n1, double n2);
    //Other operations omitted…
}
```

<span data-ttu-id="2fef9-112">O arquivo. svc de exemplo usa <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>, que adiciona um <xref:System.ServiceModel.Description.WebScriptEndpoint> ponto de extremidade padrão ao serviço.</span><span class="sxs-lookup"><span data-stu-id="2fef9-112">The sample .svc file uses <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>, which adds a <xref:System.ServiceModel.Description.WebScriptEndpoint> standard endpoint to the service.</span></span> <span data-ttu-id="2fef9-113">O ponto de extremidade é configurado em um endereço vazio relativo ao arquivo. svc.</span><span class="sxs-lookup"><span data-stu-id="2fef9-113">The endpoint is configured at an empty address relative to the .svc file.</span></span> <span data-ttu-id="2fef9-114">Isso significa que o endereço do serviço é `http://localhost/ServiceModelSamples/service.svc`, sem nenhum sufixo adicional diferente do nome da operação.</span><span class="sxs-lookup"><span data-stu-id="2fef9-114">This means that the address of the service is `http://localhost/ServiceModelSamples/service.svc`, with no additional suffixes other than the operation name.</span></span>

`<%@ServiceHost language="C#" Debug="true" Service="Microsoft.Samples.SimpleAjaxService.CalculatorService" Factory="System.ServiceModel.Activation.WebScriptServiceHostFactory" %>`

<span data-ttu-id="2fef9-115">O <xref:System.ServiceModel.Description.WebScriptEndpoint> é pré-configurado para tornar o serviço acessível de uma página de cliente do ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="2fef9-115">The <xref:System.ServiceModel.Description.WebScriptEndpoint> is pre-configured to make the service accessible from an ASP.NET AJAX client page.</span></span> <span data-ttu-id="2fef9-116">A seção a seguir no Web. config pode ser usada para fazer alterações de configuração adicionais no ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="2fef9-116">The following section in Web.config can be used to make additional configuration changes to the endpoint.</span></span> <span data-ttu-id="2fef9-117">Ela poderá ser removida se nenhuma alteração extra for necessária.</span><span class="sxs-lookup"><span data-stu-id="2fef9-117">It can be removed if no extra changes are required.</span></span>

```xml
<system.serviceModel>
  <standardEndpoints>
    <webScriptEndpoint>
      <!-- Use this element to configure the endpoint -->
      <standardEndpoint name=""  />
    </webScriptEndpoint>
  </standardEndpoints>
</system.serviceModel>
```

<span data-ttu-id="2fef9-118">O <xref:System.ServiceModel.Description.WebScriptEndpoint> define o formato de dados padrão para o serviço como JSON em vez de XML.</span><span class="sxs-lookup"><span data-stu-id="2fef9-118">The <xref:System.ServiceModel.Description.WebScriptEndpoint> sets the default data format for the service to JSON instead of XML.</span></span> <span data-ttu-id="2fef9-119">Para invocar o serviço, navegue até `http://localhost/ServiceModelSamples/service.svc/Add?n1=100&n2=200` depois de concluir a configuração e as etapas de compilação mostradas mais adiante neste tópico.</span><span class="sxs-lookup"><span data-stu-id="2fef9-119">To invoke the service, navigate to `http://localhost/ServiceModelSamples/service.svc/Add?n1=100&n2=200` after completing the set up and build steps shown later in this topic.</span></span> <span data-ttu-id="2fef9-120">Essa funcionalidade de teste é habilitada pelo uso de uma solicitação HTTP GET.</span><span class="sxs-lookup"><span data-stu-id="2fef9-120">This testing functionality is enabled by the use of a HTTP GET request.</span></span>

<span data-ttu-id="2fef9-121">A página da Web do cliente SimpleAjaxClientPage. aspx contém o código ASP.NET para invocar o serviço sempre que o usuário clicar em um dos botões de operação na página.</span><span class="sxs-lookup"><span data-stu-id="2fef9-121">The client Web page SimpleAjaxClientPage.aspx contains ASP.NET code to invoke the service whenever the user clicks one of the operation buttons on the page.</span></span> <span data-ttu-id="2fef9-122">O controle de `ScriptManager` é usado para tornar um proxy para o serviço acessível por meio de JavaScript.</span><span class="sxs-lookup"><span data-stu-id="2fef9-122">The `ScriptManager` control is used to make a proxy to the service accessible through JavaScript.</span></span>

```aspx-csharp
<asp:ScriptManager ID="ScriptManager" runat="server">
    <Services>
        <asp:ServiceReference Path="service.svc" />
    </Services>
</asp:ScriptManager>
```

<span data-ttu-id="2fef9-123">O proxy local é instanciado e as operações são invocadas usando o código JavaScript a seguir.</span><span class="sxs-lookup"><span data-stu-id="2fef9-123">The local proxy is instantiated and operations are invoked using the following JavaScript code.</span></span>

```javascript
// Code for extracting arguments n1 and n2 omitted…
// Instantiate a service proxy
var proxy = new SimpleAjaxService.ICalculator();
// Code for selecting operation omitted…
proxy.Add(parseFloat(n1), parseFloat(n2), onSuccess, onFail, null);
```

<span data-ttu-id="2fef9-124">Se a chamada de serviço for bem sucedido, o código invocará o manipulador de `onSuccess` e o resultado da operação será exibido em uma caixa de texto.</span><span class="sxs-lookup"><span data-stu-id="2fef9-124">If the service call succeeds, the code invokes the `onSuccess` handler and the result of the operation is displayed in a text box.</span></span>

```javascript
function onSuccess(mathResult){
     document.getElementById("result").value = mathResult;
}
```

> [!IMPORTANT]
> <span data-ttu-id="2fef9-125">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="2fef9-125">The samples may already be installed on your machine.</span></span> <span data-ttu-id="2fef9-126">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="2fef9-126">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="2fef9-127">Se esse diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos de Windows Workflow Foundation (WF) para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] amostras.</span><span class="sxs-lookup"><span data-stu-id="2fef9-127">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="2fef9-128">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="2fef9-128">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\SimpleAjaxService`
