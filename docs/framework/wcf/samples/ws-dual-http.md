---
title: WS Dual Http
ms.date: 03/30/2017
ms.assetid: 9997eba5-29ec-48db-86f3-fa77b241fb1a
ms.openlocfilehash: 44fdf6f0b27e15c486afa32f67668e9fd6eeac10
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/16/2019
ms.locfileid: "74138679"
---
# <a name="ws-dual-http"></a><span data-ttu-id="3320d-102">WS Dual Http</span><span class="sxs-lookup"><span data-stu-id="3320d-102">WS Dual Http</span></span>

<span data-ttu-id="3320d-103">O exemplo http duplo demonstra como configurar a associação de `WSDualHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="3320d-103">The Dual Http sample demonstrates how to configure the `WSDualHttpBinding` binding.</span></span> <span data-ttu-id="3320d-104">Este exemplo consiste em um programa de console do cliente (. exe) e uma biblioteca de serviços (. dll) hospedados pelo Serviços de Informações da Internet (IIS).</span><span class="sxs-lookup"><span data-stu-id="3320d-104">This sample consists of a client console program (.exe) and a service library (.dll) hosted by Internet Information Services (IIS).</span></span> <span data-ttu-id="3320d-105">O serviço implementa um contrato duplex.</span><span class="sxs-lookup"><span data-stu-id="3320d-105">The service implements a duplex contract.</span></span> <span data-ttu-id="3320d-106">O contrato é definido pela interface `ICalculatorDuplex`, que expõe operações matemáticas (adicionar, subtrair, multiplicar e dividir).</span><span class="sxs-lookup"><span data-stu-id="3320d-106">The contract is defined by the `ICalculatorDuplex` interface, which exposes math operations (Add, Subtract, Multiply, and Divide).</span></span> <span data-ttu-id="3320d-107">Neste exemplo, a interface `ICalculatorDuplex` permite que o cliente execute operações matemáticas, calculando um resultado em execução pela sessão.</span><span class="sxs-lookup"><span data-stu-id="3320d-107">In this sample, the `ICalculatorDuplex` interface allows the client to perform math operations, calculating a running result over the session.</span></span> <span data-ttu-id="3320d-108">Independentemente, o serviço retorna resultados na interface `ICalculatorDuplexCallback`.</span><span class="sxs-lookup"><span data-stu-id="3320d-108">Independently, the service returns results on the `ICalculatorDuplexCallback` interface.</span></span> <span data-ttu-id="3320d-109">Um contrato duplex requer uma sessão, porque um contexto deve ser estabelecido para correlacionar o conjunto de mensagens que estão sendo enviadas entre o cliente e o serviço.</span><span class="sxs-lookup"><span data-stu-id="3320d-109">A duplex contract requires a session, because a context must be established to correlate the set of messages being sent between client and service.</span></span> <span data-ttu-id="3320d-110">A associação de `WSDualHttpBinding` dá suporte à comunicação duplex.</span><span class="sxs-lookup"><span data-stu-id="3320d-110">The `WSDualHttpBinding` binding supports duplex communication.</span></span>

> [!NOTE]
> <span data-ttu-id="3320d-111">O procedimento de instalação e as instruções de Build para este exemplo estão localizados no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="3320d-111">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="3320d-112">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="3320d-112">The samples may already be installed on your machine.</span></span> <span data-ttu-id="3320d-113">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="3320d-113">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="3320d-114">Se esse diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos de Windows Workflow Foundation (WF) para .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todas as Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] amostras.</span><span class="sxs-lookup"><span data-stu-id="3320d-114">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="3320d-115">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="3320d-115">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\DualHttp`

<span data-ttu-id="3320d-116">Para configurar um ponto de extremidade de serviço com o `WSDualHttpBinding`, especifique a associação na configuração do ponto de extremidade, conforme mostrado.</span><span class="sxs-lookup"><span data-stu-id="3320d-116">To configure a service endpoint with the `WSDualHttpBinding`, specify the binding in the endpoint configuration as shown.</span></span>

```xml
<endpoint address=""
         binding="wsDualHttpBinding"
         contract="Microsoft.ServiceModel.Samples.ICalculatorDuplex" />
```

