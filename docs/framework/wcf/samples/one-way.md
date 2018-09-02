---
title: Unidirecional
ms.date: 03/30/2017
ms.assetid: 74e3e03d-cd15-4191-a6a5-1efa2dcb9e73
ms.openlocfilehash: 25720285e29641c3c040444cb643af2790f10d3b
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43407765"
---
# <a name="one-way"></a><span data-ttu-id="0fde2-102">Unidirecional</span><span class="sxs-lookup"><span data-stu-id="0fde2-102">One-Way</span></span>
<span data-ttu-id="0fde2-103">Este exemplo demonstra um contato de serviço com operações de serviço unidirecional.</span><span class="sxs-lookup"><span data-stu-id="0fde2-103">This sample demonstrates a service contact with one-way service operations.</span></span> <span data-ttu-id="0fde2-104">O cliente não aguarda a conclusão como é o caso com operações de serviço bidirecional das operações de serviço.</span><span class="sxs-lookup"><span data-stu-id="0fde2-104">The client does not wait for service operations to complete as is the case with two-way service operations.</span></span> <span data-ttu-id="0fde2-105">Este exemplo se baseia a [guia de Introdução](../../../../docs/framework/wcf/samples/getting-started-sample.md) e usa o `wsHttpBinding` associação.</span><span class="sxs-lookup"><span data-stu-id="0fde2-105">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) and uses the `wsHttpBinding` binding.</span></span> <span data-ttu-id="0fde2-106">O serviço neste exemplo é um aplicativo de console auto-hospedado para que você possa observar o serviço que recebe e processa as solicitações.</span><span class="sxs-lookup"><span data-stu-id="0fde2-106">The service in this sample is a self-hosted console application to enable you to observe the service that receives and processes requests.</span></span> <span data-ttu-id="0fde2-107">O cliente também é um aplicativo de console.</span><span class="sxs-lookup"><span data-stu-id="0fde2-107">The client is also a console application.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0fde2-108">As instruções de procedimento e compilação de configuração para este exemplo estão localizadas no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="0fde2-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="0fde2-109">Para criar um contrato de serviço unidirecional, definir seu contrato de serviço, se aplicam a <xref:System.ServiceModel.OperationContractAttribute> de classe para cada operação e defina <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> para `true` conforme mostrado no código de exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="0fde2-109">To create a one-way service contract, define your service contract, apply the <xref:System.ServiceModel.OperationContractAttribute> class to each operation, and set <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> to `true` as shown in the following sample code:</span></span>  
  
```  
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
  
 <span data-ttu-id="0fde2-110">Para demonstrar que o cliente não aguarda a conclusão das operações de serviço, o código de serviço neste exemplo implementa um atraso de cinco segundos, conforme mostrado no código de exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="0fde2-110">To demonstrate that the client does not wait for the service operations to complete, the service code in this sample implements a five-second delay, as shown in the following sample code:</span></span>  
  
```  
/ This service class implements the service contract.  
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
  
 <span data-ttu-id="0fde2-111">Quando o cliente chama o serviço, a chamada retorna sem aguardar a conclusão da operação de serviço.</span><span class="sxs-lookup"><span data-stu-id="0fde2-111">When the client calls the service, the call returns without waiting for the service operation to complete.</span></span>  
  
 <span data-ttu-id="0fde2-112">Quando você executar o exemplo, as atividades do cliente e o serviço são exibidas nas janelas do console de serviço e cliente.</span><span class="sxs-lookup"><span data-stu-id="0fde2-112">When you run the sample, the client and service activities are displayed in both the service and client console windows.</span></span> <span data-ttu-id="0fde2-113">Você pode ver as mensagens de recebimento do serviço do cliente.</span><span class="sxs-lookup"><span data-stu-id="0fde2-113">You can see the service receive messages from the client.</span></span> <span data-ttu-id="0fde2-114">Pressione ENTER em cada janela de console para desligar o serviço e o cliente.</span><span class="sxs-lookup"><span data-stu-id="0fde2-114">Press ENTER in each console window to shut down both the service and the client.</span></span>  
  
 <span data-ttu-id="0fde2-115">O cliente concluir à frente do serviço, demonstrando que um cliente não aguarda a conclusão das operações de serviço unidirecional.</span><span class="sxs-lookup"><span data-stu-id="0fde2-115">The client finishes ahead of the service, demonstrating that a client does not wait for one-way service operations to complete.</span></span> <span data-ttu-id="0fde2-116">A saída do cliente é da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="0fde2-116">The client output is as follows:</span></span>  
  
```  
Add(100,15.99)  
Subtract(145,76.54)  
Multiply(9,81.25)  
Divide(22,7)  
  
Press <ENTER> to terminate client.  
```  
  
 <span data-ttu-id="0fde2-117">A seguinte saída de serviço é mostrada:</span><span class="sxs-lookup"><span data-stu-id="0fde2-117">The following service output is shown:</span></span>  
  
