---
title: Vários contratos
ms.date: 03/30/2017
ms.assetid: 2bef319b-fe9c-4d49-ac6c-dfb23eb35099
ms.openlocfilehash: 257b3f7946a7185cdb82bda88e64e543afa85707
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70039199"
---
# <a name="multiple-contracts"></a><span data-ttu-id="90bef-102">Vários contratos</span><span class="sxs-lookup"><span data-stu-id="90bef-102">Multiple Contracts</span></span>
<span data-ttu-id="90bef-103">O exemplo de vários contratos demonstra como implementar mais de um contrato em um serviço e como configurar pontos de extremidade para se comunicar com cada um dos contratos implementados.</span><span class="sxs-lookup"><span data-stu-id="90bef-103">The Multiple Contracts sample demonstrates how to implement more than one contract on a service and how to configure endpoints for communicating with each of the implemented contracts.</span></span> <span data-ttu-id="90bef-104">Este exemplo é baseado na [introdução](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="90bef-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span> <span data-ttu-id="90bef-105">O serviço foi modificado para definir dois contratos, o `ICalculator` contrato e o `ICalculatorSession` contrato.</span><span class="sxs-lookup"><span data-stu-id="90bef-105">The service has been modified to define two contracts, the `ICalculator` contract and the `ICalculatorSession` contract.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="90bef-106">O procedimento de instalação e as instruções de Build para este exemplo estão localizados no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="90bef-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="90bef-107">A classe de serviço implementa os `ICalculator` contratos `ICalculatorSession` e.</span><span class="sxs-lookup"><span data-stu-id="90bef-107">The service class implements both the `ICalculator` and `ICalculatorSession` contracts.</span></span> <span data-ttu-id="90bef-108">Como um dos contratos requer uma sessão, o serviço usa o <xref:System.ServiceModel.InstanceContextMode.PerSession> modo de instância para manter o estado durante o tempo de vida da sessão.</span><span class="sxs-lookup"><span data-stu-id="90bef-108">Because one of the contracts requires a session, the service uses the <xref:System.ServiceModel.InstanceContextMode.PerSession> instance mode to maintain the state over the lifetime of the session.</span></span>  
  
 <span data-ttu-id="90bef-109">A configuração de serviço foi modificada para definir dois pontos de extremidade para expor cada contrato.</span><span class="sxs-lookup"><span data-stu-id="90bef-109">The service configuration has been modified to define two endpoints to expose each contract.</span></span> <span data-ttu-id="90bef-110">O `ICalculator` ponto de extremidade é exposto no endereço base usando `basicHttpBinding`um.</span><span class="sxs-lookup"><span data-stu-id="90bef-110">The `ICalculator` endpoint is exposed at the base address using a `basicHttpBinding`.</span></span> <span data-ttu-id="90bef-111">O `ICalculatorSession` ponto de extremidade é exposto no BaseAddress/Session usando `wsHttpBinding` um `BindingWithSession`com `bindingConfiguration` o atributo definido como, conforme mostrado na seguinte configuração de exemplo.</span><span class="sxs-lookup"><span data-stu-id="90bef-111">The `ICalculatorSession` endpoint is exposed at the baseaddress/session using a `wsHttpBinding` with the `bindingConfiguration` attribute set to `BindingWithSession`, as shown in the following sample configuration.</span></span>  
  
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
  
 <span data-ttu-id="90bef-112">O código do cliente gerado agora inclui uma classe de cliente para o `ICalculator` contrato original e para `ICalculatorSession` o novo contrato.</span><span class="sxs-lookup"><span data-stu-id="90bef-112">The generated client code now includes a client class for both the original `ICalculator` contract and the new `ICalculatorSession` contract.</span></span> <span data-ttu-id="90bef-113">A configuração do cliente e o código foram modificados para se comunicar com cada contrato no ponto de extremidade de serviço apropriado.</span><span class="sxs-lookup"><span data-stu-id="90bef-113">The client configuration and code have been modified to communicate with each contract at the appropriate service endpoint.</span></span>  
  
 <span data-ttu-id="90bef-114">O cliente é um aplicativo do Windows do console (. exe).</span><span class="sxs-lookup"><span data-stu-id="90bef-114">The client is a console windows application (.exe).</span></span> <span data-ttu-id="90bef-115">O serviço é hospedado pelo Serviços de Informações da Internet (IIS).</span><span class="sxs-lookup"><span data-stu-id="90bef-115">The service is hosted by Internet Information Services (IIS).</span></span>  
  
 <span data-ttu-id="90bef-116">A janela do console do cliente exibe as operações enviadas para cada um dos pontos de extremidade, primeiro o ponto final básico, seguido pelo ponto de extremidade seguro.</span><span class="sxs-lookup"><span data-stu-id="90bef-116">The client console window displays the operations sent to each of the endpoints, first the basic endpoint, followed by the secure endpoint.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="90bef-117">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="90bef-117">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="90bef-118">Verifique se você executou o [procedimento de configuração única para os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="90bef-118">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="90bef-119">Para compilar a C# edição do ou Visual Basic .NET da solução, siga as instruções em [criando os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="90bef-119">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="90bef-120">Para executar o exemplo em uma configuração de computador único ou cruzado, siga as instruções em [executando os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="90bef-120">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="90bef-121">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="90bef-121">The samples may already be installed on your machine.</span></span> <span data-ttu-id="90bef-122">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="90bef-122">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="90bef-123">Se esse diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos de Windows Workflow Foundation (WF) para .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) [!INCLUDE[wf1](../../../../includes/wf1-md.md)] e exemplos.</span><span class="sxs-lookup"><span data-stu-id="90bef-123">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="90bef-124">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="90bef-124">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\MultipleContracts`  
