---
title: "Serviço AJAX sem configuração"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e6db7acd-5679-45d4-b98a-8449c6873838
caps.latest.revision: "23"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 32879c2b618f3e22960a7828d29601f502a55585
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="ajax-service-without-configuration"></a><span data-ttu-id="ce1cb-102">Serviço AJAX sem configuração</span><span class="sxs-lookup"><span data-stu-id="ce1cb-102">AJAX Service Without Configuration</span></span>
<span data-ttu-id="ce1cb-103">Este exemplo demonstra como usar [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] para criar um básico ASP.NET Asynchronous JavaScript e XML (AJAX) serviço (um serviço que você pode acessar por meio de código JavaScript de um cliente de navegador da Web) sem usar as definições de configuração.</span><span class="sxs-lookup"><span data-stu-id="ce1cb-103">This sample demonstrates how to use [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] to create a basic ASP.NET Asynchronous JavaScript and XML (AJAX) service (a service that you can access by using JavaScript code from a Web browser client) without using any configuration settings.</span></span> <span data-ttu-id="ce1cb-104">O serviço usa a sintaxe especial no arquivo. svc para ativar automaticamente um ponto de extremidade AJAX.</span><span class="sxs-lookup"><span data-stu-id="ce1cb-104">The service uses special syntax in the .svc file to automatically enable an AJAX endpoint.</span></span>  
  
 <span data-ttu-id="ce1cb-105">Suporte do AJAX no [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] é otimizado para uso com o ASP.NET AJAX por meio de `ScriptManager` controle.</span><span class="sxs-lookup"><span data-stu-id="ce1cb-105">AJAX support in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] is optimized for use with ASP.NET AJAX through the `ScriptManager` control.</span></span> <span data-ttu-id="ce1cb-106">Para obter um exemplo do uso de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] com o ASP.NET AJAX, consulte o [Ajax exemplos](http://msdn.microsoft.com/en-us/f3fa45b3-44d5-4926-8cc4-a13c30a3bf3e).</span><span class="sxs-lookup"><span data-stu-id="ce1cb-106">For an example of using [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] with ASP.NET AJAX, see the [Ajax Samples](http://msdn.microsoft.com/en-us/f3fa45b3-44d5-4926-8cc4-a13c30a3bf3e).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ce1cb-107">As instruções de procedimento e a compilação de configuração para este exemplo estão localizadas no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="ce1cb-107">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="ce1cb-108">Este exemplo tem como base o AJAX Service usando HTTP POST.</span><span class="sxs-lookup"><span data-stu-id="ce1cb-108">This sample builds upon the AJAX Service Using HTTP POST.</span></span> <span data-ttu-id="ce1cb-109">Conforme descrito no [serviço AJAX básico](../../../../docs/framework/wcf/samples/basic-ajax-service.md) exemplo, <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> é usado para hospedar o serviço.</span><span class="sxs-lookup"><span data-stu-id="ce1cb-109">As described in the [Basic AJAX Service](../../../../docs/framework/wcf/samples/basic-ajax-service.md) sample, <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> is used to host the service.</span></span>  
  
```  
<%ServiceHost  
    language=c#  
    Debug="true"  
    Service="Microsoft.Ajax.Samples.CalculatorService  
    Factory="System.ServiceModel.Activation.WebScriptServiceHostFactory"  
%>  
```  
  
 <span data-ttu-id="ce1cb-110"><xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>adiciona automaticamente um <xref:System.ServiceModel.Description.WebScriptEndpoint> para o serviço.</span><span class="sxs-lookup"><span data-stu-id="ce1cb-110"><xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> automatically adds a <xref:System.ServiceModel.Description.WebScriptEndpoint> to the service.</span></span> <span data-ttu-id="ce1cb-111">Se nenhuma alteração na configuração precisa ser feitas para o ponto de extremidade, o \<sistema. ServiceModel > seção pode ser completamente removida do arquivo Web. config para o serviço.</span><span class="sxs-lookup"><span data-stu-id="ce1cb-111">If no configuration changes need to be made to the endpoint, the \<system.ServiceModel> section can be completely removed from the Web.config file for the service.</span></span> <span data-ttu-id="ce1cb-112">O arquivo Web. config contém algumas configurações do ASP.NET, que são usadas pelo ConfigFreeClientPage.aspx.</span><span class="sxs-lookup"><span data-stu-id="ce1cb-112">The Web.config file contains some ASP.NET settings, which are used by ConfigFreeClientPage.aspx.</span></span> <span data-ttu-id="ce1cb-113">Se não fosse esse o caso, todo o arquivo Web. config foi removido.</span><span class="sxs-lookup"><span data-stu-id="ce1cb-113">If that were not the case, the entire Web.config file could be removed.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="ce1cb-114">Os exemplos podem mais ser instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="ce1cb-114">The samples may already be installed on your computer.</span></span> <span data-ttu-id="ce1cb-115">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="ce1cb-115">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="ce1cb-116">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="ce1cb-116">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="ce1cb-117">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="ce1cb-117">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\ConfigFreeAjaxService`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="ce1cb-118">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="ce1cb-118">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="ce1cb-119">Certifique-se de que você execute as instruções de instalação em [único procedimento de instalação para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ce1cb-119">Ensure that you perform the setup instructions in [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="ce1cb-120">Compile a solução ConfigFreeAjaxService.sln conforme descrito em [compilar os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ce1cb-120">Build the solution ConfigFreeAjaxService.sln as described in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="ce1cb-121">Navegue até http://localhost/ServiceModelSamples/ConfigFreeClientPage.aspx (não abrir ConfigFreeClientPage.aspx no navegador de dentro do diretório do projeto).</span><span class="sxs-lookup"><span data-stu-id="ce1cb-121">Navigate to http://localhost/ServiceModelSamples/ConfigFreeClientPage.aspx (do not open ConfigFreeClientPage.aspx in the browser from within the project directory).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ce1cb-122">Ao executar este exemplo, certifique-se de que a autenticação anônima e autenticação do Windows não estão habilitados simultaneamente para a pasta ServiceModelSamples no IIS.</span><span class="sxs-lookup"><span data-stu-id="ce1cb-122">When running this sample, please ensure that Anonymous Authentication and Windows Authentication are not enabled simultaneously for the ServiceModelSamples folder in IIS.</span></span> <span data-ttu-id="ce1cb-123">Se esse for o caso, desative a autenticação do Windows.</span><span class="sxs-lookup"><span data-stu-id="ce1cb-123">If that is the case, please disable Windows Authentication.</span></span> <span data-ttu-id="ce1cb-124">Depois de executar o exemplo, habilitar a autenticação do Windows e execute "iisreset".</span><span class="sxs-lookup"><span data-stu-id="ce1cb-124">Once you have run the sample, enable Windows Authentication and run "iisreset".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce1cb-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ce1cb-125">See Also</span></span>  
 [<span data-ttu-id="ce1cb-126">Serviço AJAX básico</span><span class="sxs-lookup"><span data-stu-id="ce1cb-126">Basic AJAX Service</span></span>](../../../../docs/framework/wcf/samples/basic-ajax-service.md)
