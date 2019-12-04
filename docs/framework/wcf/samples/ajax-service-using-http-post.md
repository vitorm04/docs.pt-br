---
title: Serviço AJAX utilizando HTTP POST
ms.date: 03/30/2017
ms.assetid: 1ac80f20-ac1c-4ed1-9850-7e49569ff44e
ms.openlocfilehash: 560739c576965d597010a6885b53c7905aaeb8e7
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74716189"
---
# <a name="ajax-service-using-http-post"></a><span data-ttu-id="b13d8-102">Serviço AJAX utilizando HTTP POST</span><span class="sxs-lookup"><span data-stu-id="b13d8-102">AJAX Service Using HTTP POST</span></span>

<span data-ttu-id="b13d8-103">Este exemplo demonstra como usar o Windows Communication Foundation (WCF) para criar um serviço de JavaScript e XML (AJAX) assíncrono do ASP.NET que usa HTTP POST.</span><span class="sxs-lookup"><span data-stu-id="b13d8-103">This sample demonstrates how to use Windows Communication Foundation (WCF) to create an ASP.NET Asynchronous JavaScript and XML (AJAX) service that uses HTTP POST.</span></span> <span data-ttu-id="b13d8-104">Um serviço AJAX é aquele que você pode acessar usando o código básico do JavaScript de um cliente de navegador da Web.</span><span class="sxs-lookup"><span data-stu-id="b13d8-104">An AJAX service is one that you can access by using basic JavaScript code from a Web browser client.</span></span> <span data-ttu-id="b13d8-105">Este exemplo baseia-se no exemplo [básico de serviço AJAX](../../../../docs/framework/wcf/samples/basic-ajax-service.md) ; a única diferença entre os dois exemplos é o uso de HTTP POST em vez de HTTP GET.</span><span class="sxs-lookup"><span data-stu-id="b13d8-105">This sample builds on the [Basic AJAX Service](../../../../docs/framework/wcf/samples/basic-ajax-service.md) sample; the only difference between the two samples is the use of HTTP POST instead of HTTP GET.</span></span>

<span data-ttu-id="b13d8-106">O suporte ao AJAX no Windows Communication Foundation (WCF) é otimizado para uso com o ASP.NET AJAX por meio do controle de `ScriptManager`.</span><span class="sxs-lookup"><span data-stu-id="b13d8-106">AJAX support in Windows Communication Foundation (WCF) is optimized for use with ASP.NET AJAX through the `ScriptManager` control.</span></span> <span data-ttu-id="b13d8-107">Para obter um exemplo de como usar o WCF com o ASP.NET AJAX, consulte os [exemplos do AJAX](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md).</span><span class="sxs-lookup"><span data-stu-id="b13d8-107">For an example of using WCF with ASP.NET AJAX, see the [Ajax Samples](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md).</span></span>

> [!NOTE]
> <span data-ttu-id="b13d8-108">O procedimento de instalação e as instruções de Build para este exemplo estão localizados no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="b13d8-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

<span data-ttu-id="b13d8-109">O serviço no exemplo a seguir é um serviço WCF sem código específico do AJAX.</span><span class="sxs-lookup"><span data-stu-id="b13d8-109">The service in the following sample is a WCF service with no AJAX-specific code.</span></span>

<span data-ttu-id="b13d8-110">Se o atributo <xref:System.ServiceModel.Web.WebInvokeAttribute> for aplicado em uma operação ou o atributo <xref:System.ServiceModel.Web.WebGetAttribute> não for aplicado, o verbo HTTP padrão ("POST") será usado.</span><span class="sxs-lookup"><span data-stu-id="b13d8-110">If the <xref:System.ServiceModel.Web.WebInvokeAttribute> attribute is applied on an operation, or the <xref:System.ServiceModel.Web.WebGetAttribute> attribute is not applied, the default HTTP verb ("POST") is used.</span></span> <span data-ttu-id="b13d8-111">Solicitações POST são mais difíceis de construir que solicitações GET, mas não são armazenadas em cache; Use solicitações POST para todas as operações em que o Caching não é apropriado.</span><span class="sxs-lookup"><span data-stu-id="b13d8-111">POST requests are harder to construct than GET requests, but they are not cached; use POST requests for all operations where caching is not appropriate.</span></span>

