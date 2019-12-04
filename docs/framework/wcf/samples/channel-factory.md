---
title: Fábrica de canais
ms.date: 03/30/2017
ms.assetid: 09b53aa1-b13c-476c-a461-e82fcacd2a8b
ms.openlocfilehash: eac315cf88b2ecc7471f194ef6c3be902b3ccbaa
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74716041"
---
# <a name="channel-factory"></a><span data-ttu-id="54531-102">Fábrica de canais</span><span class="sxs-lookup"><span data-stu-id="54531-102">Channel Factory</span></span>

<span data-ttu-id="54531-103">Este exemplo demonstra como um aplicativo cliente pode criar um canal com a classe <xref:System.ServiceModel.ChannelFactory> em vez de um cliente gerado.</span><span class="sxs-lookup"><span data-stu-id="54531-103">This sample demonstrates how a client application can create a channel with the <xref:System.ServiceModel.ChannelFactory> class instead of a generated client.</span></span> <span data-ttu-id="54531-104">Este exemplo é baseado no [introdução](../../../../docs/framework/wcf/samples/getting-started-sample.md) que implementa um serviço de calculadora.</span><span class="sxs-lookup"><span data-stu-id="54531-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator service.</span></span>

> [!NOTE]
> <span data-ttu-id="54531-105">O procedimento de instalação e as instruções de Build para este exemplo estão localizados no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="54531-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

