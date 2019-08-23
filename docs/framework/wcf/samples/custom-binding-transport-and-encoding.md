---
title: Codificação e transporte de associação personalizado
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6c0b353d-79ee-4e61-b348-be49ad0e9a16
ms.openlocfilehash: 83b6f98ca889d4f80841b629d7a958401bac1e87
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69953746"
---
# <a name="custom-binding-transport-and-encoding"></a><span data-ttu-id="cf32e-102">Codificação e transporte de associação personalizado</span><span class="sxs-lookup"><span data-stu-id="cf32e-102">Custom Binding Transport and Encoding</span></span>
<span data-ttu-id="cf32e-103">Uma associação personalizada é definida por uma lista ordenada de elementos de associação discretos.</span><span class="sxs-lookup"><span data-stu-id="cf32e-103">A custom binding is defined by an ordered list of discrete binding elements.</span></span> <span data-ttu-id="cf32e-104">Este exemplo demonstra como configurar uma associação personalizada com vários elementos de codificação de mensagens e transporte.</span><span class="sxs-lookup"><span data-stu-id="cf32e-104">This sample demonstrates how to configure a custom binding with various transport and message encoding elements.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cf32e-105">O procedimento de instalação e as instruções de Build para este exemplo estão localizados no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="cf32e-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="cf32e-106">Este exemplo é baseado no [auto-host](../../../../docs/framework/wcf/samples/self-host.md)e foi modificado para configurar três pontos de extremidade para dar suporte a transportes http, TCP e NamedPipe com associações personalizadas.</span><span class="sxs-lookup"><span data-stu-id="cf32e-106">This sample is based on the [Self-Host](../../../../docs/framework/wcf/samples/self-host.md), and has been modified to configure three endpoints to support HTTP, TCP, and NamedPipe transports with custom bindings.</span></span> <span data-ttu-id="cf32e-107">A configuração do cliente foi modificada da mesma forma e o código do cliente foi alterado para se comunicar com cada um dos três pontos de extremidade.</span><span class="sxs-lookup"><span data-stu-id="cf32e-107">The client configuration was similarly modified, and the client code changed to communicate with each of the three endpoints.</span></span>  
  
 <span data-ttu-id="cf32e-108">O exemplo demonstra como configurar uma ligação personalizada que dá suporte a um transporte e codificação de mensagem específicos.</span><span class="sxs-lookup"><span data-stu-id="cf32e-108">The sample demonstrates a how to configure a custom binding that supports a particular transport and message encoding.</span></span> <span data-ttu-id="cf32e-109">Isso é feito configurando um transporte e uma codificação de mensagem `binding` para o elemento.</span><span class="sxs-lookup"><span data-stu-id="cf32e-109">This is accomplished by configuring a transport and a message encoding for the `binding` element.</span></span> <span data-ttu-id="cf32e-110">A ordenação de elementos de associação é importante na definição de uma associação personalizada, pois cada uma representa uma camada na pilha de canais (consulte [associações personalizadas](../../../../docs/framework/wcf/extending/custom-bindings.md)).</span><span class="sxs-lookup"><span data-stu-id="cf32e-110">The ordering of binding elements is important in defining a custom binding, because each represents a layer in the channel stack (see [Custom Bindings](../../../../docs/framework/wcf/extending/custom-bindings.md)).</span></span> <span data-ttu-id="cf32e-111">Esta amostra configura três associações personalizadas: um transporte HTTP com codificação de texto, um transporte TCP com codificação de texto e um transporte NamedPipe com uma codificação binária.</span><span class="sxs-lookup"><span data-stu-id="cf32e-111">This sample configures three custom bindings: an HTTP transport with text encoding, a TCP transport with text encoding, and a NamedPipe transport with a binary encoding.</span></span>  
  
 <span data-ttu-id="cf32e-112">A configuração de serviço define as associações personalizadas da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="cf32e-112">The service configuration defines the custom bindings as follows:</span></span>  
  
