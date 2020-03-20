---
title: Unidirecional
ms.date: 03/30/2017
ms.assetid: 74e3e03d-cd15-4191-a6a5-1efa2dcb9e73
ms.openlocfilehash: 3203762e05c794ed28b65d8fded6972fac1f5820
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183436"
---
# <a name="one-way"></a><span data-ttu-id="ba175-102">Unidirecional</span><span class="sxs-lookup"><span data-stu-id="ba175-102">One-Way</span></span>
<span data-ttu-id="ba175-103">Esta amostra demonstra um contato de serviço com operações de serviço unidirecional.</span><span class="sxs-lookup"><span data-stu-id="ba175-103">This sample demonstrates a service contact with one-way service operations.</span></span> <span data-ttu-id="ba175-104">O cliente não espera que as operações de serviço se completem, como é o caso das operações de serviço bidirecional.</span><span class="sxs-lookup"><span data-stu-id="ba175-104">The client does not wait for service operations to complete as is the case with two-way service operations.</span></span> <span data-ttu-id="ba175-105">Esta amostra é baseada no Getting `wsHttpBinding` [Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) e usa a ligação.</span><span class="sxs-lookup"><span data-stu-id="ba175-105">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) and uses the `wsHttpBinding` binding.</span></span> <span data-ttu-id="ba175-106">O serviço nesta amostra é um aplicativo de console auto-hospedado para permitir que você observe o serviço que recebe e processa solicitações.</span><span class="sxs-lookup"><span data-stu-id="ba175-106">The service in this sample is a self-hosted console application to enable you to observe the service that receives and processes requests.</span></span> <span data-ttu-id="ba175-107">O cliente também é um aplicativo de console.</span><span class="sxs-lookup"><span data-stu-id="ba175-107">The client is also a console application.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ba175-108">O procedimento de configuração e as instruções de construção desta amostra estão localizados no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="ba175-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="ba175-109">Para criar um contrato de serviço unidirecional, <xref:System.ServiceModel.OperationContractAttribute> defina seu contrato <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> `true` de serviço, aplique a classe em cada operação e defina como mostrado no seguinte código de amostra:</span><span class="sxs-lookup"><span data-stu-id="ba175-109">To create a one-way service contract, define your service contract, apply the <xref:System.ServiceModel.OperationContractAttribute> class to each operation, and set <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> to `true` as shown in the following sample code:</span></span>  
  
```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface IOneWayCalculator  
{  
    [OperationContract(IsOneWay=true)]  
    void Add(double n1, double n2);  
    [OperationContract(IsOneWay = true)]  
    void Subtract(double n1, double n2);  
    [OperationContract(IsOneWay = true)]  
    void Multiply(double n1, double n2);  
    [OperationContract(IsOneWay = true)]  
    void Divide(double n1, double n2);  
}  
```  
  
 <span data-ttu-id="ba175-110">Para demonstrar que o cliente não espera que as operações de serviço se completem, o código de serviço nesta amostra implementa um atraso de cinco segundos, como mostrado no seguinte código de amostra:</span><span class="sxs-lookup"><span data-stu-id="ba175-110">To demonstrate that the client does not wait for the service operations to complete, the service code in this sample implements a five-second delay, as shown in the following sample code:</span></span>  
  
