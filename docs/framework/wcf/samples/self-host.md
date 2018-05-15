---
title: Self-Host
ms.date: 03/30/2017
helpviewer_keywords:
- Self hosted service
- Self Host Sample [Windows Communication Foundation]
ms.assetid: 05e68661-1ddf-4abf-a899-9bb1b8272a5b
ms.openlocfilehash: d4fc6c55f0eb528e6ae8d19d733c67d7f7ce135f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="self-host"></a><span data-ttu-id="92a22-102">Self-Host</span><span class="sxs-lookup"><span data-stu-id="92a22-102">Self-Host</span></span>
<span data-ttu-id="92a22-103">Este exemplo demonstra como implementar um serviço hospedado automaticamente em um aplicativo de console.</span><span class="sxs-lookup"><span data-stu-id="92a22-103">This sample demonstrates how to implement a self-hosted service in a console application.</span></span> <span data-ttu-id="92a22-104">Este exemplo se baseia o [Introdução](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="92a22-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span> <span data-ttu-id="92a22-105">O arquivo de configuração do serviço foi renomeado de Web. config para o App. config e modificado para configurar um endereço base, o host usa.</span><span class="sxs-lookup"><span data-stu-id="92a22-105">The service configuration file has been renamed from Web.config to App.config and modified to configure a base address, which the host uses.</span></span> <span data-ttu-id="92a22-106">O código de origem do serviço foi modificado para implementar um estático `Main` função que cria e abre um host de serviço que fornece o endereço base configurado.</span><span class="sxs-lookup"><span data-stu-id="92a22-106">The service source code has been modified to implement a static `Main` function that creates and opens a service host that provides the configured base address.</span></span> <span data-ttu-id="92a22-107">A implementação do serviço foi modificada para gravar a saída para o console para cada operação.</span><span class="sxs-lookup"><span data-stu-id="92a22-107">The service implementation has been modified to write output to the console for each operation.</span></span> <span data-ttu-id="92a22-108">O cliente está inalterado, exceto para a configuração do endereço de ponto de extremidade correto do serviço.</span><span class="sxs-lookup"><span data-stu-id="92a22-108">The client has been unmodified, except for configuring the correct endpoint address of the service.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="92a22-109">As instruções de procedimento e a compilação de configuração para este exemplo estão localizadas no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="92a22-109">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="92a22-110">O exemplo implementa uma função estática principal para criar um <xref:System.ServiceModel.ServiceHost> para o determinado `CalculatorService` tipo, conforme mostrado no código de exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="92a22-110">The sample implements a static main function to create a <xref:System.ServiceModel.ServiceHost> for the given `CalculatorService` type, as shown in the following sample code.</span></span>  
  
```  
// Host the service within this EXE console application.  
public static void Main()  
{  
    // Create a ServiceHost for the CalculatorService type.  
    using (ServiceHost serviceHost =   
           new ServiceHost(typeof(CalculatorService)))  
    {  
        // Open the ServiceHost to create listeners   
        // and start listening for messages.  
        serviceHost.Open();  
  
        // The service can now be accessed.  
        Console.WriteLine("The service is ready.");  
        Console.WriteLine("Press <ENTER> to terminate service.");  
        Console.WriteLine();  
        Console.ReadLine();  
    }  
}  
```  
  
 <span data-ttu-id="92a22-111">Quando um serviço é hospedado no Internet Information Services (IIS) ou o serviço de ativação de processos do Windows (WAS), o endereço base do serviço é fornecido pelo ambiente de hospedagem.</span><span class="sxs-lookup"><span data-stu-id="92a22-111">When a service is hosted in Internet Information Services (IIS) or Windows Process Activation Service (WAS), the base address of the service is provided by the hosting environment.</span></span> <span data-ttu-id="92a22-112">No caso de hospedagem interna, você deve especificar o endereço base, por conta própria.</span><span class="sxs-lookup"><span data-stu-id="92a22-112">In the self-hosted case, you must specify the base address yourself.</span></span> <span data-ttu-id="92a22-113">Isso é feito usando o `add` elemento, o filho de [ \<baseAddresses >](../../../../docs/framework/configure-apps/file-schema/wcf/baseaddresses.md), filho de [ \<host >](../../../../docs/framework/configure-apps/file-schema/wcf/host.md), filho de [ \<serviço > ](../../../../docs/framework/configure-apps/file-schema/wcf/service.md) conforme demonstrado no exemplo de configuração.</span><span class="sxs-lookup"><span data-stu-id="92a22-113">This is done using the `add` element, child of [\<baseAddresses>](../../../../docs/framework/configure-apps/file-schema/wcf/baseaddresses.md), child of [\<host>](../../../../docs/framework/configure-apps/file-schema/wcf/host.md), child of [\<service>](../../../../docs/framework/configure-apps/file-schema/wcf/service.md) as demonstrated in the following sample configuration.</span></span>  
  
```xml  
<service   
    name="Microsoft.ServiceModel.Samples.CalculatorService"  
    behaviorConfiguration="CalculatorServiceBehavior">  
  <host>  
    <baseAddresses>  
      <add baseAddress="http://localhost:8000/ServiceModelSamples/service"/>  
    </baseAddresses>  
  </host>  
  ...  
</service>  
```  
  
 <span data-ttu-id="92a22-114">Quando você executar o exemplo, as respostas e solicitações de operação são exibidas em janelas do console de serviço e o cliente.</span><span class="sxs-lookup"><span data-stu-id="92a22-114">When you run the sample, the operation requests and responses are displayed in both the service and client console windows.</span></span> <span data-ttu-id="92a22-115">Pressione ENTER em cada janela de console para desligar o serviço e o cliente.</span><span class="sxs-lookup"><span data-stu-id="92a22-115">Press ENTER in each console window to shut down the service and client.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="92a22-116">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="92a22-116">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="92a22-117">Certifique-se de que você executou o [único procedimento de instalação para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="92a22-117">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="92a22-118">Para compilar o c# ou Visual Basic .NET edição da solução, siga as instruções em [compilar os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="92a22-118">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="92a22-119">Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="92a22-119">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="92a22-120">Os exemplos podem mais ser instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="92a22-120">The samples may already be installed on your computer.</span></span> <span data-ttu-id="92a22-121">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="92a22-121">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="92a22-122">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="92a22-122">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="92a22-123">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="92a22-123">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\SelfHost`  
  
## <a name="see-also"></a><span data-ttu-id="92a22-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="92a22-124">See Also</span></span>  
 [<span data-ttu-id="92a22-125">Exemplos de persistência e hospedagem de AppFabric</span><span class="sxs-lookup"><span data-stu-id="92a22-125">AppFabric Hosting and Persistence Samples</span></span>](http://go.microsoft.com/fwlink/?LinkId=193961)