<span data-ttu-id="3320d-117">No cliente, você deve configurar um endereço que o servidor pode usar para se conectar ao cliente, conforme mostrado na seguinte configuração de exemplo.</span><span class="sxs-lookup"><span data-stu-id="3320d-117">On the client, you must configure an address that the server can use to connect to the client as shown in the following sample configuration.</span></span>

```xml
<system.serviceModel>
  <client>
    <endpoint address=
         "http://localhost/servicemodelsamples/service.svc"
         binding="wsDualHttpBinding"
         bindingConfiguration="Binding1"
         contract="Microsoft.ServiceModel.Samples.ICalculatorDuplex" />
  </client>

  <bindings>
    <!-- Configure a WSDualHttpBinding that supports duplex -->
    <!-- communication. -->
    <wsDualHttpBinding>
      <binding name="Binding1"
               clientBaseAddress="http://localhost:8000/myClient/"
               useDefaultWebProxy="true"
               bypassProxyOnLocal="false">
      </binding>
    </wsDualHttpBinding>
  </bindings>
</system.serviceModel>
```

<span data-ttu-id="3320d-118">Quando você executa o exemplo, as solicitações de operação e as respostas são exibidas na janela do console do cliente.</span><span class="sxs-lookup"><span data-stu-id="3320d-118">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="3320d-119">Pressione ENTER na janela do cliente para desligar o cliente.</span><span class="sxs-lookup"><span data-stu-id="3320d-119">Press ENTER in the client window to shut down the client.</span></span>

```console
Press <ENTER> to terminate client once the output is displayed.

Result(100)
Result(50)
Result(882.5)
Result(441.25)
Equation(0 + 100 - 50 * 17.65 / 2 = 441.25)
```

<span data-ttu-id="3320d-120">Ao executar o exemplo, você verá as mensagens retornadas para o cliente na interface de retorno de chamada enviadas do serviço.</span><span class="sxs-lookup"><span data-stu-id="3320d-120">When you run the sample, you see the messages returned to the client on the callback interface sent from the service.</span></span> <span data-ttu-id="3320d-121">Cada resultado intermediário é exibido, seguido de toda a equação após a conclusão de todas as operações.</span><span class="sxs-lookup"><span data-stu-id="3320d-121">Each intermediate result is displayed, followed by the entire equation upon completion of all operations.</span></span> <span data-ttu-id="3320d-122">Pressione ENTER para desligar o cliente.</span><span class="sxs-lookup"><span data-stu-id="3320d-122">Press ENTER to shut down the client.</span></span>

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="3320d-123">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="3320d-123">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="3320d-124">Instale o ASP.NET 4,0 usando o comando a seguir.</span><span class="sxs-lookup"><span data-stu-id="3320d-124">Install ASP.NET 4.0 using the following command.</span></span>

    ```console
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable
    ```

2. <span data-ttu-id="3320d-125">Verifique se você executou o [procedimento de configuração única para os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="3320d-125">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

3. <span data-ttu-id="3320d-126">Para compilar a C# edição do ou Visual Basic .NET da solução, siga as instruções em [criando os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="3320d-126">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

4. <span data-ttu-id="3320d-127">Para executar o exemplo em uma configuração de computador único ou cruzado, siga as instruções em [executando os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="3320d-127">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="3320d-128">Ao executar o cliente em uma configuração entre computadores, certifique-se de substituir localhost no atributo `address` do [> de ponto de extremidade\<do elemento \<client >](../../configure-apps/file-schema/wcf/endpoint-of-client.md) e o atributo `clientBaseAddress` da [Associação\<](../../configure-apps/file-schema/wcf/bindings.md) o elemento do elemento [\<wsDualHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md) com o nome do computador apropriado, conforme mostrado:</span><span class="sxs-lookup"><span data-stu-id="3320d-128">When running the client in a cross-machine configuration, be sure to replace localhost in both the `address` attribute of the [\<endpoint> of \<client>](../../configure-apps/file-schema/wcf/endpoint-of-client.md) element and the `clientBaseAddress` attribute of the [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) element of the [\<wsDualHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md) element with the name of the appropriate machine, as shown:</span></span>

    ```xml
    <client>
        <endpoint name = ""
          address=
         "http://service_machine_name/servicemodelsamples/service.svc"
        />
    </client>
    ...
    <wsDualHttpBinding>
        <binding name="DuplexBinding" clientBaseAddress=
            "http://client_machine_name:8000/myClient/">
        </binding>
    </wsDualHttpBinding>
    ```
