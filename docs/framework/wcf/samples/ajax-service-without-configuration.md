---
title: Serviço AJAX sem configuração
ms.date: 03/30/2017
ms.assetid: e6db7acd-5679-45d4-b98a-8449c6873838
ms.openlocfilehash: 24f07193b955e2b4877ac2e9302a7be0cd879676
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69913353"
---
# <a name="ajax-service-without-configuration"></a><span data-ttu-id="e2cb5-102">Serviço AJAX sem configuração</span><span class="sxs-lookup"><span data-stu-id="e2cb5-102">AJAX Service Without Configuration</span></span>
<span data-ttu-id="e2cb5-103">Este exemplo demonstra como usar o Windows Communication Foundation (WCF) para criar um serviço básico de JavaScript e XML (AJAX) ASP.NET assíncrono (um serviço que você pode acessar usando o código JavaScript de um cliente de navegador da Web) sem usar nenhuma configuração Configurações.</span><span class="sxs-lookup"><span data-stu-id="e2cb5-103">This sample demonstrates how to use Windows Communication Foundation (WCF) to create a basic ASP.NET Asynchronous JavaScript and XML (AJAX) service (a service that you can access by using JavaScript code from a Web browser client) without using any configuration settings.</span></span> <span data-ttu-id="e2cb5-104">O serviço usa uma sintaxe especial no arquivo. svc para habilitar automaticamente um ponto de extremidade AJAX.</span><span class="sxs-lookup"><span data-stu-id="e2cb5-104">The service uses special syntax in the .svc file to automatically enable an AJAX endpoint.</span></span>  
  
 <span data-ttu-id="e2cb5-105">O suporte ao AJAX no WCF é otimizado para uso com o `ScriptManager` ASP.NET AJAX por meio do controle.</span><span class="sxs-lookup"><span data-stu-id="e2cb5-105">AJAX support in WCF is optimized for use with ASP.NET AJAX through the `ScriptManager` control.</span></span> <span data-ttu-id="e2cb5-106">Para obter um exemplo de como usar o WCF com o ASP.NET AJAX, consulte os [exemplos do AJAX](ajax.md).</span><span class="sxs-lookup"><span data-stu-id="e2cb5-106">For an example of using WCF with ASP.NET AJAX, see the [Ajax Samples](ajax.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e2cb5-107">O procedimento de instalação e as instruções de Build para este exemplo estão localizados no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="e2cb5-107">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="e2cb5-108">Este exemplo baseia-se no serviço AJAX usando HTTP POST.</span><span class="sxs-lookup"><span data-stu-id="e2cb5-108">This sample builds upon the AJAX Service Using HTTP POST.</span></span> <span data-ttu-id="e2cb5-109">Conforme descrito no exemplo [básico de serviço AJAX](../../../../docs/framework/wcf/samples/basic-ajax-service.md) , <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> é usado para hospedar o serviço.</span><span class="sxs-lookup"><span data-stu-id="e2cb5-109">As described in the [Basic AJAX Service](../../../../docs/framework/wcf/samples/basic-ajax-service.md) sample, <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> is used to host the service.</span></span>  

```svc
<%ServiceHost  
    language=c#  
    Debug="true"  
    Service="Microsoft.Ajax.Samples.CalculatorService  
    Factory="System.ServiceModel.Activation.WebScriptServiceHostFactory"  
%>  
```

 <span data-ttu-id="e2cb5-110"><xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>adiciona automaticamente um <xref:System.ServiceModel.Description.WebScriptEndpoint> ao serviço.</span><span class="sxs-lookup"><span data-stu-id="e2cb5-110"><xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> automatically adds a <xref:System.ServiceModel.Description.WebScriptEndpoint> to the service.</span></span> <span data-ttu-id="e2cb5-111">Se nenhuma alteração de configuração precisar ser feita no ponto de extremidade, `<system.ServiceModel>` a seção poderá ser completamente removida do arquivo Web. config para o serviço.</span><span class="sxs-lookup"><span data-stu-id="e2cb5-111">If no configuration changes need to be made to the endpoint, the `<system.ServiceModel>` section can be completely removed from the Web.config file for the service.</span></span> <span data-ttu-id="e2cb5-112">O arquivo Web. config contém algumas configurações de ASP.NET, que são usadas pelo ConfigFreeClientPage. aspx.</span><span class="sxs-lookup"><span data-stu-id="e2cb5-112">The Web.config file contains some ASP.NET settings, which are used by ConfigFreeClientPage.aspx.</span></span> <span data-ttu-id="e2cb5-113">Se esse não for o caso, todo o arquivo Web. config poderá ser removido.</span><span class="sxs-lookup"><span data-stu-id="e2cb5-113">If that were not the case, the entire Web.config file could be removed.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="e2cb5-114">Os exemplos podem mais ser instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="e2cb5-114">The samples may already be installed on your computer.</span></span> <span data-ttu-id="e2cb5-115">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="e2cb5-115">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="e2cb5-116">Se esse diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos de Windows Workflow Foundation (WF) para .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) [!INCLUDE[wf1](../../../../includes/wf1-md.md)] e exemplos.</span><span class="sxs-lookup"><span data-stu-id="e2cb5-116">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="e2cb5-117">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="e2cb5-117">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\ConfigFreeAjaxService`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="e2cb5-118">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="e2cb5-118">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="e2cb5-119">Certifique-se de executar as instruções de instalação no [procedimento de configuração única para os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e2cb5-119">Ensure that you perform the setup instructions in [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="e2cb5-120">Crie a solução ConfigFreeAjaxService. sln, conforme descrito em [criando os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e2cb5-120">Build the solution ConfigFreeAjaxService.sln as described in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="e2cb5-121">Navegue até `http://localhost/ServiceModelSamples/ConfigFreeClientPage.aspx` (não abra ConfigFreeClientPage. aspx no navegador de dentro do diretório do projeto).</span><span class="sxs-lookup"><span data-stu-id="e2cb5-121">Navigate to `http://localhost/ServiceModelSamples/ConfigFreeClientPage.aspx` (do not open ConfigFreeClientPage.aspx in the browser from within the project directory).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e2cb5-122">Ao executar este exemplo, verifique se a autenticação anônima e a autenticação do Windows não estão habilitadas simultaneamente para a pasta ServiceModelSamples no IIS.</span><span class="sxs-lookup"><span data-stu-id="e2cb5-122">When running this sample, please ensure that Anonymous Authentication and Windows Authentication are not enabled simultaneously for the ServiceModelSamples folder in IIS.</span></span> <span data-ttu-id="e2cb5-123">Se esse for o caso, desabilite a autenticação do Windows.</span><span class="sxs-lookup"><span data-stu-id="e2cb5-123">If that is the case, please disable Windows Authentication.</span></span> <span data-ttu-id="e2cb5-124">Depois de executar o exemplo, habilite a autenticação do Windows e execute "iisreset".</span><span class="sxs-lookup"><span data-stu-id="e2cb5-124">Once you have run the sample, enable Windows Authentication and run "iisreset".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2cb5-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e2cb5-125">See also</span></span>

- [<span data-ttu-id="e2cb5-126">Serviço AJAX básico</span><span class="sxs-lookup"><span data-stu-id="e2cb5-126">Basic AJAX Service</span></span>](../../../../docs/framework/wcf/samples/basic-ajax-service.md)