```xml  
<bindings>  
    <customBinding>  
        <binding name="HttpBinding" >  
            <textMessageEncoding   
                messageVersion="Soap12Addressing10"/>  
            <httpTransport />  
        </binding>  
        <binding name="TcpBinding" >  
            <textMessageEncoding />  
            <tcpTransport />  
        </binding>  
        <binding name="NamedPipeBinding" >  
            <binaryMessageEncoding />  
            <namedPipeTransport />  
        </binding>  
    </customBinding>  
</bindings>  
```  
  
 <span data-ttu-id="cf32e-113">Quando você executa o exemplo, as solicitações e respostas da operação são exibidas na janela do console do cliente e do serviço.</span><span class="sxs-lookup"><span data-stu-id="cf32e-113">When you run the sample, the operation requests and responses are displayed in both the service and client console window.</span></span> <span data-ttu-id="cf32e-114">O cliente se comunica com cada um dos três pontos de extremidade, acessando primeiro HTTP, depois TCP e, por fim, NamedPipe.</span><span class="sxs-lookup"><span data-stu-id="cf32e-114">The client communicates with each of the three endpoints, accessing first HTTP, then TCP, and finally NamedPipe.</span></span> <span data-ttu-id="cf32e-115">Pressione ENTER em cada janela do console para desligar o serviço e o cliente.</span><span class="sxs-lookup"><span data-stu-id="cf32e-115">Press ENTER in each console window to shut down the service and client.</span></span>  
  
 <span data-ttu-id="cf32e-116">A `namedPipeTransport` associação não oferece suporte a operações de máquina a máquina.</span><span class="sxs-lookup"><span data-stu-id="cf32e-116">The `namedPipeTransport` binding does not support machine-to-machine operations.</span></span> <span data-ttu-id="cf32e-117">Ele é usado somente para comunicação no mesmo computador.</span><span class="sxs-lookup"><span data-stu-id="cf32e-117">It is used only for communication on the same machine.</span></span> <span data-ttu-id="cf32e-118">Portanto, ao executar o exemplo em um cenário de máquina cruzada, comente as seguintes linhas no arquivo de código do cliente:</span><span class="sxs-lookup"><span data-stu-id="cf32e-118">Therefore, when running the sample in a cross-machine scenario, comment out the following lines in the client code file:</span></span>  
  
```csharp  
CalculatorClient client = new CalculatorClient("default");  
Console.WriteLine("Communicate with named pipe endpoint.");  
// Call operations.  
DoCalculations(client);  
//Closing the client gracefully closes the connection and cleans up resources  
client.Close();  
```  
  
```vb  
Dim client As New CalculatorClient("default")  
Console.WriteLine("Communicate with named pipe endpoint.")  
' call operations  
DoCalculations(client)  
'Closing the client gracefully closes the connection and cleans up resources  
client.Close()  
```  
  
> [!NOTE]
> <span data-ttu-id="cf32e-119">Se você usar svcutil. exe para regenerar a configuração para este exemplo, certifique-se de modificar o nome do ponto de extremidade na configuração do cliente para corresponder ao código do cliente.</span><span class="sxs-lookup"><span data-stu-id="cf32e-119">If you use Svcutil.exe to regenerate the configuration for this sample, be sure to modify the endpoint name in the client configuration to match the client code.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="cf32e-120">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="cf32e-120">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="cf32e-121">Verifique se você executou o [procedimento de configuração única para os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="cf32e-121">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="cf32e-122">Para criar a C#edição C++do, ou Visual Basic .NET da solução, siga as instruções em [criando os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="cf32e-122">To build the C#, C++, or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="cf32e-123">Para executar o exemplo em uma configuração de computador único ou cruzado, siga as instruções em [executando os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="cf32e-123">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="cf32e-124">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="cf32e-124">The samples may already be installed on your machine.</span></span> <span data-ttu-id="cf32e-125">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="cf32e-125">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="cf32e-126">Se esse diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos de Windows Workflow Foundation (WF) para .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) [!INCLUDE[wf1](../../../../includes/wf1-md.md)] e exemplos.</span><span class="sxs-lookup"><span data-stu-id="cf32e-126">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="cf32e-127">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="cf32e-127">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Custom\Transport`  
