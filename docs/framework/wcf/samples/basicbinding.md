---
title: BasicBinding
ms.date: 03/30/2017
ms.assetid: 86fbeb87-4d89-4b61-9577-867e0ac12945
ms.openlocfilehash: 6a929c3bff9f6b2602a78775cdd5020220dc1f9b
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58815934"
---
# <a name="basicbinding"></a><span data-ttu-id="c501c-102">BasicBinding</span><span class="sxs-lookup"><span data-stu-id="c501c-102">BasicBinding</span></span>
<span data-ttu-id="c501c-103">Este exemplo demonstra o uso de `basicHttpBinding` que fornece interoperabilidade de comunicação e o máximo HTTP com o primeiro – e second - generation serviços da Web.</span><span class="sxs-lookup"><span data-stu-id="c501c-103">This sample demonstrates the use of `basicHttpBinding` that provides HTTP communication and maximum interoperability with first- and second-generation Web services.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c501c-104">Os procedimentos de instalação e as instruções de compilação para esse exemplo estão localizadas no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="c501c-104">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="c501c-105">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="c501c-105">The samples may already be installed on your machine.</span></span> <span data-ttu-id="c501c-106">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="c501c-106">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="c501c-107">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="c501c-107">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="c501c-108">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="c501c-108">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Basic\Http`  
  
## <a name="sample-details"></a><span data-ttu-id="c501c-109">Detalhes de exemplo</span><span class="sxs-lookup"><span data-stu-id="c501c-109">Sample Details</span></span>  
 <span data-ttu-id="c501c-110">Este exemplo se baseia a [guia de Introdução](../../../../docs/framework/wcf/samples/getting-started-sample.md) que implementa um serviço de calculadora.</span><span class="sxs-lookup"><span data-stu-id="c501c-110">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator service.</span></span>  
  
 <span data-ttu-id="c501c-111">Para usar a associação básica com o comportamento padrão, somente o nome da seção de associação é necessário.</span><span class="sxs-lookup"><span data-stu-id="c501c-111">To use the basic binding with default behavior, only the binding section name is required.</span></span> <span data-ttu-id="c501c-112">Se você quiser configurar a associação básica e alterar algumas de suas configurações, é necessário definir uma configuração de associação.</span><span class="sxs-lookup"><span data-stu-id="c501c-112">If you want to configure the basic binding and change some of its settings, it is necessary to define a binding configuration.</span></span> <span data-ttu-id="c501c-113">O ponto de extremidade deve fazer referência a configuração de associação por nome usando o `bindingConfiguration` atributo da <`endpoint`> elemento, conforme mostrado no código de exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="c501c-113">The endpoint must reference the binding configuration by name by using the `bindingConfiguration` attribute of the <`endpoint`> element, as shown in the following sample code.</span></span>  
  
```xml  
<services>  
    <service   
        type="Microsoft.ServiceModel.Samples.CalculatorService"  
        behaviorConfiguration="CalculatorServiceBehavior">  
       <endpoint address=""  
             binding="basicHttpBinding"  
             bindingConfiguration="Binding1"   
             contract="Microsoft.ServiceModel.Samples.ICalculator" />  
    </service>  
</services>  
```  
  
 <span data-ttu-id="c501c-114">Neste exemplo, a configuração de associação é chamada `"Binding1"` e é definido como mostrado no exemplo de código a seguir.</span><span class="sxs-lookup"><span data-stu-id="c501c-114">In this sample, the binding configuration is named `"Binding1"` and is defined as shown in the following code example.</span></span>  
  
```xml  
<bindings>  
   <basicHttpBinding>  
      <binding name="Binding1"   
               hostNameComparisonMode="StrongWildcard"   
               receiveTimeout="00:10:00"  
               sendTimeout="00:10:00"  
               openTimeout="00:10:00"  
               closeTimeout="00:10:00"  
               maxMessageSize="65536"   
               maxBufferSize="65536"   
               maxBufferPoolSize="524288"   
               transferMode="Buffered"   
               messageEncoding="Text"   
               textEncoding="utf-8"  
               bypassProxyOnLocal="false"  
               useDefaultWebProxy="true" >  
         <security mode="None" />  
      </binding>  
   </basicHttpBinding>  
</bindings>  
```  
  
 <span data-ttu-id="c501c-115">O elemento de associação fornece atributos para definir o modo de comparação de nome de host, tamanho máximo da mensagem, as opções de proxy, tempos limite, codificação de mensagem e outras opções.</span><span class="sxs-lookup"><span data-stu-id="c501c-115">The binding element provides attributes for setting the host name comparison mode, maximum message size, proxy options, timeouts, message encoding, and other options.</span></span>  
  
 <span data-ttu-id="c501c-116">Quando você executar o exemplo, as respostas e solicitações de operação são exibidas na janela do console de cliente.</span><span class="sxs-lookup"><span data-stu-id="c501c-116">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="c501c-117">Pressione ENTER na janela do cliente para desligar o cliente.</span><span class="sxs-lookup"><span data-stu-id="c501c-117">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="c501c-118">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="c501c-118">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="c501c-119">Instalar [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 usando o comando a seguir.</span><span class="sxs-lookup"><span data-stu-id="c501c-119">Install [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 using the following command.</span></span>  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2.  <span data-ttu-id="c501c-120">Certifique-se de que você tenha executado o [procedimento de configuração de uso único para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c501c-120">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3.  <span data-ttu-id="c501c-121">Para compilar a edição em C# ou Visual Basic .NET da solução, siga as instruções em [compilando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c501c-121">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4.  <span data-ttu-id="c501c-122">Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c501c-122">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
