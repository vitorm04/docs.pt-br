---
title: "Serviço AJAX básico"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d66d0c91-0109-45a0-a901-f3e4667c2465
caps.latest.revision: "30"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6b2bf20c0a98f0571780e5af45c32f8062450d88
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2018
---
# <a name="basic-ajax-service"></a><span data-ttu-id="fc523-102">Serviço AJAX básico</span><span class="sxs-lookup"><span data-stu-id="fc523-102">Basic AJAX Service</span></span>
<span data-ttu-id="fc523-103">Este exemplo demonstra como usar [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] para criar um serviço básico de JavaScript assíncrona do ASP.NET AJAX (and XML) (um serviço que você pode acessar usando o código JavaScript de um cliente de navegador da Web).</span><span class="sxs-lookup"><span data-stu-id="fc523-103">This sample demonstrates how to use [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] to create a basic ASP.NET Asynchronous JavaScript and XML (AJAX) service (a service that you can access using JavaScript code from a Web browser client).</span></span> <span data-ttu-id="fc523-104">O serviço usa o <xref:System.ServiceModel.Web.WebGetAttribute> atributo para garantir que o serviço responde a solicitações HTTP GET e está configurado para usar o formato de dados de objeto notação JSON (JavaScript) para respostas.</span><span class="sxs-lookup"><span data-stu-id="fc523-104">The service uses the <xref:System.ServiceModel.Web.WebGetAttribute> attribute to ensure that the service responds to HTTP GET requests and is configured to use the JavaScript Object Notation (JSON) data format for responses.</span></span>  
  
 <span data-ttu-id="fc523-105">Suporte do AJAX no [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] é otimizado para uso com o ASP.NET AJAX por meio de `ScriptManager` controle.</span><span class="sxs-lookup"><span data-stu-id="fc523-105">AJAX support in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] is optimized for use with ASP.NET AJAX through the `ScriptManager` control.</span></span> <span data-ttu-id="fc523-106">Para obter um exemplo do uso de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] com o ASP.NET AJAX, consulte o [AJAX exemplos](http://msdn.microsoft.com/library/f3fa45b3-44d5-4926-8cc4-a13c30a3bf3e).</span><span class="sxs-lookup"><span data-stu-id="fc523-106">For an example of using [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] with ASP.NET AJAX, see the [AJAX Samples](http://msdn.microsoft.com/library/f3fa45b3-44d5-4926-8cc4-a13c30a3bf3e).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fc523-107">Os procedimentos de instalação e as instruções de compilação para esse exemplo estão localizadas no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="fc523-107">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="fc523-108">No código a seguir, o <xref:System.ServiceModel.Web.WebGetAttribute> atributo é aplicado para o `Add` operação para garantir que o serviço responde a solicitações HTTP GET.</span><span class="sxs-lookup"><span data-stu-id="fc523-108">In the following code, the <xref:System.ServiceModel.Web.WebGetAttribute> attribute is applied to the `Add` operation to ensure that the service responds to HTTP GET requests.</span></span> <span data-ttu-id="fc523-109">O código usa GET para manter a simplicidade (você pode construir uma solicitação HTTP GET em qualquer navegador da Web).</span><span class="sxs-lookup"><span data-stu-id="fc523-109">The code uses GET for simplicity (you can construct an HTTP GET request from any Web browser).</span></span> <span data-ttu-id="fc523-110">Você também pode usar GET para habilitar o cache.</span><span class="sxs-lookup"><span data-stu-id="fc523-110">You can also use GET to enable caching.</span></span> <span data-ttu-id="fc523-111">HTTP POST é o padrão na ausência de `WebGetAttribute` atributo.</span><span class="sxs-lookup"><span data-stu-id="fc523-111">HTTP POST is the default in the absence of the `WebGetAttribute` attribute.</span></span>  
  
```  
[ServiceContract(Namespace = "SimpleAjaxService")]  
public interface ICalculator  
{  
  
    [WebGet]  
    double Add(double n1, double n2);  
    //Other operations omitted…  
}  
```  
  
 <span data-ttu-id="fc523-112">O arquivo. svc de exemplo usa <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>, que adiciona um <xref:System.ServiceModel.Description.WebScriptEndpoint> ponto de extremidade padrão para o serviço.</span><span class="sxs-lookup"><span data-stu-id="fc523-112">The sample .svc file uses <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>, which adds a <xref:System.ServiceModel.Description.WebScriptEndpoint> standard endpoint to the service.</span></span> <span data-ttu-id="fc523-113">O ponto de extremidade é configurado em um endereço vazio em relação ao arquivo. svc.</span><span class="sxs-lookup"><span data-stu-id="fc523-113">The endpoint is configured at an empty address relative to the .svc file.</span></span> <span data-ttu-id="fc523-114">Isso significa que o endereço do serviço é http://localhost/ServiceModelSamples/service.svc com nenhuma sufixos adicionais que não seja o nome da operação.</span><span class="sxs-lookup"><span data-stu-id="fc523-114">This means that the address of the service is http://localhost/ServiceModelSamples/service.svc, with no additional suffixes other than the operation name.</span></span>  
  
```  
<%@ServiceHost language="C#" Debug="true" Service="Microsoft.Samples.SimpleAjaxService.CalculatorService" Factory="System.ServiceModel.Activation.WebScriptServiceHostFactory" %>  
```  
  
 <span data-ttu-id="fc523-115">O <xref:System.ServiceModel.Description.WebScriptEndpoint> é pré-configurado para disponibilizar o serviço de uma página de cliente ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="fc523-115">The <xref:System.ServiceModel.Description.WebScriptEndpoint> is pre-configured to make the service accessible from an ASP.NET AJAX client page.</span></span> <span data-ttu-id="fc523-116">A seção a seguir no Web. config pode ser usada para fazer alterações de configuração adicionais para o ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="fc523-116">The following section in Web.config can be used to make additional configuration changes to the endpoint.</span></span> <span data-ttu-id="fc523-117">Ele pode ser removido se nenhuma alteração adicional é necessária.</span><span class="sxs-lookup"><span data-stu-id="fc523-117">It can be removed if no extra changes are required.</span></span>  
  
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
  
 <span data-ttu-id="fc523-118">O <xref:System.ServiceModel.Description.WebScriptEndpoint> define o formato de dados padrão para o serviço em JSON em vez de XML.</span><span class="sxs-lookup"><span data-stu-id="fc523-118">The <xref:System.ServiceModel.Description.WebScriptEndpoint> sets the default data format for the service to JSON instead of XML.</span></span> <span data-ttu-id="fc523-119">Para chamar o serviço, navegue até http://localhost/ServiceModelSamples/service.svc/Add?n1=100&n2=200 depois de concluir o conjunto de backup e criar etapas mostradas neste tópico.</span><span class="sxs-lookup"><span data-stu-id="fc523-119">To invoke the service, navigate to http://localhost/ServiceModelSamples/service.svc/Add?n1=100&n2=200 after completing the set up and build steps shown later in this topic.</span></span> <span data-ttu-id="fc523-120">Essa funcionalidade de teste é habilitada pelo uso de uma solicitação HTTP GET.</span><span class="sxs-lookup"><span data-stu-id="fc523-120">This testing functionality is enabled by the use of a HTTP GET request.</span></span>  
  
 <span data-ttu-id="fc523-121">O cliente SimpleAjaxClientPage.aspx de página da Web contém código para chamar o serviço sempre que o usuário clica em um dos botões de operação na página do ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="fc523-121">The client Web page SimpleAjaxClientPage.aspx contains ASP.NET code to invoke the service whenever the user clicks one of the operation buttons on the page.</span></span> <span data-ttu-id="fc523-122">O `ScriptManager` controle é usado para disponibilizar um proxy para o serviço por meio de JavaScript.</span><span class="sxs-lookup"><span data-stu-id="fc523-122">The `ScriptManager` control is used to make a proxy to the service accessible through JavaScript.</span></span>  
  
```  
<asp:ScriptManager ID="ScriptManager" runat="server">  
    <Services>  
        <asp:ServiceReference Path="service.svc" />  
    </Services>  
</asp:ScriptManager>  
```  
  
 <span data-ttu-id="fc523-123">O proxy local é instanciado e operações são invocadas usando o seguinte código JavaScript.</span><span class="sxs-lookup"><span data-stu-id="fc523-123">The local proxy is instantiated and operations are invoked using the following JavaScript code.</span></span>  
  
```  
// Code for extracting arguments n1 and n2 omitted…  
// Instantiate a service proxy  
var proxy = new SimpleAjaxService.ICalculator();  
// Code for selecting operation omitted…  
proxy.Add(parseFloat(n1), parseFloat(n2), onSuccess, onFail, null);  
```  
  
 <span data-ttu-id="fc523-124">Se a chamada de serviço for bem-sucedida, o código chama o `onSuccess` manipulador e o resultado da operação é exibido na caixa de texto.</span><span class="sxs-lookup"><span data-stu-id="fc523-124">If the service call succeeds, the code invokes the `onSuccess` handler and the result of the operation is displayed in a text box.</span></span>  
  
```  
function onSuccess(mathResult){  
     document.getElementById("result").value = mathResult;  
}  
```  
  
> [!IMPORTANT]
>  <span data-ttu-id="fc523-125">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="fc523-125">The samples may already be installed on your machine.</span></span> <span data-ttu-id="fc523-126">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="fc523-126">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="fc523-127">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="fc523-127">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="fc523-128">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="fc523-128">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\SimpleAjaxService`  
  
## <a name="see-also"></a><span data-ttu-id="fc523-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fc523-129">See Also</span></span>
