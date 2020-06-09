---
title: Sessão confiável de associação personalizada
ms.date: 03/30/2017
ms.assetid: c5fcd409-246f-4f3e-b3f1-629506ca4c04
ms.openlocfilehash: bd690f96eea885c4d414f9725125e1918fdffa23
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84585137"
---
# <a name="custom-binding-reliable-session"></a><span data-ttu-id="be5b4-102">Sessão confiável de associação personalizada</span><span class="sxs-lookup"><span data-stu-id="be5b4-102">Custom Binding Reliable Session</span></span>

<span data-ttu-id="be5b4-103">Uma associação personalizada é definida por uma lista ordenada de elementos de associação discretos.</span><span class="sxs-lookup"><span data-stu-id="be5b4-103">A custom binding is defined by an ordered list of discrete binding elements.</span></span> <span data-ttu-id="be5b4-104">Este exemplo demonstra como configurar uma associação personalizada com vários elementos de codificação de mensagens e transporte, especialmente permitindo sessões confiáveis.</span><span class="sxs-lookup"><span data-stu-id="be5b4-104">This sample demonstrates how to configure a custom binding with various transport and message encoding elements, especially enabling reliable sessions.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="be5b4-105">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="be5b4-105">The samples may already be installed on your machine.</span></span> <span data-ttu-id="be5b4-106">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="be5b4-106">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="be5b4-107">Se esse diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos de Windows Workflow Foundation (WF) para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="be5b4-107">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="be5b4-108">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="be5b4-108">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Custom\ReliableSession`

## <a name="sample-details"></a><span data-ttu-id="be5b4-109">Detalhes de exemplo</span><span class="sxs-lookup"><span data-stu-id="be5b4-109">Sample Details</span></span>

<span data-ttu-id="be5b4-110">As sessões confiáveis fornecem recursos para mensagens e sessões confiáveis.</span><span class="sxs-lookup"><span data-stu-id="be5b4-110">Reliable sessions provide features for reliable messaging and sessions.</span></span> <span data-ttu-id="be5b4-111">A Reliable Messaging repete a comunicação em caso de falha e permite que as garantias de entrega, como a chegada da ordem das mensagens a serem especificadas.</span><span class="sxs-lookup"><span data-stu-id="be5b4-111">Reliable messaging retries communication on failure and allows delivery assurances such as in-order arrival of messages to be specified.</span></span> <span data-ttu-id="be5b4-112">As sessões mantêm o estado para clientes entre chamadas.</span><span class="sxs-lookup"><span data-stu-id="be5b4-112">Sessions maintain state for clients between calls.</span></span> <span data-ttu-id="be5b4-113">O exemplo implementa sessões para manter o estado do cliente e especifica garantias de entrega em ordem.</span><span class="sxs-lookup"><span data-stu-id="be5b4-113">The sample implements sessions for maintaining client state and specifies in-order delivery assurances.</span></span> <span data-ttu-id="be5b4-114">O exemplo se baseia na [introdução](getting-started-sample.md) que implementa um serviço de calculadora.</span><span class="sxs-lookup"><span data-stu-id="be5b4-114">The sample is based on the [Getting Started](getting-started-sample.md) that implements a calculator service.</span></span> <span data-ttu-id="be5b4-115">Os recursos de sessão confiáveis são habilitados e configurados nos arquivos de configuração do aplicativo para o cliente e o serviço.</span><span class="sxs-lookup"><span data-stu-id="be5b4-115">The reliable session features are enabled and configured in the application configuration files for the client and service.</span></span>

> [!NOTE]
> <span data-ttu-id="be5b4-116">Os procedimentos de instalação e as instruções de compilação para esse exemplo estão localizadas no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="be5b4-116">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>

<span data-ttu-id="be5b4-117">A ordenação de elementos de associação é importante na definição de uma associação personalizada, pois cada uma representa uma camada na pilha de canais (consulte [associações personalizadas](../extending/custom-bindings.md)).</span><span class="sxs-lookup"><span data-stu-id="be5b4-117">The ordering of binding elements is important in defining a custom binding, because each represents a layer in the channel stack (see [Custom Bindings](../extending/custom-bindings.md)).</span></span>

<span data-ttu-id="be5b4-118">A configuração de serviço para o exemplo é definida conforme mostrado no exemplo de código a seguir.</span><span class="sxs-lookup"><span data-stu-id="be5b4-118">The service configuration for the sample is defined as shown in the following code example.</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <system.serviceModel>
    <services>
      <service
          name="Microsoft.ServiceModel.Samples.CalculatorService"
          behaviorConfiguration="CalculatorServiceBehavior">
        <!-- This endpoint is exposed at the base address provided by host: http://localhost/servicemodelsamples/service.svc  -->
        <!-- specify customBinding binding and a binding configuration to use -->
        <endpoint address=""
                  binding="customBinding"
                  bindingConfiguration="Binding1"
                  contract="Microsoft.ServiceModel.Samples.ICalculator" />
        <!-- The mex endpoint is exposed at http://localhost/servicemodelsamples/service.svc/mex -->
        <endpoint address="mex"
                  binding="mexHttpBinding"
                  contract="IMetadataExchange" />
      </service>
    </services>

    <!-- custom binding configuration - configures HTTP transport, reliable sessions -->
    <bindings>
      <customBinding>
        <binding name="Binding1">
          <reliableSession />
          <security authenticationMode="SecureConversation"
                     requireSecurityContextCancellation="true">
          </security>
          <compositeDuplex />
          <oneWay />
          <textMessageEncoding messageVersion="Soap12WSAddressing10" writeEncoding="utf-8" />
          <httpTransport authenticationScheme="Anonymous" bypassProxyOnLocal="false"
                        hostNameComparisonMode="StrongWildcard"
                        proxyAuthenticationScheme="Anonymous" realm=""
                        useDefaultWebProxy="true" />
        </binding>
      </customBinding>
    </bindings>

    <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->
    <behaviors>
      <serviceBehaviors>
        <behavior name="CalculatorServiceBehavior">
          <serviceMetadata httpGetEnabled="True"/>
          <serviceDebug includeExceptionDetailInFaults="False" />
        </behavior>
      </serviceBehaviors>
    </behaviors>

  </system.serviceModel>

</configuration>
```

