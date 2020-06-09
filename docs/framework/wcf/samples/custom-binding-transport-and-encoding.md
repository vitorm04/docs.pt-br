---
title: Codificação e transporte de associação personalizado
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6c0b353d-79ee-4e61-b348-be49ad0e9a16
ms.openlocfilehash: 3b3a0f1b52afce495ca41a426ebc9e57314d8254
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84592522"
---
# <a name="custom-binding-transport-and-encoding"></a><span data-ttu-id="0a7ad-102">Codificação e transporte de associação personalizado</span><span class="sxs-lookup"><span data-stu-id="0a7ad-102">Custom Binding Transport and Encoding</span></span>
<span data-ttu-id="0a7ad-103">Uma associação personalizada é definida por uma lista ordenada de elementos de associação discretos.</span><span class="sxs-lookup"><span data-stu-id="0a7ad-103">A custom binding is defined by an ordered list of discrete binding elements.</span></span> <span data-ttu-id="0a7ad-104">Este exemplo demonstra como configurar uma associação personalizada com vários elementos de codificação de mensagens e transporte.</span><span class="sxs-lookup"><span data-stu-id="0a7ad-104">This sample demonstrates how to configure a custom binding with various transport and message encoding elements.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0a7ad-105">O procedimento de instalação e as instruções de Build para este exemplo estão localizados no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="0a7ad-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="0a7ad-106">Este exemplo é baseado no [auto-host](self-host.md)e foi modificado para configurar três pontos de extremidade para dar suporte a transportes http, TCP e NamedPipe com associações personalizadas.</span><span class="sxs-lookup"><span data-stu-id="0a7ad-106">This sample is based on the [Self-Host](self-host.md), and has been modified to configure three endpoints to support HTTP, TCP, and NamedPipe transports with custom bindings.</span></span> <span data-ttu-id="0a7ad-107">A configuração do cliente foi modificada da mesma forma e o código do cliente foi alterado para se comunicar com cada um dos três pontos de extremidade.</span><span class="sxs-lookup"><span data-stu-id="0a7ad-107">The client configuration was similarly modified, and the client code changed to communicate with each of the three endpoints.</span></span>  
  
 <span data-ttu-id="0a7ad-108">O exemplo demonstra como configurar uma ligação personalizada que dá suporte a um transporte e codificação de mensagem específicos.</span><span class="sxs-lookup"><span data-stu-id="0a7ad-108">The sample demonstrates a how to configure a custom binding that supports a particular transport and message encoding.</span></span> <span data-ttu-id="0a7ad-109">Isso é feito configurando um transporte e uma codificação de mensagem para o `binding` elemento.</span><span class="sxs-lookup"><span data-stu-id="0a7ad-109">This is accomplished by configuring a transport and a message encoding for the `binding` element.</span></span> <span data-ttu-id="0a7ad-110">A ordenação de elementos de associação é importante na definição de uma associação personalizada, pois cada uma representa uma camada na pilha de canais (consulte [associações personalizadas](../extending/custom-bindings.md)).</span><span class="sxs-lookup"><span data-stu-id="0a7ad-110">The ordering of binding elements is important in defining a custom binding, because each represents a layer in the channel stack (see [Custom Bindings](../extending/custom-bindings.md)).</span></span> <span data-ttu-id="0a7ad-111">Esta amostra configura três associações personalizadas: um transporte HTTP com codificação de texto, um transporte TCP com codificação de texto e um transporte NamedPipe com uma codificação binária.</span><span class="sxs-lookup"><span data-stu-id="0a7ad-111">This sample configures three custom bindings: an HTTP transport with text encoding, a TCP transport with text encoding, and a NamedPipe transport with a binary encoding.</span></span>  
  
 <span data-ttu-id="0a7ad-112">A configuração de serviço define as associações personalizadas da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="0a7ad-112">The service configuration defines the custom bindings as follows:</span></span>  
  
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
  
 <span data-ttu-id="0a7ad-113">Quando você executa o exemplo, as solicitações e respostas da operação são exibidas na janela do console do cliente e do serviço.</span><span class="sxs-lookup"><span data-stu-id="0a7ad-113">When you run the sample, the operation requests and responses are displayed in both the service and client console window.</span></span> <span data-ttu-id="0a7ad-114">O cliente se comunica com cada um dos três pontos de extremidade, acessando primeiro HTTP, depois TCP e, por fim, NamedPipe.</span><span class="sxs-lookup"><span data-stu-id="0a7ad-114">The client communicates with each of the three endpoints, accessing first HTTP, then TCP, and finally NamedPipe.</span></span> <span data-ttu-id="0a7ad-115">Pressione ENTER em cada janela do console para desligar o serviço e o cliente.</span><span class="sxs-lookup"><span data-stu-id="0a7ad-115">Press ENTER in each console window to shut down the service and client.</span></span>  
  
 <span data-ttu-id="0a7ad-116">A `namedPipeTransport` associação não oferece suporte a operações de máquina a máquina.</span><span class="sxs-lookup"><span data-stu-id="0a7ad-116">The `namedPipeTransport` binding does not support machine-to-machine operations.</span></span> <span data-ttu-id="0a7ad-117">Ele é usado somente para comunicação no mesmo computador.</span><span class="sxs-lookup"><span data-stu-id="0a7ad-117">It is used only for communication on the same machine.</span></span> <span data-ttu-id="0a7ad-118">Portanto, ao executar o exemplo em um cenário de máquina cruzada, comente as seguintes linhas no arquivo de código do cliente:</span><span class="sxs-lookup"><span data-stu-id="0a7ad-118">Therefore, when running the sample in a cross-machine scenario, comment out the following lines in the client code file:</span></span>  
  
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
> <span data-ttu-id="0a7ad-119">Se você usar svcutil. exe para regenerar a configuração para este exemplo, certifique-se de modificar o nome do ponto de extremidade na configuração do cliente para corresponder ao código do cliente.</span><span class="sxs-lookup"><span data-stu-id="0a7ad-119">If you use Svcutil.exe to regenerate the configuration for this sample, be sure to modify the endpoint name in the client configuration to match the client code.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="0a7ad-120">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="0a7ad-120">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="0a7ad-121">Verifique se você executou o [procedimento de configuração única para os exemplos de Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="0a7ad-121">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="0a7ad-122">Para criar a edição C#, C++ ou Visual Basic .NET da solução, siga as instruções em [criando os exemplos de Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="0a7ad-122">To build the C#, C++, or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="0a7ad-123">Para executar o exemplo em uma configuração de computador único ou cruzado, siga as instruções em [executando os exemplos de Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="0a7ad-123">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="0a7ad-124">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="0a7ad-124">The samples may already be installed on your machine.</span></span> <span data-ttu-id="0a7ad-125">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="0a7ad-125">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="0a7ad-126">Se esse diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos de Windows Workflow Foundation (WF) para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="0a7ad-126">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="0a7ad-127">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="0a7ad-127">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Custom\Transport`  
