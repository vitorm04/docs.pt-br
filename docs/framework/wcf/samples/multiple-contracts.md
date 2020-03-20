---
title: Vários contratos
ms.date: 03/30/2017
ms.assetid: 2bef319b-fe9c-4d49-ac6c-dfb23eb35099
ms.openlocfilehash: ed59803b867dfe7994aceea010aa656c53927a0c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144338"
---
# <a name="multiple-contracts"></a><span data-ttu-id="4fbba-102">Vários contratos</span><span class="sxs-lookup"><span data-stu-id="4fbba-102">Multiple Contracts</span></span>
<span data-ttu-id="4fbba-103">A amostra de Contratos Múltiplos demonstra como implementar mais de um contrato em um serviço e como configurar pontos finais para se comunicar com cada um dos contratos implementados.</span><span class="sxs-lookup"><span data-stu-id="4fbba-103">The Multiple Contracts sample demonstrates how to implement more than one contract on a service and how to configure endpoints for communicating with each of the implemented contracts.</span></span> <span data-ttu-id="4fbba-104">Esta amostra é baseada no [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="4fbba-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span> <span data-ttu-id="4fbba-105">O serviço foi modificado para definir `ICalculator` dois `ICalculatorSession` contratos, o contrato e o contrato.</span><span class="sxs-lookup"><span data-stu-id="4fbba-105">The service has been modified to define two contracts, the `ICalculator` contract and the `ICalculatorSession` contract.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4fbba-106">O procedimento de configuração e as instruções de construção desta amostra estão localizados no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="4fbba-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="4fbba-107">A classe de serviços implementa tanto os `ICalculator` contratos quanto `ICalculatorSession` os contratos.</span><span class="sxs-lookup"><span data-stu-id="4fbba-107">The service class implements both the `ICalculator` and `ICalculatorSession` contracts.</span></span> <span data-ttu-id="4fbba-108">Como um dos contratos requer uma sessão, o serviço usa o <xref:System.ServiceModel.InstanceContextMode.PerSession> modo instância para manter o estado durante a vida útil da sessão.</span><span class="sxs-lookup"><span data-stu-id="4fbba-108">Because one of the contracts requires a session, the service uses the <xref:System.ServiceModel.InstanceContextMode.PerSession> instance mode to maintain the state over the lifetime of the session.</span></span>  
  
 <span data-ttu-id="4fbba-109">A configuração do serviço foi modificada para definir dois pontos finais para expor cada contrato.</span><span class="sxs-lookup"><span data-stu-id="4fbba-109">The service configuration has been modified to define two endpoints to expose each contract.</span></span> <span data-ttu-id="4fbba-110">O `ICalculator` ponto final é exposto no `basicHttpBinding`endereço base usando um .</span><span class="sxs-lookup"><span data-stu-id="4fbba-110">The `ICalculator` endpoint is exposed at the base address using a `basicHttpBinding`.</span></span> <span data-ttu-id="4fbba-111">O `ICalculatorSession` ponto final é exposto no endereço `wsHttpBinding` base/sessão usando um com o atributo `bindingConfiguration` definido para `BindingWithSession`, como mostrado na configuração da amostra a seguir.</span><span class="sxs-lookup"><span data-stu-id="4fbba-111">The `ICalculatorSession` endpoint is exposed at the baseaddress/session using a `wsHttpBinding` with the `bindingConfiguration` attribute set to `BindingWithSession`, as shown in the following sample configuration.</span></span>  
  
```xml  
<service
    name="Microsoft.ServiceModel.Samples.CalculatorService"  
    behaviorConfiguration="CalculatorServiceBehavior">  
  <!-- ICalculator endpoint is exposed using BasicBinding at the base  
       address provided by host:   
       http://localhost/servicemodelsamples/service.svc  -->  
  <endpoint address=""  
            binding="basicHttpBinding"  
            contract="Microsoft.ServiceModel.Samples.ICalculator" />  
  <!-- ICalculatorSession endpoint is exposed using BindingWithSession  
       at {baseaddress}/session:  
       http://localhost/servicemodelsamples/service.svc/session -->  
  <endpoint address="session"  
            binding="wsHttpBinding"  
            bindingConfiguration="BindingWithSession"
           contract="Microsoft.ServiceModel.Samples.ICalculatorSession" />  
  ...  
</service>  
```  
  
 <span data-ttu-id="4fbba-112">O código do cliente gerado agora inclui `ICalculator` uma classe `ICalculatorSession` cliente tanto para o contrato original quanto para o novo contrato.</span><span class="sxs-lookup"><span data-stu-id="4fbba-112">The generated client code now includes a client class for both the original `ICalculator` contract and the new `ICalculatorSession` contract.</span></span> <span data-ttu-id="4fbba-113">A configuração e o código do cliente foram modificados para se comunicar com cada contrato no ponto final de serviço apropriado.</span><span class="sxs-lookup"><span data-stu-id="4fbba-113">The client configuration and code have been modified to communicate with each contract at the appropriate service endpoint.</span></span>  
  
 <span data-ttu-id="4fbba-114">O cliente é um aplicativo de janelas de console (.exe).</span><span class="sxs-lookup"><span data-stu-id="4fbba-114">The client is a console windows application (.exe).</span></span> <span data-ttu-id="4fbba-115">O serviço é hospedado pelos Serviços de Informação da Internet (IIS).</span><span class="sxs-lookup"><span data-stu-id="4fbba-115">The service is hosted by Internet Information Services (IIS).</span></span>  
  
 <span data-ttu-id="4fbba-116">A janela do console cliente exibe as operações enviadas para cada um dos pontos finais, primeiro o ponto final básico, seguido pelo ponto final seguro.</span><span class="sxs-lookup"><span data-stu-id="4fbba-116">The client console window displays the operations sent to each of the endpoints, first the basic endpoint, followed by the secure endpoint.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="4fbba-117">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="4fbba-117">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="4fbba-118">Certifique-se de que você tenha realizado o [procedimento de configuração única para as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="4fbba-118">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="4fbba-119">Para construir a edição C# ou Visual Basic .NET da solução, siga as instruções em [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="4fbba-119">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="4fbba-120">Para executar a amostra em uma configuração de máquina única ou cruzada, siga as instruções em [Executar as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="4fbba-120">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="4fbba-121">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="4fbba-121">The samples may already be installed on your machine.</span></span> <span data-ttu-id="4fbba-122">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="4fbba-122">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="4fbba-123">Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation).</span><span class="sxs-lookup"><span data-stu-id="4fbba-123">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="4fbba-124">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="4fbba-124">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\MultipleContracts`  