<span data-ttu-id="be5b4-119">Ao executar em um cenário entre máquinas, você deve alterar o endereço do ponto de extremidade do cliente para refletir o nome do host do serviço.</span><span class="sxs-lookup"><span data-stu-id="be5b4-119">When running in a cross-machine scenario, you must change client's endpoint address to reflect the host name of the service.</span></span>

<span data-ttu-id="be5b4-120">Quando você executa o exemplo, as solicitações de operação e as respostas são exibidas na janela do console do cliente.</span><span class="sxs-lookup"><span data-stu-id="be5b4-120">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="be5b4-121">Pressione ENTER na janela do cliente para desligar o cliente.</span><span class="sxs-lookup"><span data-stu-id="be5b4-121">Press ENTER in the client window to shut down the client.</span></span>

```console
Add(100,15.99) = 115.99
Subtract(145,76.54) = 68.46
Multiply(9,81.25) = 731.25
Divide(22,7) = 3.14285714285714

Press <ENTER> to terminate client.
```

#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="be5b4-122">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="be5b4-122">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="be5b4-123">Instale o ASP.NET 4,0 usando o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="be5b4-123">Install ASP.NET 4.0 using the following command:</span></span>

    ```console
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable
    ```

2. <span data-ttu-id="be5b4-124">Verifique se você executou o [procedimento de configuração única para os exemplos de Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="be5b4-124">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

3. <span data-ttu-id="be5b4-125">Para criar a edição C# ou Visual Basic .NET da solução, siga as instruções em [criando os exemplos de Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="be5b4-125">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

4. <span data-ttu-id="be5b4-126">Para executar o exemplo em uma configuração de computador único ou cruzado, siga as instruções em [executando os exemplos de Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="be5b4-126">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="be5b4-127">Ao executar o cliente em uma configuração entre computadores, certifique-se de substituir "localhost" no `address` atributo do [\<endpoint>](../../configure-apps/file-schema/wcf/endpoint-element.md) elemento e no `clientBaseAddress` atributo de [\<compositeDuplex>](../../configure-apps/file-schema/wcf/compositeduplex.md) pelo nome do computador apropriado, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="be5b4-127">When running the client in a cross-machine configuration, be sure to replace "localhost" in both the `address` attribute of the [\<endpoint>](../../configure-apps/file-schema/wcf/endpoint-element.md) element and the `clientBaseAddress` attribute of the [\<compositeDuplex>](../../configure-apps/file-schema/wcf/compositeduplex.md) with the name of the appropriate machine, as shown in the following example.</span></span>

    ```xml
    <endpoint name = ""
    address="http://service_machine_name/servicemodelsamples/service.svc" />
    <compositeDuplex clientBaseAddress="http://client_machine_name:8000/myClient/" />
    ```
