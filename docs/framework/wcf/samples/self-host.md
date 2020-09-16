---
title: Self-Host
ms.date: 03/30/2017
helpviewer_keywords:
- Self hosted service
- Self Host Sample [Windows Communication Foundation]
ms.assetid: 05e68661-1ddf-4abf-a899-9bb1b8272a5b
ms.openlocfilehash: 544ae8c0bc88d49c281810714225dbadecfd443b
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90558401"
---
# <a name="self-host"></a><span data-ttu-id="73b5b-102">Self-Host</span><span class="sxs-lookup"><span data-stu-id="73b5b-102">Self-Host</span></span>
<span data-ttu-id="73b5b-103">Este exemplo demonstra como implementar um serviço hospedado automaticamente em um aplicativo de console.</span><span class="sxs-lookup"><span data-stu-id="73b5b-103">This sample demonstrates how to implement a self-hosted service in a console application.</span></span> <span data-ttu-id="73b5b-104">Este exemplo é baseado na [introdução](getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="73b5b-104">This sample is based on the [Getting Started](getting-started-sample.md).</span></span> <span data-ttu-id="73b5b-105">O arquivo de configuração de serviço foi renomeado de Web.config para App.config e modificado para configurar um endereço base, que o host usa.</span><span class="sxs-lookup"><span data-stu-id="73b5b-105">The service configuration file has been renamed from Web.config to App.config and modified to configure a base address, which the host uses.</span></span> <span data-ttu-id="73b5b-106">O código-fonte do serviço foi modificado para implementar uma `Main` função estática que cria e abre um host de serviço que fornece o endereço base configurado.</span><span class="sxs-lookup"><span data-stu-id="73b5b-106">The service source code has been modified to implement a static `Main` function that creates and opens a service host that provides the configured base address.</span></span> <span data-ttu-id="73b5b-107">A implementação do serviço foi modificada para gravar a saída no console para cada operação.</span><span class="sxs-lookup"><span data-stu-id="73b5b-107">The service implementation has been modified to write output to the console for each operation.</span></span> <span data-ttu-id="73b5b-108">O cliente não foi modificado, exceto para configurar o endereço do ponto de extremidade correto do serviço.</span><span class="sxs-lookup"><span data-stu-id="73b5b-108">The client has been unmodified, except for configuring the correct endpoint address of the service.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="73b5b-109">O procedimento de instalação e as instruções de Build para este exemplo estão localizados no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="73b5b-109">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="73b5b-110">O exemplo implementa uma função principal estática para criar um <xref:System.ServiceModel.ServiceHost> para o `CalculatorService` tipo fornecido, conforme mostrado no código de exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="73b5b-110">The sample implements a static main function to create a <xref:System.ServiceModel.ServiceHost> for the given `CalculatorService` type, as shown in the following sample code.</span></span>  
  
```csharp
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
  
 <span data-ttu-id="73b5b-111">Quando um serviço é hospedado no Serviços de Informações da Internet (IIS) ou no WAS (serviço de ativação de processos do Windows), o endereço base do serviço é fornecido pelo ambiente de hospedagem.</span><span class="sxs-lookup"><span data-stu-id="73b5b-111">When a service is hosted in Internet Information Services (IIS) or Windows Process Activation Service (WAS), the base address of the service is provided by the hosting environment.</span></span> <span data-ttu-id="73b5b-112">No caso do auto-hospedado, você deve especificar o endereço base por conta própria.</span><span class="sxs-lookup"><span data-stu-id="73b5b-112">In the self-hosted case, you must specify the base address yourself.</span></span> <span data-ttu-id="73b5b-113">Isso é feito usando o `add` elemento, filho de [\<baseAddresses>](../../configure-apps/file-schema/wcf/baseaddresses.md) , filho de [\<host>](../../configure-apps/file-schema/wcf/host.md) , filho de, [\<service>](../../configure-apps/file-schema/wcf/service.md) conforme demonstrado na configuração de exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="73b5b-113">This is done using the `add` element, child of [\<baseAddresses>](../../configure-apps/file-schema/wcf/baseaddresses.md), child of [\<host>](../../configure-apps/file-schema/wcf/host.md), child of [\<service>](../../configure-apps/file-schema/wcf/service.md) as demonstrated in the following sample configuration.</span></span>  
  
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
  
 <span data-ttu-id="73b5b-114">Quando você executa o exemplo, as solicitações e respostas da operação são exibidas nas janelas do console do cliente e do serviço.</span><span class="sxs-lookup"><span data-stu-id="73b5b-114">When you run the sample, the operation requests and responses are displayed in both the service and client console windows.</span></span> <span data-ttu-id="73b5b-115">Pressione ENTER em cada janela do console para desligar o serviço e o cliente.</span><span class="sxs-lookup"><span data-stu-id="73b5b-115">Press ENTER in each console window to shut down the service and client.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="73b5b-116">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="73b5b-116">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="73b5b-117">Verifique se você executou o [procedimento de configuração única para os exemplos de Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="73b5b-117">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="73b5b-118">Para criar a edição C# ou Visual Basic .NET da solução, siga as instruções em [criando os exemplos de Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="73b5b-118">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="73b5b-119">Para executar o exemplo em uma configuração de computador único ou entre computadores, siga as instruções em [executando os exemplos de Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="73b5b-119">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="73b5b-120">Os exemplos podem mais ser instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="73b5b-120">The samples may already be installed on your computer.</span></span> <span data-ttu-id="73b5b-121">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="73b5b-121">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="73b5b-122">Se esse diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos de Windows Workflow Foundation (WF) para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="73b5b-122">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="73b5b-123">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="73b5b-123">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\SelfHost`  
  
## <a name="see-also"></a><span data-ttu-id="73b5b-124">Confira também</span><span class="sxs-lookup"><span data-stu-id="73b5b-124">See also</span></span>

- <span data-ttu-id="73b5b-125">[Hospedagem de AppFabric e persistência Exemplos](/previous-versions/appfabric/ff383418(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="73b5b-125">[AppFabric Hosting and Persistence Samples](/previous-versions/appfabric/ff383418(v=azure.10))</span></span>