```csharp
// This service class implements the service contract.  
// This code writes output to the console window.  
 [ServiceBehavior(ConcurrencyMode = ConcurrencyMode.Multiple,  
    InstanceContextMode = InstanceContextMode.PerCall)]  
public class CalculatorService : IOneWayCalculator  
{  
    public void Add(double n1, double n2)  
    {  
        Console.WriteLine("Received Add({0},{1}) - sleeping", n1, n2);  
        System.Threading.Thread.Sleep(1000 * 5);  
        double result = n1 + n2;  
        Console.WriteLine("Processing Add({0},{1}) - result: {2}", n1, n2, result);  
    }  
    ...  
}  
```  
  
 <span data-ttu-id="ba175-111">Quando o cliente liga para o serviço, a chamada retorna sem esperar que a operação do serviço seja concluída.</span><span class="sxs-lookup"><span data-stu-id="ba175-111">When the client calls the service, the call returns without waiting for the service operation to complete.</span></span>  
  
 <span data-ttu-id="ba175-112">Quando você executa a amostra, as atividades de cliente e serviço são exibidas nas janelas de serviço e console do cliente.</span><span class="sxs-lookup"><span data-stu-id="ba175-112">When you run the sample, the client and service activities are displayed in both the service and client console windows.</span></span> <span data-ttu-id="ba175-113">Você pode ver o serviço receber mensagens do cliente.</span><span class="sxs-lookup"><span data-stu-id="ba175-113">You can see the service receive messages from the client.</span></span> <span data-ttu-id="ba175-114">Pressione ENTER em cada janela do console para desligar o serviço e o cliente.</span><span class="sxs-lookup"><span data-stu-id="ba175-114">Press ENTER in each console window to shut down both the service and the client.</span></span>  
  
 <span data-ttu-id="ba175-115">O cliente termina à frente do serviço, demonstrando que um cliente não espera que as operações de serviço unidirecional se concluam.</span><span class="sxs-lookup"><span data-stu-id="ba175-115">The client finishes ahead of the service, demonstrating that a client does not wait for one-way service operations to complete.</span></span> <span data-ttu-id="ba175-116">A saída do cliente é a seguinte:</span><span class="sxs-lookup"><span data-stu-id="ba175-116">The client output is as follows:</span></span>  
  
```console  
Add(100,15.99)  
Subtract(145,76.54)  
Multiply(9,81.25)  
Divide(22,7)  
  
Press <ENTER> to terminate client.  
```  
  
 <span data-ttu-id="ba175-117">A seguinte saída de serviço é mostrada:</span><span class="sxs-lookup"><span data-stu-id="ba175-117">The following service output is shown:</span></span>  
  
```console  
The service is ready.  
Press <ENTER> to terminate service.  
  
Received Add(100,15.99) - sleeping  
Received Subtract(145,76.54) - sleeping  
Received Multiply(9,81.25) - sleeping  
Received Divide(22,7) - sleeping  
Processing Add(100,15.99) - result: 115.99  
Processing Subtract(145,76.54) - result: 68.46  
Processing Multiply(9,81.25) - result: 731.25  
Processing Divide(22,7) - result: 3.14285714285714  
```  
  