```  
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
>  <span data-ttu-id="0fde2-118">HTTP é, por definição, um protocolo de solicitação/resposta; Quando uma solicitação é feita, uma resposta é retornada.</span><span class="sxs-lookup"><span data-stu-id="0fde2-118">HTTP is, by definition, a request/response protocol; when a request is made, a response is returned.</span></span> <span data-ttu-id="0fde2-119">Isso é verdadeiro mesmo para uma operação de serviço unidirecional que é exposta no HTTP.</span><span class="sxs-lookup"><span data-stu-id="0fde2-119">This is true even for a one-way service operation that is exposed over HTTP.</span></span> <span data-ttu-id="0fde2-120">Quando a operação é chamada, o serviço retornará um código de status HTTP de 202 antes que a operação de serviço foi executada.</span><span class="sxs-lookup"><span data-stu-id="0fde2-120">When the operation is called, the service returns an HTTP status code of 202 before the service operation has executed.</span></span> <span data-ttu-id="0fde2-121">Esse código de status significa que a solicitação foi aceita para processamento, mas o processamento ainda não foi concluído.</span><span class="sxs-lookup"><span data-stu-id="0fde2-121">This status code means that the request has been accepted for processing, but the processing has not yet been completed.</span></span> <span data-ttu-id="0fde2-122">O cliente que chamou a operação bloqueia até que ele recebe a resposta 202 do serviço.</span><span class="sxs-lookup"><span data-stu-id="0fde2-122">The client that called the operation blocks until it receives the 202 response from the service.</span></span> <span data-ttu-id="0fde2-123">Isso pode causar um comportamento inesperado quando várias mensagens unidirecionais são enviadas usando uma associação que está configurada para usar sessões.</span><span class="sxs-lookup"><span data-stu-id="0fde2-123">This can cause some unexpected behavior when multiple one-way messages are sent using a binding that is configured to use sessions.</span></span> <span data-ttu-id="0fde2-124">O `wsHttpBinding` associação usada nesse exemplo é configurada para usar sessões por padrão para estabelecer um contexto de segurança.</span><span class="sxs-lookup"><span data-stu-id="0fde2-124">The `wsHttpBinding` binding used in this sample is configured to use sessions by default to establish a security context.</span></span> <span data-ttu-id="0fde2-125">Por padrão, mensagens em uma sessão são garantidas de chegar na ordem em que elas são enviadas.</span><span class="sxs-lookup"><span data-stu-id="0fde2-125">By default, messages in a session are guaranteed to arrive in the order in which they are sent.</span></span> <span data-ttu-id="0fde2-126">Por isso, quando a segunda mensagem em uma sessão é enviada, ela não é processada até que a primeira mensagem foi processada.</span><span class="sxs-lookup"><span data-stu-id="0fde2-126">Because of this, when the second message in a session is sent, it is not processed until the first message has been processed.</span></span> <span data-ttu-id="0fde2-127">O resultado disso é que o cliente não recebe uma mensagem de resposta 202 até que o processamento da mensagem anterior foi concluído.</span><span class="sxs-lookup"><span data-stu-id="0fde2-127">The result of this is that the client does not receive the 202 response for a message until the processing of the previous message has been completed.</span></span> <span data-ttu-id="0fde2-128">O cliente, portanto, é exibida para o bloco em cada chamada de operação subsequente.</span><span class="sxs-lookup"><span data-stu-id="0fde2-128">The client therefore appears to block on each subsequent operation call.</span></span> <span data-ttu-id="0fde2-129">Para evitar esse comportamento, este exemplo configura o tempo de execução para distribuir mensagens simultaneamente para instâncias distintas para processamento.</span><span class="sxs-lookup"><span data-stu-id="0fde2-129">To avoid this behavior, this sample configures the runtime to dispatch messages concurrently to distinct instances for processing.</span></span> <span data-ttu-id="0fde2-130">Os conjuntos de exemplo <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> para `PerCall` para que cada mensagem pode ser processada por uma instância diferente.</span><span class="sxs-lookup"><span data-stu-id="0fde2-130">The sample sets <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> to `PerCall` so that each message can be processed by a different instance.</span></span> <span data-ttu-id="0fde2-131"><xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> é definido como `Multiple` para permitir que mais de um thread enviar mensagens por vez.</span><span class="sxs-lookup"><span data-stu-id="0fde2-131"><xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> is set to `Multiple` to allow more than one thread to dispatch messages at a time.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="0fde2-132">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="0fde2-132">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="0fde2-133">Certifique-se de que você tenha executado o [procedimento de configuração de uso único para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="0fde2-133">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="0fde2-134">Para compilar a edição em C# ou Visual Basic .NET da solução, siga as instruções em [compilando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="0fde2-134">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="0fde2-135">Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="0fde2-135">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0fde2-136">Execute o serviço antes de executar o cliente e desligar o cliente antes de desligar o serviço.</span><span class="sxs-lookup"><span data-stu-id="0fde2-136">Run the service before you run the client and shut down the client before shutting down the service.</span></span> <span data-ttu-id="0fde2-137">Isso evita uma exceção do cliente quando o cliente não é possível fechar a sessão de segurança corretamente porque o serviço não existe mais.</span><span class="sxs-lookup"><span data-stu-id="0fde2-137">This avoids a client exception when the client cannot close the security session cleanly because the service is gone.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="0fde2-138">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="0fde2-138">The samples may already be installed on your machine.</span></span> <span data-ttu-id="0fde2-139">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="0fde2-139">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="0fde2-140">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="0fde2-140">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="0fde2-141">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="0fde2-141">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Service\Oneway`  
  
## <a name="see-also"></a><span data-ttu-id="0fde2-142">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0fde2-142">See Also</span></span>
