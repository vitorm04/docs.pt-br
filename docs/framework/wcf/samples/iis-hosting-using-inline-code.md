---
title: Hospedagem do IIS utilizando código embutido
ms.date: 03/30/2017
helpviewer_keywords:
- Web hosted service
- IIS Hosting Using Inline Code Sample [Windows Communication Foundation]
ms.assetid: 56fe3687-a34b-4661-8e30-b33770f413fa
ms.openlocfilehash: 47d056e35b92654c8e47647c7273c5d69b37bd97
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84594641"
---
# <a name="iis-hosting-using-inline-code"></a><span data-ttu-id="6142f-102">Hospedagem do IIS utilizando código embutido</span><span class="sxs-lookup"><span data-stu-id="6142f-102">IIS Hosting Using Inline Code</span></span>

<span data-ttu-id="6142f-103">Este exemplo demonstra como implementar um serviço hospedado pelo Serviços de Informações da Internet (IIS), onde o código de serviço está contido em linha em um arquivo. svc e é compilado sob demanda.</span><span class="sxs-lookup"><span data-stu-id="6142f-103">This sample demonstrates how to implement a service hosted by Internet Information Services (IIS), where the service code is contained in-line in a .svc file and is compiled on demand.</span></span> <span data-ttu-id="6142f-104">O código de serviço também pode ser implementado diretamente em arquivos de código-fonte localizados no diretório \ App_Code do aplicativo ou compilado no assembly implantado no \bin.</span><span class="sxs-lookup"><span data-stu-id="6142f-104">Service code can also be implemented directly in source code files located in the application's \App_Code directory, or compiled into assembly deployed in \bin.</span></span> <span data-ttu-id="6142f-105">Este exemplo não demonstra essas técnicas.</span><span class="sxs-lookup"><span data-stu-id="6142f-105">This sample does not demonstrate these techniques.</span></span>

> [!NOTE]
> <span data-ttu-id="6142f-106">Os procedimentos de instalação e as instruções de compilação para esse exemplo estão localizadas no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="6142f-106">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="6142f-107">Os exemplos podem mais ser instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="6142f-107">The samples may already be installed on your computer.</span></span> <span data-ttu-id="6142f-108">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="6142f-108">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="6142f-109">Se esse diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos de Windows Workflow Foundation (WF) para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="6142f-109">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="6142f-110">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="6142f-110">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WebHost\InlineCode`

<span data-ttu-id="6142f-111">O exemplo demonstra um serviço típico que implementa um contrato que define um padrão de comunicação de solicitação-resposta.</span><span class="sxs-lookup"><span data-stu-id="6142f-111">The sample demonstrates a typical service that implements a contract that defines a request-reply communication pattern.</span></span> <span data-ttu-id="6142f-112">O serviço é hospedado no IIS e o código do serviço está totalmente contido no arquivo Service. svc.</span><span class="sxs-lookup"><span data-stu-id="6142f-112">The service is hosted in IIS and the service code is entirely contained in the Service.svc file.</span></span> <span data-ttu-id="6142f-113">O serviço é ativado pelo host e compilado sob demanda pela primeira mensagem enviada ao serviço.</span><span class="sxs-lookup"><span data-stu-id="6142f-113">The service is host-activated and compiled on-demand by the first message sent to the service.</span></span> <span data-ttu-id="6142f-114">Não há necessidade de pré-compilação.</span><span class="sxs-lookup"><span data-stu-id="6142f-114">There is no pre-compilation necessary.</span></span> <span data-ttu-id="6142f-115">O serviço implementa um `ICalculator` contrato, conforme definido no código a seguir:</span><span class="sxs-lookup"><span data-stu-id="6142f-115">The service implements an `ICalculator` contract as defined in the following code:</span></span>

```csharp
// Define a service contract.
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]
    public interface ICalculator
{
    [OperationContract]
    double Add(double n1, double n2);
    [OperationContract]
    double Subtract(double n1, double n2);
    [OperationContract]
    double Multiply(double n1, double n2);
    [OperationContract]
    double Divide(double n1, double n2);
}
```

<span data-ttu-id="6142f-116">A implementação do serviço calcula e retorna o resultado apropriado.</span><span class="sxs-lookup"><span data-stu-id="6142f-116">The service implementation calculates and returns the appropriate result.</span></span>

`<%@ServiceHost language=c# Debug="true" Service="Microsoft.ServiceModel.Samples.CalculatorService" %>`

```csharp
// Service class that implements the service contract.
public class CalculatorService : ICalculator
{
    public double Add(double n1, double n2)
    {
        return n1 + n2;
    }
    public double Subtract(double n1, double n2)
    {
        return n1 - n2;
    }
    public double Multiply(double n1, double n2)
    {
        return n1 * n2;
    }
    public double Divide(double n1, double n2)
    {
        return n1 / n2;
    }
}
```

<span data-ttu-id="6142f-117">Quando você executa o exemplo, as solicitações de operação e as respostas são exibidas na janela do console do cliente.</span><span class="sxs-lookup"><span data-stu-id="6142f-117">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="6142f-118">Pressione ENTER na janela do cliente para desligar o cliente.</span><span class="sxs-lookup"><span data-stu-id="6142f-118">Press ENTER in the client window to shut down the client.</span></span>

```console
Add(100,15.99) = 115.99
Subtract(145,76.54) = 68.46
Multiply(9,81.25) = 731.25
Divide(22,7) = 3.14285714285714

Press <ENTER> to terminate client.
```

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="6142f-119">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="6142f-119">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="6142f-120">Verifique se você executou o [procedimento de configuração única para os exemplos de Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="6142f-120">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="6142f-121">Para criar a edição C# ou Visual Basic .NET da solução, siga as instruções em [criando os exemplos de Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="6142f-121">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

3. <span data-ttu-id="6142f-122">Depois que a solução tiver sido criada, execute Setup. bat para configurar o aplicativo ServiceModelSamples no IIS 7,0.</span><span class="sxs-lookup"><span data-stu-id="6142f-122">After the solution has been built, run setup.bat to set up the ServiceModelSamples Application in IIS 7.0.</span></span> <span data-ttu-id="6142f-123">O diretório ServiceModelSamples agora deve aparecer como um aplicativo IIS 7,0.</span><span class="sxs-lookup"><span data-stu-id="6142f-123">The ServiceModelSamples directory should now appear as an IIS 7.0 Application.</span></span>

4. <span data-ttu-id="6142f-124">Para executar o exemplo em uma configuração de computador único ou entre computadores, siga as instruções em [executando os exemplos de Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="6142f-124">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span> <span data-ttu-id="6142f-125">Para obter um exemplo de como criar um aplicativo cliente que pode chamar esse serviço, consulte [como: criar um cliente](../how-to-create-a-wcf-client.md).</span><span class="sxs-lookup"><span data-stu-id="6142f-125">For an example on how to create a client application that can call this service, see [How to: Create a Client](../how-to-create-a-wcf-client.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="6142f-126">Confira também</span><span class="sxs-lookup"><span data-stu-id="6142f-126">See also</span></span>

- <span data-ttu-id="6142f-127">[Hospedagem de AppFabric e persistência Exemplos](https://docs.microsoft.com/previous-versions/appfabric/ff383418(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="6142f-127">[AppFabric Hosting and Persistence Samples](https://docs.microsoft.com/previous-versions/appfabric/ff383418(v=azure.10))</span></span>
