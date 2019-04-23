---
title: Codificação e transporte de associação personalizado
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6c0b353d-79ee-4e61-b348-be49ad0e9a16
ms.openlocfilehash: d293ccb45a3af85ca5ca23fec9e3c01a55564581
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59767559"
---
# <a name="custom-binding-transport-and-encoding"></a><span data-ttu-id="0c4f9-102">Codificação e transporte de associação personalizado</span><span class="sxs-lookup"><span data-stu-id="0c4f9-102">Custom Binding Transport and Encoding</span></span>
<span data-ttu-id="0c4f9-103">Uma associação personalizada é definida por uma lista ordenada de elementos de associação discretos.</span><span class="sxs-lookup"><span data-stu-id="0c4f9-103">A custom binding is defined by an ordered list of discrete binding elements.</span></span> <span data-ttu-id="0c4f9-104">Este exemplo demonstra como configurar uma associação personalizada com vários transporte e mensagem que codifica elementos.</span><span class="sxs-lookup"><span data-stu-id="0c4f9-104">This sample demonstrates how to configure a custom binding with various transport and message encoding elements.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0c4f9-105">As instruções de procedimento e compilação de configuração para este exemplo estão localizadas no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="0c4f9-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="0c4f9-106">Este exemplo se baseia a [auto-hospedar](../../../../docs/framework/wcf/samples/self-host.md)e foi modificado para configurar os três pontos de extremidade para dar suporte a transportes HTTP, TCP e pipe nomeado com associações personalizadas.</span><span class="sxs-lookup"><span data-stu-id="0c4f9-106">This sample is based on the [Self-Host](../../../../docs/framework/wcf/samples/self-host.md), and has been modified to configure three endpoints to support HTTP, TCP, and NamedPipe transports with custom bindings.</span></span> <span data-ttu-id="0c4f9-107">A configuração de cliente da mesma forma foi modificada e o código do cliente é alterado para se comunicar com cada um dos três pontos de extremidade.</span><span class="sxs-lookup"><span data-stu-id="0c4f9-107">The client configuration was similarly modified, and the client code changed to communicate with each of the three endpoints.</span></span>  
  
 <span data-ttu-id="0c4f9-108">O exemplo demonstra como configurar uma associação personalizada que dá suporte a um transporte particular e a codificação de mensagem.</span><span class="sxs-lookup"><span data-stu-id="0c4f9-108">The sample demonstrates a how to configure a custom binding that supports a particular transport and message encoding.</span></span> <span data-ttu-id="0c4f9-109">Isso é feito configurando um transporte e uma mensagem de codificação para o `binding` elemento.</span><span class="sxs-lookup"><span data-stu-id="0c4f9-109">This is accomplished by configuring a transport and a message encoding for the `binding` element.</span></span> <span data-ttu-id="0c4f9-110">A ordenação dos elementos de associação é importante definir uma ligação personalizada, porque cada um representa uma camada da pilha de canal (consulte [ligações personalizadas](../../../../docs/framework/wcf/extending/custom-bindings.md)).</span><span class="sxs-lookup"><span data-stu-id="0c4f9-110">The ordering of binding elements is important in defining a custom binding, because each represents a layer in the channel stack (see [Custom Bindings](../../../../docs/framework/wcf/extending/custom-bindings.md)).</span></span> <span data-ttu-id="0c4f9-111">Esta amostra configura três ligações personalizadas: um transporte HTTP com codificação de texto, um transporte TCP com codificação de texto e um transporte de pipe nomeado com uma codificação binária.</span><span class="sxs-lookup"><span data-stu-id="0c4f9-111">This sample configures three custom bindings: an HTTP transport with text encoding, a TCP transport with text encoding, and a NamedPipe transport with a binary encoding.</span></span>  
  
 <span data-ttu-id="0c4f9-112">A configuração de serviço define as associações personalizadas da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="0c4f9-112">The service configuration defines the custom bindings as follows:</span></span>  
  
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
  
 <span data-ttu-id="0c4f9-113">Quando você executar o exemplo, as respostas e solicitações de operação são exibidas na janela do console de serviço e cliente.</span><span class="sxs-lookup"><span data-stu-id="0c4f9-113">When you run the sample, the operation requests and responses are displayed in both the service and client console window.</span></span> <span data-ttu-id="0c4f9-114">O cliente se comunica com cada um dos três pontos de extremidade, acessando primeiro HTTP, TCP e, finalmente, pipe nomeado.</span><span class="sxs-lookup"><span data-stu-id="0c4f9-114">The client communicates with each of the three endpoints, accessing first HTTP, then TCP, and finally NamedPipe.</span></span> <span data-ttu-id="0c4f9-115">Pressione ENTER em cada janela de console para desligar o serviço e o cliente.</span><span class="sxs-lookup"><span data-stu-id="0c4f9-115">Press ENTER in each console window to shut down the service and client.</span></span>  
  
 <span data-ttu-id="0c4f9-116">O `namedPipeTransport` associação não dá suporte a operações de máquina para máquina.</span><span class="sxs-lookup"><span data-stu-id="0c4f9-116">The `namedPipeTransport` binding does not support machine-to-machine operations.</span></span> <span data-ttu-id="0c4f9-117">Ele é usado apenas para comunicação no mesmo computador.</span><span class="sxs-lookup"><span data-stu-id="0c4f9-117">It is used only for communication on the same machine.</span></span> <span data-ttu-id="0c4f9-118">Portanto, ao executar o exemplo em um cenário entre máquinas, comente as linhas a seguir no arquivo de código do cliente:</span><span class="sxs-lookup"><span data-stu-id="0c4f9-118">Therefore, when running the sample in a cross-machine scenario, comment out the following lines in the client code file:</span></span>  
  
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
>  <span data-ttu-id="0c4f9-119">Se você usar Svcutil.exe para gerar novamente a configuração para este exemplo, certifique-se de modificar o nome do ponto de extremidade na configuração do cliente para coincidir com o código do cliente.</span><span class="sxs-lookup"><span data-stu-id="0c4f9-119">If you use Svcutil.exe to regenerate the configuration for this sample, be sure to modify the endpoint name in the client configuration to match the client code.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="0c4f9-120">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="0c4f9-120">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="0c4f9-121">Certifique-se de que você tenha executado o [procedimento de configuração de uso único para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="0c4f9-121">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="0c4f9-122">Para compilar a edição de c#, C++ ou Visual Basic .NET da solução, siga as instruções em [compilando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="0c4f9-122">To build the C#, C++, or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="0c4f9-123">Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="0c4f9-123">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="0c4f9-124">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="0c4f9-124">The samples may already be installed on your machine.</span></span> <span data-ttu-id="0c4f9-125">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="0c4f9-125">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="0c4f9-126">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="0c4f9-126">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="0c4f9-127">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="0c4f9-127">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Custom\Transport`  
