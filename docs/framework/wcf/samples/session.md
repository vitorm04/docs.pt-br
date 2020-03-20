---
title: Session
ms.date: 03/30/2017
helpviewer_keywords:
- Sessions
ms.assetid: 36e1db50-008c-4b32-8d09-b56e790b8417
ms.openlocfilehash: 85f1034999fc4cd36075c49bd8f4631bbd283679
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183360"
---
# <a name="session"></a><span data-ttu-id="9207e-102">Session</span><span class="sxs-lookup"><span data-stu-id="9207e-102">Session</span></span>
<span data-ttu-id="9207e-103">A amostra de Sessão demonstra como implementar um contrato que requer uma sessão.</span><span class="sxs-lookup"><span data-stu-id="9207e-103">The Session sample demonstrates how to implement a contract that requires a session.</span></span> <span data-ttu-id="9207e-104">Uma sessão fornece contexto para a realização de múltiplas operações.</span><span class="sxs-lookup"><span data-stu-id="9207e-104">A session provides context for performing multiple operations.</span></span> <span data-ttu-id="9207e-105">Isso permite que um serviço associe o estado a uma determinada sessão, de tal forma que as operações subsequentes possam usar o estado de uma operação anterior.</span><span class="sxs-lookup"><span data-stu-id="9207e-105">This allows a service to associate state with a given session, such that subsequent operations can use the state of a previous operation.</span></span> <span data-ttu-id="9207e-106">Esta amostra é baseada no [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md), que implementa um serviço de calculadora.</span><span class="sxs-lookup"><span data-stu-id="9207e-106">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md), which implements a calculator service.</span></span> <span data-ttu-id="9207e-107">O `ICalculator` contrato foi modificado para permitir que um conjunto de operações aritméticas seja realizado, mantendo um resultado em execução.</span><span class="sxs-lookup"><span data-stu-id="9207e-107">The `ICalculator` contract has been modified to allow a set of arithmetic operations to be performed, while keeping a running result.</span></span> <span data-ttu-id="9207e-108">Essa funcionalidade é definida `ICalculatorSession` pelo contrato.</span><span class="sxs-lookup"><span data-stu-id="9207e-108">This functionality is defined by the `ICalculatorSession` contract.</span></span> <span data-ttu-id="9207e-109">O serviço mantém o estado para um cliente, pois várias operações de serviço são chamadas para realizar um cálculo.</span><span class="sxs-lookup"><span data-stu-id="9207e-109">The service maintains the state for a client as multiple service operations are called to perform a calculation.</span></span> <span data-ttu-id="9207e-110">O cliente pode recuperar o `Result()` resultado atual ligando `Clear()`e limpar o resultado para zero ligando .</span><span class="sxs-lookup"><span data-stu-id="9207e-110">The client can retrieve the current result by calling `Result()` and clear the result to zero by calling `Clear()`.</span></span>  
  
 <span data-ttu-id="9207e-111">Nesta amostra, o cliente é um aplicativo de console (.exe) e o serviço é hospedado pelo Internet Information Services (IIS).</span><span class="sxs-lookup"><span data-stu-id="9207e-111">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9207e-112">O procedimento de configuração e as instruções de construção desta amostra estão localizados no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="9207e-112">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="9207e-113">Definir <xref:System.ServiceModel.SessionMode> o contrato `Required` para garantir que, quando o contrato estiver exposto sobre uma ligação específica, a vinculação suporta sessões.</span><span class="sxs-lookup"><span data-stu-id="9207e-113">Setting the <xref:System.ServiceModel.SessionMode> of the contract to `Required` ensures that when the contract is exposed over a particular binding, the binding supports sessions.</span></span> <span data-ttu-id="9207e-114">Se a vinculação não suportar sessões, uma exceção será lançada.</span><span class="sxs-lookup"><span data-stu-id="9207e-114">If the binding does not support sessions an exception is thrown.</span></span> <span data-ttu-id="9207e-115">A `ICalculatorSession` interface é definida de forma que uma ou mais operações possam ser chamadas, o que modifica um resultado em execução, como mostrado no código de amostra a seguir.</span><span class="sxs-lookup"><span data-stu-id="9207e-115">The `ICalculatorSession` interface is defined such that one or more operations can be called, which modifies a running result, as shown in the following sample code.</span></span>  
  
```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples", SessionMode=SessionMode.Required)]  
public interface ICalculatorSession  
{  
    [OperationContract(IsOneWay=true)]  
    void Clear();  
    [OperationContract(IsOneWay = true)]  
    void AddTo(double n);  
    [OperationContract(IsOneWay = true)]  
    void SubtractFrom(double n);  
    [OperationContract(IsOneWay = true)]  
    void MultiplyBy(double n);  
    [OperationContract(IsOneWay = true)]  
    void DivideBy(double n);  
    [OperationContract]  
    double Result();  
}  
```  
  
 <span data-ttu-id="9207e-116">O serviço <xref:System.ServiceModel.InstanceContextMode> usa <xref:System.ServiceModel.InstanceContextMode.PerSession> um de para vincular um determinado contexto de instância de serviço a cada sessão recebida.</span><span class="sxs-lookup"><span data-stu-id="9207e-116">The service uses a <xref:System.ServiceModel.InstanceContextMode> of <xref:System.ServiceModel.InstanceContextMode.PerSession> to bind a given service instance context to each incoming session.</span></span> <span data-ttu-id="9207e-117">Isso permite que o serviço mantenha o resultado de execução de cada sessão em uma variável de membro local.</span><span class="sxs-lookup"><span data-stu-id="9207e-117">This allows the service to maintain the running result for each session in a local member variable.</span></span>  
  
```csharp
[ServiceBehavior(InstanceContextMode=InstanceContextMode.PerSession)]  
public class CalculatorService : ICalculatorSession  
{  
    double result = 0.0D;  
  
    public void Clear()  
    {  result = 0.0D; }  
  
    public void AddTo(double n)  
    {  result += n;   }  
  
    public void SubtractFrom(double n)  
    {  result -= n;   }  
  
    public void MultiplyBy(double n)  
    {  result *= n;   }  
  
    public void DivideBy(double n)  
    {  result /= n;   }  
  
    public double Result()  
    {  return result; }  
}  
```  
  
 <span data-ttu-id="9207e-118">Quando você executa a amostra, o cliente faz várias solicitações ao servidor e solicita o resultado, que ele exibe na janela do console cliente.</span><span class="sxs-lookup"><span data-stu-id="9207e-118">When you run the sample, the client makes several requests to the server and requests the result, which it then displays in the client console window.</span></span> <span data-ttu-id="9207e-119">Pressione ENTER na janela do cliente para desligar o cliente.</span><span class="sxs-lookup"><span data-stu-id="9207e-119">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
(((0 + 100) - 50) * 17.65) / 2 = 441.25  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="9207e-120">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="9207e-120">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="9207e-121">Certifique-se de que você tenha realizado o [procedimento de configuração única para as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="9207e-121">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="9207e-122">Para construir a edição C# ou Visual Basic .NET da solução, siga as instruções em [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="9207e-122">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="9207e-123">Para executar a amostra em uma configuração de máquina única ou cruzada, siga as instruções em [Executar as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="9207e-123">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="9207e-124">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="9207e-124">The samples may already be installed on your machine.</span></span> <span data-ttu-id="9207e-125">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="9207e-125">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="9207e-126">Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation).</span><span class="sxs-lookup"><span data-stu-id="9207e-126">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="9207e-127">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="9207e-127">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Service\Session`  