```csharp
[ServiceContract(Namespace = "PostAjaxService")]
public interface ICalculator
{
    [WebInvoke]
    double Add(double n1, double n2);
    //Other operations omitted…
}
```

<span data-ttu-id="b13d8-112">Crie um ponto de extremidade AJAX no serviço usando o <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>, assim como no exemplo de serviço básico AJAX.</span><span class="sxs-lookup"><span data-stu-id="b13d8-112">Create an AJAX endpoint on the service by using the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>, just as in the Basic AJAX Service sample.</span></span>

<span data-ttu-id="b13d8-113">Ao contrário das solicitações GET, não é possível invocar serviços POST do navegador.</span><span class="sxs-lookup"><span data-stu-id="b13d8-113">Unlike GET requests, you cannot invoke POST services from the browser.</span></span> <span data-ttu-id="b13d8-114">Por exemplo, navegar até `http://localhost/ServiceModelSamples/service.svc/Add?n1=100&n2=200` resulta em um erro, pois o serviço de POSTAgem espera que os parâmetros `n1` e `n2` sejam enviados no corpo da mensagem no formato JSON, e não na URL.</span><span class="sxs-lookup"><span data-stu-id="b13d8-114">For example, navigating to `http://localhost/ServiceModelSamples/service.svc/Add?n1=100&n2=200` results in an error, because the POST service expects the `n1` and `n2` parameters to be sent in the message body in the JSON format, and not in the URL.</span></span>

<span data-ttu-id="b13d8-115">A página da Web do cliente PostAjaxClientPage. aspx contém o código ASP.NET para invocar o serviço sempre que o usuário clicar em um dos botões de operação na página.</span><span class="sxs-lookup"><span data-stu-id="b13d8-115">The client Web page PostAjaxClientPage.aspx contains ASP.NET code to invoke the service whenever the user clicks one of the operation buttons on the page.</span></span> <span data-ttu-id="b13d8-116">O serviço responde da mesma maneira que no exemplo de [serviço AJAX básico](../../../../docs/framework/wcf/samples/basic-ajax-service.md) , com a solicitação get.</span><span class="sxs-lookup"><span data-stu-id="b13d8-116">The service responds in the same way as in the [Basic AJAX Service](../../../../docs/framework/wcf/samples/basic-ajax-service.md) sample, with the GET request.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b13d8-117">Os exemplos podem mais ser instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="b13d8-117">The samples may already be installed on your computer.</span></span> <span data-ttu-id="b13d8-118">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="b13d8-118">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="b13d8-119">Se esse diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos de Windows Workflow Foundation (WF) para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] amostras.</span><span class="sxs-lookup"><span data-stu-id="b13d8-119">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="b13d8-120">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="b13d8-120">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\PostAjaxService`

## <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="b13d8-121">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="b13d8-121">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="b13d8-122">Certifique-se de executar as instruções de instalação do [procedimento de configuração única para os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="b13d8-122">Ensure that you perform the setup instructions [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="b13d8-123">Crie a solução PostAjaxService. sln, conforme descrito em [criando os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="b13d8-123">Build the solution PostAjaxService.sln as described in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

3. <span data-ttu-id="b13d8-124">Navegue até `http://localhost/ServiceModelSamples/PostAjaxClientPage.aspx` (não abra PostAjaxClientPage. aspx no navegador do diretório do projeto).</span><span class="sxs-lookup"><span data-stu-id="b13d8-124">Navigate to `http://localhost/ServiceModelSamples/PostAjaxClientPage.aspx` (do not open PostAjaxClientPage.aspx in the browser from the project directory).</span></span>
