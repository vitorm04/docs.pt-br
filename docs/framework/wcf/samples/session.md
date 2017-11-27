---
title: Session
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Sessions
ms.assetid: 36e1db50-008c-4b32-8d09-b56e790b8417
caps.latest.revision: "31"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: e36666b72d14bbe257cd6ced8a35c360659a91dd
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="session"></a><span data-ttu-id="43eaa-102">Session</span><span class="sxs-lookup"><span data-stu-id="43eaa-102">Session</span></span>
<span data-ttu-id="43eaa-103">A sessão demonstra como implementar um contrato que requer uma sessão.</span><span class="sxs-lookup"><span data-stu-id="43eaa-103">The Session sample demonstrates how to implement a contract that requires a session.</span></span> <span data-ttu-id="43eaa-104">Uma sessão fornece contexto para executar várias operações.</span><span class="sxs-lookup"><span data-stu-id="43eaa-104">A session provides context for performing multiple operations.</span></span> <span data-ttu-id="43eaa-105">Isso permite que um serviço associar a uma determinada sessão, de estado, de modo que as operações subsequentes podem usar o estado de uma operação anterior.</span><span class="sxs-lookup"><span data-stu-id="43eaa-105">This allows a service to associate state with a given session, such that subsequent operations can use the state of a previous operation.</span></span> <span data-ttu-id="43eaa-106">Este exemplo se baseia o [Introdução](../../../../docs/framework/wcf/samples/getting-started-sample.md), que implementa um serviço de cálculo.</span><span class="sxs-lookup"><span data-stu-id="43eaa-106">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md), which implements a calculator service.</span></span> <span data-ttu-id="43eaa-107">O `ICalculator` contrato foi modificado para permitir que um conjunto de operações aritméticas a ser executada, mantendo um resultado de execução.</span><span class="sxs-lookup"><span data-stu-id="43eaa-107">The `ICalculator` contract has been modified to allow a set of arithmetic operations to be performed, while keeping a running result.</span></span> <span data-ttu-id="43eaa-108">Essa funcionalidade é definida pelo `ICalculatorSession` contrato.</span><span class="sxs-lookup"><span data-stu-id="43eaa-108">This functionality is defined by the `ICalculatorSession` contract.</span></span> <span data-ttu-id="43eaa-109">O serviço mantém o estado de um cliente, como várias operações de serviço são chamadas para executar um cálculo.</span><span class="sxs-lookup"><span data-stu-id="43eaa-109">The service maintains the state for a client as multiple service operations are called to perform a calculation.</span></span> <span data-ttu-id="43eaa-110">O cliente pode recuperar o resultado atual chamando `Result()` e desmarque o resultado como zero chamando `Clear()`.</span><span class="sxs-lookup"><span data-stu-id="43eaa-110">The client can retrieve the current result by calling `Result()` and clear the result to zero by calling `Clear()`.</span></span>  
  
 <span data-ttu-id="43eaa-111">Neste exemplo, o cliente é um aplicativo de console (.exe) e o serviço é hospedado por serviços de informações da Internet (IIS).</span><span class="sxs-lookup"><span data-stu-id="43eaa-111">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="43eaa-112">As instruções de procedimento e a compilação de configuração para este exemplo estão localizadas no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="43eaa-112">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="43eaa-113">Definindo o <xref:System.ServiceModel.SessionMode> do contrato para `Required` garante que quando o contrato é exposto por uma associação específica, a associação oferece suporte a sessões.</span><span class="sxs-lookup"><span data-stu-id="43eaa-113">Setting the <xref:System.ServiceModel.SessionMode> of the contract to `Required` ensures that when the contract is exposed over a particular binding, the binding supports sessions.</span></span> <span data-ttu-id="43eaa-114">Se a associação não oferece suporte a sessões uma exceção será lançada.</span><span class="sxs-lookup"><span data-stu-id="43eaa-114">If the binding does not support sessions an exception is thrown.</span></span> <span data-ttu-id="43eaa-115">O `ICalculatorSession` interface é definida, de modo que podem ser chamadas uma ou mais operações, que modifica um resultado de execução, conforme mostrado no código de exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="43eaa-115">The `ICalculatorSession` interface is defined such that one or more operations can be called, which modifies a running result, as shown in the following sample code.</span></span>  
  
```  
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
  
 <span data-ttu-id="43eaa-116">O serviço usa um <xref:System.ServiceModel.InstanceContextMode> de <xref:System.ServiceModel.InstanceContextMode.PerSession> para associar um contexto de instância de serviço fornecido para cada sessão de entrada.</span><span class="sxs-lookup"><span data-stu-id="43eaa-116">The service uses a <xref:System.ServiceModel.InstanceContextMode> of <xref:System.ServiceModel.InstanceContextMode.PerSession> to bind a given service instance context to each incoming session.</span></span> <span data-ttu-id="43eaa-117">Isso permite que o serviço manter o resultado de execução para cada sessão em uma variável de membro local.</span><span class="sxs-lookup"><span data-stu-id="43eaa-117">This allows the service to maintain the running result for each session in a local member variable.</span></span>  
  
```  
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
  
 <span data-ttu-id="43eaa-118">Quando você executar o exemplo, o cliente faz várias solicitações para o servidor e solicita o resultado, que então são exibidos na janela do console do cliente.</span><span class="sxs-lookup"><span data-stu-id="43eaa-118">When you run the sample, the client makes several requests to the server and requests the result, which it then displays in the client console window.</span></span> <span data-ttu-id="43eaa-119">Pressione ENTER na janela do cliente para desligar o cliente.</span><span class="sxs-lookup"><span data-stu-id="43eaa-119">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
(((0 + 100) - 50) * 17.65) / 2 = 441.25  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="43eaa-120">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="43eaa-120">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="43eaa-121">Certifique-se de que você executou o [único procedimento de instalação para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="43eaa-121">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="43eaa-122">Para compilar o c# ou Visual Basic .NET edição da solução, siga as instruções em [compilar os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="43eaa-122">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="43eaa-123">Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="43eaa-123">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="43eaa-124">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="43eaa-124">The samples may already be installed on your machine.</span></span> <span data-ttu-id="43eaa-125">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="43eaa-125">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="43eaa-126">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="43eaa-126">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="43eaa-127">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="43eaa-127">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Service\Session`  
  
## <a name="see-also"></a><span data-ttu-id="43eaa-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="43eaa-128">See Also</span></span>