> [!NOTE]
> <span data-ttu-id="ba175-118">HTTP é, por definição, um protocolo de solicitação/resposta; quando uma solicitação é feita, uma resposta é devolvida.</span><span class="sxs-lookup"><span data-stu-id="ba175-118">HTTP is, by definition, a request/response protocol; when a request is made, a response is returned.</span></span> <span data-ttu-id="ba175-119">Isso é verdade mesmo para uma operação de serviço unidirecional que é exposta em HTTP.</span><span class="sxs-lookup"><span data-stu-id="ba175-119">This is true even for a one-way service operation that is exposed over HTTP.</span></span> <span data-ttu-id="ba175-120">Quando a operação é chamada, o serviço retorna um código de status HTTP de 202 antes da operação de serviço ser executada.</span><span class="sxs-lookup"><span data-stu-id="ba175-120">When the operation is called, the service returns an HTTP status code of 202 before the service operation has executed.</span></span> <span data-ttu-id="ba175-121">Este código de status significa que a solicitação foi aceita para processamento, mas o processamento ainda não foi concluído.</span><span class="sxs-lookup"><span data-stu-id="ba175-121">This status code means that the request has been accepted for processing, but the processing has not yet been completed.</span></span> <span data-ttu-id="ba175-122">O cliente que ligou para os blocos da operação até receber a resposta 202 do serviço.</span><span class="sxs-lookup"><span data-stu-id="ba175-122">The client that called the operation blocks until it receives the 202 response from the service.</span></span> <span data-ttu-id="ba175-123">Isso pode causar algum comportamento inesperado quando várias mensagens unidirecionais são enviadas usando uma vinculação configurada para usar sessões.</span><span class="sxs-lookup"><span data-stu-id="ba175-123">This can cause some unexpected behavior when multiple one-way messages are sent using a binding that is configured to use sessions.</span></span> <span data-ttu-id="ba175-124">A `wsHttpBinding` vinculação usada nesta amostra é configurada para usar sessões por padrão para estabelecer um contexto de segurança.</span><span class="sxs-lookup"><span data-stu-id="ba175-124">The `wsHttpBinding` binding used in this sample is configured to use sessions by default to establish a security context.</span></span> <span data-ttu-id="ba175-125">Por padrão, as mensagens em uma sessão são garantidas para chegar na ordem em que são enviadas.</span><span class="sxs-lookup"><span data-stu-id="ba175-125">By default, messages in a session are guaranteed to arrive in the order in which they are sent.</span></span> <span data-ttu-id="ba175-126">Por causa disso, quando a segunda mensagem em uma sessão é enviada, ela não é processada até que a primeira mensagem tenha sido processada.</span><span class="sxs-lookup"><span data-stu-id="ba175-126">Because of this, when the second message in a session is sent, it is not processed until the first message has been processed.</span></span> <span data-ttu-id="ba175-127">O resultado disso é que o cliente não recebe a resposta 202 para uma mensagem até que o processamento da mensagem anterior tenha sido concluído.</span><span class="sxs-lookup"><span data-stu-id="ba175-127">The result of this is that the client does not receive the 202 response for a message until the processing of the previous message has been completed.</span></span> <span data-ttu-id="ba175-128">O cliente, portanto, parece bloquear cada chamada de operação subseqüente.</span><span class="sxs-lookup"><span data-stu-id="ba175-128">The client therefore appears to block on each subsequent operation call.</span></span> <span data-ttu-id="ba175-129">Para evitar esse comportamento, essa amostra configura o tempo de execução para despachar mensagens simultaneamente a instâncias distintas para processamento.</span><span class="sxs-lookup"><span data-stu-id="ba175-129">To avoid this behavior, this sample configures the runtime to dispatch messages concurrently to distinct instances for processing.</span></span> <span data-ttu-id="ba175-130">A amostra <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> `PerCall` define para que cada mensagem possa ser processada por uma instância diferente.</span><span class="sxs-lookup"><span data-stu-id="ba175-130">The sample sets <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> to `PerCall` so that each message can be processed by a different instance.</span></span> <span data-ttu-id="ba175-131"><xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A>é definido `Multiple` para permitir que mais de um segmento despacha mensagens de cada vez.</span><span class="sxs-lookup"><span data-stu-id="ba175-131"><xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> is set to `Multiple` to allow more than one thread to dispatch messages at a time.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="ba175-132">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="ba175-132">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="ba175-133">Certifique-se de que você tenha realizado o [procedimento de configuração única para as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ba175-133">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="ba175-134">Para construir a edição C# ou Visual Basic .NET da solução, siga as instruções em [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ba175-134">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="ba175-135">Para executar a amostra em uma configuração de máquina única ou cruzada, siga as instruções em [Executar as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ba175-135">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ba175-136">Execute o serviço antes de executar o cliente e desligue o cliente antes de desligar o serviço.</span><span class="sxs-lookup"><span data-stu-id="ba175-136">Run the service before you run the client and shut down the client before shutting down the service.</span></span> <span data-ttu-id="ba175-137">Isso evita uma exceção do cliente quando o cliente não pode fechar a sessão de segurança de forma limpa porque o serviço se foi.</span><span class="sxs-lookup"><span data-stu-id="ba175-137">This avoids a client exception when the client cannot close the security session cleanly because the service is gone.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="ba175-138">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="ba175-138">The samples may already be installed on your machine.</span></span> <span data-ttu-id="ba175-139">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="ba175-139">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="ba175-140">Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation).</span><span class="sxs-lookup"><span data-stu-id="ba175-140">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="ba175-141">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="ba175-141">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Service\Oneway`  