<span data-ttu-id="54531-106">Este exemplo usa a classe <xref:System.ServiceModel.ChannelFactory%601> para criar um canal para um ponto de extremidade de serviço.</span><span class="sxs-lookup"><span data-stu-id="54531-106">This sample uses the <xref:System.ServiceModel.ChannelFactory%601> class to create a channel to a service endpoint.</span></span> <span data-ttu-id="54531-107">Normalmente, para criar um canal para um ponto de extremidade de serviço, você gera um tipo de cliente com a [ferramenta de utilitário de metadados ServiceModel (svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) e cria uma instância do tipo gerado.</span><span class="sxs-lookup"><span data-stu-id="54531-107">Typically, to create a channel to a service endpoint you generate a client type with the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) and create an instance of the generated type.</span></span> <span data-ttu-id="54531-108">Você também pode criar um canal usando a classe <xref:System.ServiceModel.ChannelFactory%601>, conforme demonstrado neste exemplo.</span><span class="sxs-lookup"><span data-stu-id="54531-108">You can also create a channel by using the <xref:System.ServiceModel.ChannelFactory%601> class, as demonstrated in this sample.</span></span> <span data-ttu-id="54531-109">O serviço criado pelo código de exemplo a seguir é idêntico ao serviço no [introdução](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="54531-109">The service created by the following sample code is identical to the service in the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span>

```csharp
EndpointAddress address = new EndpointAddress("http://localhost/servicemodelsamples/service.svc");
WSHttpBinding binding = new WSHttpBinding();
ChannelFactory<ICalculator> factory = new
                    ChannelFactory<ICalculator>(binding, address);
ICalculator channel = factory.CreateChannel();
```

> [!IMPORTANT]
> <span data-ttu-id="54531-110">Se você estiver executando este exemplo em um cenário de máquina cruzada, deverá substituir "localhost" no código anterior pelo nome totalmente qualificado do computador que está executando o serviço.</span><span class="sxs-lookup"><span data-stu-id="54531-110">If you are running this sample in a cross-machine scenario, you must replace "localhost" in the preceding code with the fully-qualified name of the machine that is running the service.</span></span> <span data-ttu-id="54531-111">Este exemplo não usa a configuração para definir o endereço do ponto de extremidade, portanto, isso deve ser feito no código.</span><span class="sxs-lookup"><span data-stu-id="54531-111">This sample does not use configuration to set the endpoint address, so this must be done in code.</span></span>

<span data-ttu-id="54531-112">Depois que o canal é criado, as operações de serviço podem ser invocadas exatamente como com um cliente gerado.</span><span class="sxs-lookup"><span data-stu-id="54531-112">Once the channel is created, service operations can be invoked just as with a generated client.</span></span>

```csharp
// Call the Add service operation.
double value1 = 100.00D;
double value2 = 15.99D;
double result = channel.Add(value1, value2);
Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);
```

<span data-ttu-id="54531-113">Para fechar o canal, primeiro ele deve ser convertido em uma interface <xref:System.ServiceModel.IClientChannel>.</span><span class="sxs-lookup"><span data-stu-id="54531-113">To close the channel, it must first be cast to an <xref:System.ServiceModel.IClientChannel> interface.</span></span> <span data-ttu-id="54531-114">Isso ocorre porque o canal como gerado é declarado no aplicativo cliente usando a interface `ICalculator`, que tem métodos como `Add` e `Subtract`, mas não `Close`.</span><span class="sxs-lookup"><span data-stu-id="54531-114">This is because the channel as generated is declared in the client application using the `ICalculator` interface, which has methods like `Add` and `Subtract` but not `Close`.</span></span> <span data-ttu-id="54531-115">O método `Close` se origina na interface <xref:System.ServiceModel.ICommunicationObject>.</span><span class="sxs-lookup"><span data-stu-id="54531-115">The `Close` method originates on the <xref:System.ServiceModel.ICommunicationObject> interface.</span></span>

```csharp
// Close the channel.
 ((IClientChannel)client).Close();
```

<span data-ttu-id="54531-116">Quando você executa o exemplo, as solicitações de operação e as respostas são exibidas na janela do console do cliente.</span><span class="sxs-lookup"><span data-stu-id="54531-116">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="54531-117">Pressione ENTER na janela do cliente para desligar o aplicativo cliente.</span><span class="sxs-lookup"><span data-stu-id="54531-117">Press ENTER in the client window to shut down the client application.</span></span>

```console
Add(100,15.99) = 115.99
Subtract(145,76.54) = 68.46
Multiply(9,81.25) = 731.25
Divide(22,7) = 3.14285714285714

Press <ENTER> to terminate client.
```

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="54531-118">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="54531-118">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="54531-119">Verifique se você executou o [procedimento de configuração única para os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="54531-119">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="54531-120">Para compilar a C# edição do ou Visual Basic .NET da solução, siga as instruções em [criando os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="54531-120">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span> <span data-ttu-id="54531-121">Observe que esse exemplo não habilita a publicação de metadados.</span><span class="sxs-lookup"><span data-stu-id="54531-121">Note that this sample does not enable metadata publishing.</span></span> <span data-ttu-id="54531-122">Primeiro, você deve habilitar a publicação de metadados para este exemplo para regenerar o tipo de cliente.</span><span class="sxs-lookup"><span data-stu-id="54531-122">You must first enable metadata publishing for this sample to regenerate the client type.</span></span>

3. <span data-ttu-id="54531-123">Para executar o exemplo em uma configuração de computador único ou cruzado, siga as instruções em [executando os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="54531-123">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>

### <a name="to-run-the-sample-cross-machine"></a><span data-ttu-id="54531-124">Para executar o exemplo de computador cruzado</span><span class="sxs-lookup"><span data-stu-id="54531-124">To run the sample cross machine</span></span>

1. <span data-ttu-id="54531-125">Substitua "localhost" no código a seguir pelo nome totalmente qualificado do computador que está executando o serviço.</span><span class="sxs-lookup"><span data-stu-id="54531-125">Replace "localhost" in the following code with the fully-qualified name of the machine that is running the service.</span></span>

    ```csharp
    EndpointAddress address = new EndpointAddress("http://localhost/servicemodelsamples/service.svc");
    ```

> [!IMPORTANT]
> <span data-ttu-id="54531-126">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="54531-126">The samples may already be installed on your machine.</span></span> <span data-ttu-id="54531-127">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="54531-127">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="54531-128">Se esse diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos de Windows Workflow Foundation (WF) para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] amostras.</span><span class="sxs-lookup"><span data-stu-id="54531-128">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="54531-129">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="54531-129">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\ChannelFactory`
