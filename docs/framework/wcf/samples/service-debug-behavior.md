---
title: "Comportamento de depuração de serviço"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9d8fd3fb-dc39-427a-8235-336a7e7162ba
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 007ce7eeae6022255ad1b31921e14e0518d72bee
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="service-debug-behavior"></a><span data-ttu-id="14d67-102">Comportamento de depuração de serviço</span><span class="sxs-lookup"><span data-stu-id="14d67-102">Service Debug Behavior</span></span>
<span data-ttu-id="14d67-103">Este exemplo demonstra como as configurações de comportamento de serviço podem ser configuradas.</span><span class="sxs-lookup"><span data-stu-id="14d67-103">This sample demonstrates how service debug behavior settings can be configured.</span></span> <span data-ttu-id="14d67-104">O exemplo se baseia o [Introdução](../../../../docs/framework/wcf/samples/getting-started-sample.md), que implementa o `ICalculator` contrato de serviço.</span><span class="sxs-lookup"><span data-stu-id="14d67-104">The sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md), which implements the `ICalculator` service contract.</span></span> <span data-ttu-id="14d67-105">Este exemplo define explicitamente o comportamento de depuração de serviço no arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="14d67-105">This sample explicitly defines service debug behavior in the configuration file.</span></span> <span data-ttu-id="14d67-106">Ele também pode ser feito imperativa no código.</span><span class="sxs-lookup"><span data-stu-id="14d67-106">It can also be done imperatively in code.</span></span>  
  
 <span data-ttu-id="14d67-107">Neste exemplo, o cliente é um aplicativo de console (.exe) e o serviço é hospedado por serviços de informações da Internet (IIS).</span><span class="sxs-lookup"><span data-stu-id="14d67-107">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="14d67-108">As instruções de procedimento e a compilação de configuração para este exemplo estão localizadas no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="14d67-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="14d67-109">O arquivo Web. config para o servidor define o comportamento de depuração de serviço para habilitar a página de Ajuda e o tratamento de exceções, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="14d67-109">The Web.config file for the server defines the service debug behavior to enable the help page and exception handling as shown in the following sample.</span></span>  
  
```xml  
<behaviors>  
     <serviceBehaviors>  
         <behavior name="CalculatorServiceBehavior">  
         <!-- WARNING: Setting includeExceptionDetailInFaults = "True" could result in leaking secured server information to the client.-->  
         <!-- Please set this to false when deploying -->  
             <serviceDebug includeExceptionDetailInFaults="True" httpHelpPageEnabled="True"/>  
         </behavior>  
     </serviceBehaviors>  
</behaviors>  
```  
  
 <span data-ttu-id="14d67-110">[\<serviceDebug >](../../../../docs/framework/configure-apps/file-schema/wcf/servicedebug.md) é o elemento de configuração que permite alterar as propriedades de comportamento de depuração do serviço.</span><span class="sxs-lookup"><span data-stu-id="14d67-110">[\<serviceDebug>](../../../../docs/framework/configure-apps/file-schema/wcf/servicedebug.md) is the configuration element that allows changing the service debug behavior properties.</span></span> <span data-ttu-id="14d67-111">O usuário pode modificar esse comportamento para realizar o seguinte:</span><span class="sxs-lookup"><span data-stu-id="14d67-111">The user can modify this behavior to achieve the following:</span></span>  
  
-   <span data-ttu-id="14d67-112">Isso permite que o serviço retornar qualquer exceção que é lançada pelo código do aplicativo, mesmo se a exceção não é declarada usando a <xref:System.ServiceModel.FaultContractAttribute>.</span><span class="sxs-lookup"><span data-stu-id="14d67-112">This allows the service to return any exception that is thrown by the application code even if the exception is not declared using the <xref:System.ServiceModel.FaultContractAttribute>.</span></span> <span data-ttu-id="14d67-113">Isso é feito definindo `includeExceptionDetailInFaults` para `true`.</span><span class="sxs-lookup"><span data-stu-id="14d67-113">It is done by setting `includeExceptionDetailInFaults` to `true`.</span></span> <span data-ttu-id="14d67-114">Essa configuração é útil durante a depuração de casos em que o servidor está lançando uma exceção inesperada.</span><span class="sxs-lookup"><span data-stu-id="14d67-114">This setting is useful when debugging cases where the server is throwing an unexpected exception.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="14d67-115">Não é seguro para ativar essa configuração em um ambiente de produção.</span><span class="sxs-lookup"><span data-stu-id="14d67-115">It is not secure to turn this setting on in a production environment.</span></span> <span data-ttu-id="14d67-116">Uma exceção inesperada do servidor pode ter algumas informações que não são destinadas para o cliente e, portanto definindo `includeExceptionDetailsInFaults` para `true` pode resultar em um vazamento de informação.</span><span class="sxs-lookup"><span data-stu-id="14d67-116">An unexpected server exception may have some information that is not intended for the client and so setting `includeExceptionDetailsInFaults` to `true` might result in an information leak.</span></span>  
  
