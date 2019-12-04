---
title: Sessão
ms.date: 03/30/2017
helpviewer_keywords:
- Sessions
ms.assetid: 36e1db50-008c-4b32-8d09-b56e790b8417
ms.openlocfilehash: e364b539e355f669037983813f9e6d1e0371da1f
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715080"
---
# <a name="session"></a><span data-ttu-id="c5798-102">Sessão</span><span class="sxs-lookup"><span data-stu-id="c5798-102">Session</span></span>
<span data-ttu-id="c5798-103">O exemplo de sessão demonstra como implementar um contrato que requer uma sessão.</span><span class="sxs-lookup"><span data-stu-id="c5798-103">The Session sample demonstrates how to implement a contract that requires a session.</span></span> <span data-ttu-id="c5798-104">Uma sessão fornece contexto para executar várias operações.</span><span class="sxs-lookup"><span data-stu-id="c5798-104">A session provides context for performing multiple operations.</span></span> <span data-ttu-id="c5798-105">Isso permite que um serviço associe o estado a uma determinada sessão, de modo que as operações subsequentes possam usar o estado de uma operação anterior.</span><span class="sxs-lookup"><span data-stu-id="c5798-105">This allows a service to associate state with a given session, such that subsequent operations can use the state of a previous operation.</span></span> <span data-ttu-id="c5798-106">Este exemplo é baseado na [introdução](../../../../docs/framework/wcf/samples/getting-started-sample.md), que implementa um serviço de calculadora.</span><span class="sxs-lookup"><span data-stu-id="c5798-106">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md), which implements a calculator service.</span></span> <span data-ttu-id="c5798-107">O contrato de `ICalculator` foi modificado para permitir que um conjunto de operações aritméticas seja executado, mantendo um resultado em execução.</span><span class="sxs-lookup"><span data-stu-id="c5798-107">The `ICalculator` contract has been modified to allow a set of arithmetic operations to be performed, while keeping a running result.</span></span> <span data-ttu-id="c5798-108">Essa funcionalidade é definida pelo contrato de `ICalculatorSession`.</span><span class="sxs-lookup"><span data-stu-id="c5798-108">This functionality is defined by the `ICalculatorSession` contract.</span></span> <span data-ttu-id="c5798-109">O serviço mantém o estado de um cliente, pois várias operações de serviço são chamadas para executar um cálculo.</span><span class="sxs-lookup"><span data-stu-id="c5798-109">The service maintains the state for a client as multiple service operations are called to perform a calculation.</span></span> <span data-ttu-id="c5798-110">O cliente pode recuperar o resultado atual chamando `Result()` e limpar o resultado para zero chamando `Clear()`.</span><span class="sxs-lookup"><span data-stu-id="c5798-110">The client can retrieve the current result by calling `Result()` and clear the result to zero by calling `Clear()`.</span></span>  
  
 <span data-ttu-id="c5798-111">Neste exemplo, o cliente é um aplicativo de console (. exe) e o serviço é hospedado pelo Serviços de Informações da Internet (IIS).</span><span class="sxs-lookup"><span data-stu-id="c5798-111">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c5798-112">O procedimento de instalação e as instruções de Build para este exemplo estão localizados no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="c5798-112">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="c5798-113">Definir a <xref:System.ServiceModel.SessionMode> do contrato para `Required` garante que quando o contrato for exposto em uma associação específica, a associação dará suporte a sessões.</span><span class="sxs-lookup"><span data-stu-id="c5798-113">Setting the <xref:System.ServiceModel.SessionMode> of the contract to `Required` ensures that when the contract is exposed over a particular binding, the binding supports sessions.</span></span> <span data-ttu-id="c5798-114">Se a associação não oferecer suporte a sessões, uma exceção será lançada.</span><span class="sxs-lookup"><span data-stu-id="c5798-114">If the binding does not support sessions an exception is thrown.</span></span> <span data-ttu-id="c5798-115">A interface `ICalculatorSession` é definida de modo que uma ou mais operações possam ser chamadas, o que modifica um resultado em execução, conforme mostrado no código de exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="c5798-115">The `ICalculatorSession` interface is defined such that one or more operations can be called, which modifies a running result, as shown in the following sample code.</span></span>  
  
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
  
 <span data-ttu-id="c5798-116">O serviço usa uma <xref:System.ServiceModel.InstanceContextMode> de <xref:System.ServiceModel.InstanceContextMode.PerSession> para associar um determinado contexto de instância de serviço a cada sessão de entrada.</span><span class="sxs-lookup"><span data-stu-id="c5798-116">The service uses a <xref:System.ServiceModel.InstanceContextMode> of <xref:System.ServiceModel.InstanceContextMode.PerSession> to bind a given service instance context to each incoming session.</span></span> <span data-ttu-id="c5798-117">Isso permite que o serviço Mantenha o resultado em execução para cada sessão em uma variável de membro local.</span><span class="sxs-lookup"><span data-stu-id="c5798-117">This allows the service to maintain the running result for each session in a local member variable.</span></span>  
  
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
  
 <span data-ttu-id="c5798-118">Quando você executa o exemplo, o cliente faz várias solicitações para o servidor e solicita o resultado, que é exibido na janela do console do cliente.</span><span class="sxs-lookup"><span data-stu-id="c5798-118">When you run the sample, the client makes several requests to the server and requests the result, which it then displays in the client console window.</span></span> <span data-ttu-id="c5798-119">Pressione ENTER na janela do cliente para desligar o cliente.</span><span class="sxs-lookup"><span data-stu-id="c5798-119">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
(((0 + 100) - 50) * 17.65) / 2 = 441.25  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="c5798-120">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="c5798-120">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="c5798-121">Verifique se você executou o [procedimento de configuração única para os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c5798-121">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="c5798-122">Para compilar a C# edição do ou Visual Basic .NET da solução, siga as instruções em [criando os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c5798-122">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="c5798-123">Para executar o exemplo em uma configuração de computador único ou cruzado, siga as instruções em [executando os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c5798-123">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="c5798-124">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="c5798-124">The samples may already be installed on your machine.</span></span> <span data-ttu-id="c5798-125">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="c5798-125">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="c5798-126">Se esse diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos de Windows Workflow Foundation (WF) para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] amostras.</span><span class="sxs-lookup"><span data-stu-id="c5798-126">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="c5798-127">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="c5798-127">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Service\Session`  
