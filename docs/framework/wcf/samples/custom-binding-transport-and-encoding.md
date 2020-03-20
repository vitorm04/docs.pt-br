---
title: Codificação e transporte de associação personalizado
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6c0b353d-79ee-4e61-b348-be49ad0e9a16
ms.openlocfilehash: 47841b23dc3259aeb233192f396397745864d7ba
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79145158"
---
# <a name="custom-binding-transport-and-encoding"></a><span data-ttu-id="a933f-102">Codificação e transporte de associação personalizado</span><span class="sxs-lookup"><span data-stu-id="a933f-102">Custom Binding Transport and Encoding</span></span>
<span data-ttu-id="a933f-103">Uma vinculação personalizada é definida por uma lista ordenada de elementos de ligação discretos.</span><span class="sxs-lookup"><span data-stu-id="a933f-103">A custom binding is defined by an ordered list of discrete binding elements.</span></span> <span data-ttu-id="a933f-104">Esta amostra demonstra como configurar uma vinculação personalizada com vários elementos de codificação de transporte e mensagens.</span><span class="sxs-lookup"><span data-stu-id="a933f-104">This sample demonstrates how to configure a custom binding with various transport and message encoding elements.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a933f-105">O procedimento de configuração e as instruções de construção desta amostra estão localizados no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="a933f-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="a933f-106">Esta amostra é baseada no [Self-Host](../../../../docs/framework/wcf/samples/self-host.md)e foi modificada para configurar três pontos finais para suportar transportes HTTP, TCP e NamedPipe com vinculações personalizadas.</span><span class="sxs-lookup"><span data-stu-id="a933f-106">This sample is based on the [Self-Host](../../../../docs/framework/wcf/samples/self-host.md), and has been modified to configure three endpoints to support HTTP, TCP, and NamedPipe transports with custom bindings.</span></span> <span data-ttu-id="a933f-107">A configuração do cliente foi modificada da mesma forma, e o código do cliente mudou para se comunicar com cada um dos três pontos finais.</span><span class="sxs-lookup"><span data-stu-id="a933f-107">The client configuration was similarly modified, and the client code changed to communicate with each of the three endpoints.</span></span>  
  
 <span data-ttu-id="a933f-108">A amostra demonstra como configurar uma vinculação personalizada que suporta uma codificação de transporte e mensagem específica.</span><span class="sxs-lookup"><span data-stu-id="a933f-108">The sample demonstrates a how to configure a custom binding that supports a particular transport and message encoding.</span></span> <span data-ttu-id="a933f-109">Isso é feito configurando um transporte e `binding` uma codificação de mensagem para o elemento.</span><span class="sxs-lookup"><span data-stu-id="a933f-109">This is accomplished by configuring a transport and a message encoding for the `binding` element.</span></span> <span data-ttu-id="a933f-110">A ordenação de elementos de ligação é importante para definir uma vinculação personalizada, pois cada uma representa uma camada na pilha de canais (ver [Vinculações personalizadas](../../../../docs/framework/wcf/extending/custom-bindings.md)).</span><span class="sxs-lookup"><span data-stu-id="a933f-110">The ordering of binding elements is important in defining a custom binding, because each represents a layer in the channel stack (see [Custom Bindings](../../../../docs/framework/wcf/extending/custom-bindings.md)).</span></span> <span data-ttu-id="a933f-111">Esta amostra configura três vinculações personalizadas: um transporte HTTP com codificação de texto, um transporte TCP com codificação de texto e um transporte NamedPipe com uma codificação binária.</span><span class="sxs-lookup"><span data-stu-id="a933f-111">This sample configures three custom bindings: an HTTP transport with text encoding, a TCP transport with text encoding, and a NamedPipe transport with a binary encoding.</span></span>  
  
 <span data-ttu-id="a933f-112">A configuração do serviço define as vinculações personalizadas da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="a933f-112">The service configuration defines the custom bindings as follows:</span></span>  
  
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
  
 <span data-ttu-id="a933f-113">Quando você executa a amostra, as solicitações e respostas da operação são exibidas tanto na janela de serviço quanto no console do cliente.</span><span class="sxs-lookup"><span data-stu-id="a933f-113">When you run the sample, the operation requests and responses are displayed in both the service and client console window.</span></span> <span data-ttu-id="a933f-114">O cliente se comunica com cada um dos três pontos finais, acessando primeiro HTTP, depois TCP e, finalmente, NamedPipe.</span><span class="sxs-lookup"><span data-stu-id="a933f-114">The client communicates with each of the three endpoints, accessing first HTTP, then TCP, and finally NamedPipe.</span></span> <span data-ttu-id="a933f-115">Pressione ENTER em cada janela do console para desligar o serviço e o cliente.</span><span class="sxs-lookup"><span data-stu-id="a933f-115">Press ENTER in each console window to shut down the service and client.</span></span>  
  
 <span data-ttu-id="a933f-116">A `namedPipeTransport` ligação não suporta operações máquina a máquina.</span><span class="sxs-lookup"><span data-stu-id="a933f-116">The `namedPipeTransport` binding does not support machine-to-machine operations.</span></span> <span data-ttu-id="a933f-117">É usado apenas para comunicação na mesma máquina.</span><span class="sxs-lookup"><span data-stu-id="a933f-117">It is used only for communication on the same machine.</span></span> <span data-ttu-id="a933f-118">Portanto, ao executar a amostra em um cenário de máquina cruzada, comente as seguintes linhas no arquivo de código do cliente:</span><span class="sxs-lookup"><span data-stu-id="a933f-118">Therefore, when running the sample in a cross-machine scenario, comment out the following lines in the client code file:</span></span>  
  
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
> <span data-ttu-id="a933f-119">Se você usar Svcutil.exe para regenerar a configuração desta amostra, certifique-se de modificar o nome do ponto final na configuração do cliente para corresponder ao código do cliente.</span><span class="sxs-lookup"><span data-stu-id="a933f-119">If you use Svcutil.exe to regenerate the configuration for this sample, be sure to modify the endpoint name in the client configuration to match the client code.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="a933f-120">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="a933f-120">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="a933f-121">Certifique-se de que você tenha realizado o [procedimento de configuração única para as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="a933f-121">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="a933f-122">Para construir a edição C#, C++ou Visual Basic .NET da solução, siga as instruções em [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="a933f-122">To build the C#, C++, or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="a933f-123">Para executar a amostra em uma configuração de máquina única ou cruzada, siga as instruções em [Executar as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="a933f-123">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="a933f-124">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="a933f-124">The samples may already be installed on your machine.</span></span> <span data-ttu-id="a933f-125">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="a933f-125">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="a933f-126">Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation).</span><span class="sxs-lookup"><span data-stu-id="a933f-126">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="a933f-127">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="a933f-127">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Custom\Transport`  