-   <span data-ttu-id="14d67-117">O [ \<serviceDebug >](../../../../docs/framework/configure-apps/file-schema/wcf/servicedebug.md) também permite que um usuário habilitar ou desabilitar a página de Ajuda.</span><span class="sxs-lookup"><span data-stu-id="14d67-117">The [\<serviceDebug>](../../../../docs/framework/configure-apps/file-schema/wcf/servicedebug.md) also allows a user to enable or disable the help page.</span></span> <span data-ttu-id="14d67-118">Cada serviço opcionalmente pode expor uma página de Ajuda que contém informações sobre o serviço, incluindo o ponto de extremidade para obter o WSDL para o serviço.</span><span class="sxs-lookup"><span data-stu-id="14d67-118">Each service can optionally expose a help page that contains information about the service including the endpoint to get WSDL for the service.</span></span> <span data-ttu-id="14d67-119">Isso pode ser habilitado definindo `httpHelpPageEnabled` para `true`.</span><span class="sxs-lookup"><span data-stu-id="14d67-119">This can be enabled by setting `httpHelpPageEnabled` to `true`.</span></span> <span data-ttu-id="14d67-120">Isso permite que a página de ajuda a ser retornado para uma solicitação GET para o endereço base do serviço.</span><span class="sxs-lookup"><span data-stu-id="14d67-120">This enables the help page to be returned to a GET request to the base address of the service.</span></span> <span data-ttu-id="14d67-121">Você pode alterar esse endereço, definindo outro atributo `httpHelpPageUrl`.</span><span class="sxs-lookup"><span data-stu-id="14d67-121">You can change this address by setting another attribute `httpHelpPageUrl`.</span></span> <span data-ttu-id="14d67-122">Você pode fazer isso segura usando HTTPS em vez de HTTP.</span><span class="sxs-lookup"><span data-stu-id="14d67-122">You can make this secure by using HTTPS instead of HTTP.</span></span> <span data-ttu-id="14d67-123">Isso pode ser feito definindo `httpsHelpPageEnabled` e `httpsHelpPageUrl`.</span><span class="sxs-lookup"><span data-stu-id="14d67-123">This can be done by setting `httpsHelpPageEnabled` and `httpsHelpPageUrl`.</span></span>  
  
 <span data-ttu-id="14d67-124">Quando você executar o exemplo, as respostas e solicitações de operação são exibidas na janela do console do cliente.</span><span class="sxs-lookup"><span data-stu-id="14d67-124">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="14d67-125">As três primeiras operações (Adicionar, subtrair e multiplique) deve ter êxito.</span><span class="sxs-lookup"><span data-stu-id="14d67-125">The first three operations (Add, Subtract and Multiply) must succeed.</span></span> <span data-ttu-id="14d67-126">A última operação ("divisão") falhará com uma divisão por zero exceção.</span><span class="sxs-lookup"><span data-stu-id="14d67-126">The last operation ("divide") fails with a division by zero exception.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="14d67-127">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="14d67-127">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="14d67-128">Certifique-se de que você executou o [único procedimento de instalação para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="14d67-128">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="14d67-129">Para compilar o c# ou Visual Basic .NET edição da solução, siga as instruções em [compilar os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="14d67-129">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="14d67-130">Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="14d67-130">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="14d67-131">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="14d67-131">The samples may already be installed on your machine.</span></span> <span data-ttu-id="14d67-132">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="14d67-132">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="14d67-133">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="14d67-133">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="14d67-134">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="14d67-134">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\ServiceDebug`  
  
## <a name="see-also"></a><span data-ttu-id="14d67-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="14d67-135">See Also</span></span>
