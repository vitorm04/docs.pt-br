---
title: Serviço AJAX utilizando HTTP POST
ms.date: 03/30/2017
ms.assetid: 1ac80f20-ac1c-4ed1-9850-7e49569ff44e
ms.openlocfilehash: f904a26d87a21a931035b45261dbcd970f7d63a1
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33804102"
---
# <a name="ajax-service-using-http-post"></a><span data-ttu-id="f4016-102">Serviço AJAX utilizando HTTP POST</span><span class="sxs-lookup"><span data-stu-id="f4016-102">AJAX Service Using HTTP POST</span></span>
<span data-ttu-id="f4016-103">Este exemplo demonstra como usar o Windows Communication Foundation (WCF) para criar um [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] serviço JavaScript assíncrono e XML (AJAX) que usa o HTTP POST.</span><span class="sxs-lookup"><span data-stu-id="f4016-103">This sample demonstrates how to use Windows Communication Foundation (WCF) to create an [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Asynchronous JavaScript and XML (AJAX) service that uses HTTP POST.</span></span> <span data-ttu-id="f4016-104">Um serviço de AJAX é aquele que você pode acessar usando o código JavaScript básico de um cliente de navegador da Web.</span><span class="sxs-lookup"><span data-stu-id="f4016-104">An AJAX service is one that you can access by using basic JavaScript code from a Web browser client.</span></span> <span data-ttu-id="f4016-105">Este exemplo se baseia o [serviço AJAX básico](../../../../docs/framework/wcf/samples/basic-ajax-service.md) exemplo; a única diferença entre os dois exemplos é o uso de HTTP POST em vez de HTTP GET.</span><span class="sxs-lookup"><span data-stu-id="f4016-105">This sample builds on the [Basic AJAX Service](../../../../docs/framework/wcf/samples/basic-ajax-service.md) sample; the only difference between the two samples is the use of HTTP POST instead of HTTP GET.</span></span>  
  
 <span data-ttu-id="f4016-106">Suporte do AJAX no Windows Communication Foundation (WCF) é otimizado para uso com o ASP.NET AJAX por meio de `ScriptManager` controle.</span><span class="sxs-lookup"><span data-stu-id="f4016-106">AJAX support in Windows Communication Foundation (WCF) is optimized for use with ASP.NET AJAX through the `ScriptManager` control.</span></span> <span data-ttu-id="f4016-107">Para obter um exemplo de como usar o WCF com o ASP.NET AJAX, consulte o [Ajax exemplos](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md).</span><span class="sxs-lookup"><span data-stu-id="f4016-107">For an example of using WCF with ASP.NET AJAX, see the [Ajax Samples](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f4016-108">As instruções de procedimento e a compilação de configuração para este exemplo estão localizadas no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="f4016-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="f4016-109">O serviço no exemplo a seguir é um serviço WCF, sem nenhum código específico do AJAX.</span><span class="sxs-lookup"><span data-stu-id="f4016-109">The service in the following sample is a WCF service with no AJAX-specific code.</span></span>  
  
 <span data-ttu-id="f4016-110">Se o <xref:System.ServiceModel.Web.WebInvokeAttribute> atributo é aplicado em uma operação, ou o <xref:System.ServiceModel.Web.WebGetAttribute> atributo não é aplicado, o verbo HTTP padrão ("POST") é usado.</span><span class="sxs-lookup"><span data-stu-id="f4016-110">If the <xref:System.ServiceModel.Web.WebInvokeAttribute> attribute is applied on an operation, or the <xref:System.ServiceModel.Web.WebGetAttribute> attribute is not applied, the default HTTP verb ("POST") is used.</span></span> <span data-ttu-id="f4016-111">As solicitações POST são mais difíceis de construir que as solicitações GET, mas eles não estão em cache; Use solicitações POST para todas as operações em que o cache não é apropriado.</span><span class="sxs-lookup"><span data-stu-id="f4016-111">POST requests are harder to construct than GET requests, but they are not cached; use POST requests for all operations where caching is not appropriate.</span></span>  

```csharp
[ServiceContract(Namespace = "PostAjaxService")]  
public interface ICalculator  
{
    [WebInvoke]  
    double Add(double n1, double n2);  
    //Other operations omitted…  
}
```

 <span data-ttu-id="f4016-112">Crie um ponto de extremidade do AJAX no serviço usando o <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>, assim como o exemplo de serviço AJAX básico.</span><span class="sxs-lookup"><span data-stu-id="f4016-112">Create an AJAX endpoint on the service by using the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>, just as in the Basic AJAX Service sample.</span></span>  
  
 <span data-ttu-id="f4016-113">Ao contrário das solicitações GET, você não pode invocar serviços POST do navegador.</span><span class="sxs-lookup"><span data-stu-id="f4016-113">Unlike GET requests, you cannot invoke POST services from the browser.</span></span> <span data-ttu-id="f4016-114">Por exemplo, navegando para http://localhost/ServiceModelSamples/service.svc/Add?n1=100&n2=200 resulta em um erro, porque o serviço de POSTAGEM espera o `n1` e `n2` parâmetros para ser enviados no corpo da mensagem — no formato JSON — e não na URL.</span><span class="sxs-lookup"><span data-stu-id="f4016-114">For example, navigating to http://localhost/ServiceModelSamples/service.svc/Add?n1=100&n2=200 results in an error, because the POST service expects the `n1` and `n2` parameters to be sent in the message body—in the JSON format—and not in the URL.</span></span>  
  
 <span data-ttu-id="f4016-115">O cliente PostAjaxClientPage.aspx de página da Web contém código para chamar o serviço sempre que o usuário clica em um dos botões de operação na página do ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="f4016-115">The client Web page PostAjaxClientPage.aspx contains ASP.NET code to invoke the service whenever the user clicks one of the operation buttons on the page.</span></span> <span data-ttu-id="f4016-116">O serviço responde da mesma maneira como no [serviço AJAX básico](../../../../docs/framework/wcf/samples/basic-ajax-service.md) exemplo, com a solicitação de obtenção.</span><span class="sxs-lookup"><span data-stu-id="f4016-116">The service responds in the same way as in the [Basic AJAX Service](../../../../docs/framework/wcf/samples/basic-ajax-service.md) sample, with the GET request.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="f4016-117">Os exemplos podem mais ser instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="f4016-117">The samples may already be installed on your computer.</span></span> <span data-ttu-id="f4016-118">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="f4016-118">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="f4016-119">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="f4016-119">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="f4016-120">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="f4016-120">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\PostAjaxService`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="f4016-121">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="f4016-121">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="f4016-122">Certifique-se de que você execute as instruções de instalação [único procedimento de instalação para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="f4016-122">Ensure that you perform the setup instructions [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="f4016-123">Compile a solução PostAjaxService.sln conforme descrito em [compilar os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="f4016-123">Build the solution PostAjaxService.sln as described in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="f4016-124">Navegue até http://localhost/ServiceModelSamples/PostAjaxClientPage.aspx (não abrir PostAjaxClientPage.aspx no navegador do diretório do projeto).</span><span class="sxs-lookup"><span data-stu-id="f4016-124">Navigate to http://localhost/ServiceModelSamples/PostAjaxClientPage.aspx (do not open PostAjaxClientPage.aspx in the browser from the project directory).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4016-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f4016-125">See Also</span></span>
