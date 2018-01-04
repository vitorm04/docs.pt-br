---
title: "Codificação e transporte de associação personalizado"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 6c0b353d-79ee-4e61-b348-be49ad0e9a16
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 82db4ec7dfd1dd10837f2b2424615f8afbe81932
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="custom-binding-transport-and-encoding"></a><span data-ttu-id="c50d3-102">Codificação e transporte de associação personalizado</span><span class="sxs-lookup"><span data-stu-id="c50d3-102">Custom Binding Transport and Encoding</span></span>
<span data-ttu-id="c50d3-103">Uma associação personalizada é definida por uma lista ordenada de elementos de associação discretos.</span><span class="sxs-lookup"><span data-stu-id="c50d3-103">A custom binding is defined by an ordered list of discrete binding elements.</span></span> <span data-ttu-id="c50d3-104">Este exemplo demonstra como configurar uma associação personalizada com vários transporte e elementos de codificação de mensagem.</span><span class="sxs-lookup"><span data-stu-id="c50d3-104">This sample demonstrates how to configure a custom binding with various transport and message encoding elements.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c50d3-105">As instruções de procedimento e a compilação de configuração para este exemplo estão localizadas no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="c50d3-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="c50d3-106">Este exemplo se baseia o [auto-host](../../../../docs/framework/wcf/samples/self-host.md)e foi modificado para configurar três pontos de extremidade para dar suporte a transportes HTTP, TCP e pipe nomeado com associações personalizadas.</span><span class="sxs-lookup"><span data-stu-id="c50d3-106">This sample is based on the [Self-Host](../../../../docs/framework/wcf/samples/self-host.md), and has been modified to configure three endpoints to support HTTP, TCP, and NamedPipe transports with custom bindings.</span></span> <span data-ttu-id="c50d3-107">A configuração de cliente da mesma forma foi modificada e o código do cliente é alterado para se comunicar com cada um dos três pontos de extremidade.</span><span class="sxs-lookup"><span data-stu-id="c50d3-107">The client configuration was similarly modified, and the client code changed to communicate with each of the three endpoints.</span></span>  
  
 <span data-ttu-id="c50d3-108">O exemplo demonstra um como configurar uma associação personalizada que dá suporte a um transporte particular e a codificação de mensagens.</span><span class="sxs-lookup"><span data-stu-id="c50d3-108">The sample demonstrates a how to configure a custom binding that supports a particular transport and message encoding.</span></span> <span data-ttu-id="c50d3-109">Isso é feito por meio da configuração de um transporte e uma mensagem de codificação para o `binding` elemento.</span><span class="sxs-lookup"><span data-stu-id="c50d3-109">This is accomplished by configuring a transport and a message encoding for the `binding` element.</span></span> <span data-ttu-id="c50d3-110">A ordenação dos elementos de associação é importante definir uma associação personalizada, como cada uma representa uma camada da pilha de canal (consulte [associações personalizadas](../../../../docs/framework/wcf/extending/custom-bindings.md)).</span><span class="sxs-lookup"><span data-stu-id="c50d3-110">The ordering of binding elements is important in defining a custom binding, because each represents a layer in the channel stack (see [Custom Bindings](../../../../docs/framework/wcf/extending/custom-bindings.md)).</span></span> <span data-ttu-id="c50d3-111">Este exemplo configura três associações personalizadas: um transporte HTTP com codificação de texto, um transporte TCP com codificação de texto e um transporte de pipe nomeado com uma codificação binária.</span><span class="sxs-lookup"><span data-stu-id="c50d3-111">This sample configures three custom bindings: an HTTP transport with text encoding, a TCP transport with text encoding, and a NamedPipe transport with a binary encoding.</span></span>  
  
 <span data-ttu-id="c50d3-112">A configuração de serviço define as associações personalizadas da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="c50d3-112">The service configuration defines the custom bindings as follows:</span></span>  
  
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
  
 <span data-ttu-id="c50d3-113">Quando você executar o exemplo, as respostas e solicitações de operação são exibidas na janela do console de serviço e o cliente.</span><span class="sxs-lookup"><span data-stu-id="c50d3-113">When you run the sample, the operation requests and responses are displayed in both the service and client console window.</span></span> <span data-ttu-id="c50d3-114">O cliente se comunica com cada um dos três pontos de extremidade, acessando primeiro HTTP, TCP e, finalmente, pipe nomeado.</span><span class="sxs-lookup"><span data-stu-id="c50d3-114">The client communicates with each of the three endpoints, accessing first HTTP, then TCP, and finally NamedPipe.</span></span> <span data-ttu-id="c50d3-115">Pressione ENTER em cada janela de console para desligar o serviço e o cliente.</span><span class="sxs-lookup"><span data-stu-id="c50d3-115">Press ENTER in each console window to shut down the service and client.</span></span>  
  
 <span data-ttu-id="c50d3-116">O `namedPipeTransport` associação não oferece suporte a operações de máquina para máquina.</span><span class="sxs-lookup"><span data-stu-id="c50d3-116">The `namedPipeTransport` binding does not support machine-to-machine operations.</span></span> <span data-ttu-id="c50d3-117">Ele é usado apenas para comunicação no mesmo computador.</span><span class="sxs-lookup"><span data-stu-id="c50d3-117">It is used only for communication on the same machine.</span></span> <span data-ttu-id="c50d3-118">Portanto, ao executar o exemplo em um cenário de várias máquinas, comente as linhas seguintes no arquivo de código do cliente:</span><span class="sxs-lookup"><span data-stu-id="c50d3-118">Therefore, when running the sample in a cross-machine scenario, comment out the following lines in the client code file:</span></span>  
  
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
>  <span data-ttu-id="c50d3-119">Se você usar o Svcutil.exe para gerar novamente a configuração para este exemplo, certifique-se de modificar o nome do ponto de extremidade na configuração do cliente para coincidir com o código do cliente.</span><span class="sxs-lookup"><span data-stu-id="c50d3-119">If you use Svcutil.exe to regenerate the configuration for this sample, be sure to modify the endpoint name in the client configuration to match the client code.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="c50d3-120">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="c50d3-120">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="c50d3-121">Certifique-se de que você executou o [único procedimento de instalação para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c50d3-121">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="c50d3-122">Para criar a edição do c#, C++ ou Visual Basic .NET da solução, siga as instruções em [compilar os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c50d3-122">To build the C#, C++, or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="c50d3-123">Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c50d3-123">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="c50d3-124">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="c50d3-124">The samples may already be installed on your machine.</span></span> <span data-ttu-id="c50d3-125">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="c50d3-125">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="c50d3-126">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="c50d3-126">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="c50d3-127">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="c50d3-127">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Custom\Transport`  
  
## <a name="see-also"></a><span data-ttu-id="c50d3-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c50d3-128">See Also</span></span>
