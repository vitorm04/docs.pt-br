---
title: Contrato de falha
ms.date: 03/30/2017
ms.assetid: b31b140e-dc3b-408b-b3c7-10b6fe769725
ms.openlocfilehash: 5b3348f31d239d6bf7e64852ba02010115062669
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43724898"
---
# <a name="fault-contract"></a><span data-ttu-id="6ccf2-102">Contrato de falha</span><span class="sxs-lookup"><span data-stu-id="6ccf2-102">Fault Contract</span></span>
<span data-ttu-id="6ccf2-103">O exemplo de contrato de falha demonstra como se comunicar informações de erro de um serviço para um cliente.</span><span class="sxs-lookup"><span data-stu-id="6ccf2-103">The Fault Contract sample demonstrates how to communicate error information from a service to a client.</span></span> <span data-ttu-id="6ccf2-104">O exemplo se baseia a [guia de Introdução](../../../../docs/framework/wcf/samples/getting-started-sample.md), com algum código adicional adicionado ao serviço para converter uma exceção interna para uma falha.</span><span class="sxs-lookup"><span data-stu-id="6ccf2-104">The sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md), with some additional code added to the service to convert an internal exception to a fault.</span></span> <span data-ttu-id="6ccf2-105">O cliente tenta executar a divisão por zero para forçar uma condição de erro no serviço.</span><span class="sxs-lookup"><span data-stu-id="6ccf2-105">The client attempts to perform division by zero to force an error condition on the service.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6ccf2-106">As instruções de procedimento e compilação de configuração para este exemplo estão localizadas no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="6ccf2-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="6ccf2-107">O contrato de Calculadora foi modificado para incluir um <xref:System.ServiceModel.FaultContractAttribute> conforme mostrado no código de exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="6ccf2-107">The calculator contract has been modified to include a <xref:System.ServiceModel.FaultContractAttribute> as shown in the following sample code.</span></span>  
  
```  
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface ICalculator  
{  
    [OperationContract]  
    int Add(int n1, int n2);  
    [OperationContract]  
    int Subtract(int n1, int n2);  
    [OperationContract]  
    int Multiply(int n1, int n2);  
    [OperationContract]  
    [FaultContract(typeof(MathFault))]  
    int Divide(int n1, int n2);  
}  
```  
  
 <span data-ttu-id="6ccf2-108">O <xref:System.ServiceModel.FaultContractAttribute> atributo indica que o `Divide` operação poderá retornar uma falha do tipo `MathFault`.</span><span class="sxs-lookup"><span data-stu-id="6ccf2-108">The <xref:System.ServiceModel.FaultContractAttribute> attribute indicates that the `Divide` operation may return a fault of type `MathFault`.</span></span> <span data-ttu-id="6ccf2-109">Uma falha pode ser de qualquer tipo que pode ser serializado.</span><span class="sxs-lookup"><span data-stu-id="6ccf2-109">A fault can be of any type that can be serialized.</span></span> <span data-ttu-id="6ccf2-110">Nesse caso, o `MathFault` é um contrato de dados, da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="6ccf2-110">In this case, the `MathFault` is a data contract, as follows:</span></span>  
  
```  
[DataContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public class MathFault  
{      
    private string operation;  
    private string problemType;  
  
    [DataMember]  
    public string Operation  
    {  
        get { return operation; }  
        set { operation = value; }  
    }  
  
    [DataMember]          
    public string ProblemType  
    {  
        get { return problemType; }  
        set { problemType = value; }  
    }  
}  
```  
  
 <span data-ttu-id="6ccf2-111">O `Divide` método lança um <xref:System.ServiceModel.FaultException%601> ocorrerá uma exceção quando uma divisão por zero exceção conforme mostrado no código de exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="6ccf2-111">The `Divide` method throws a <xref:System.ServiceModel.FaultException%601> exception when a divide by zero exception occurs as shown in the following sample code.</span></span> <span data-ttu-id="6ccf2-112">Essa exceção resulta em uma falha que está sendo enviada ao cliente.</span><span class="sxs-lookup"><span data-stu-id="6ccf2-112">This exception results in a fault being sent to the client.</span></span>  
  
```  
public int Divide(int n1, int n2)  
{  
    try  
    {  
        return n1 / n2;  
    }  
    catch (DivideByZeroException)  
    {  
        MathFault mf = new MathFault();  
        mf.operation = "division";  
        mf.problemType = "divide by zero";  
        throw new FaultException<MathFault>(mf);  
    }  
}  
```  
  
 <span data-ttu-id="6ccf2-113">O código do cliente força um erro ao solicitar uma divisão por zero.</span><span class="sxs-lookup"><span data-stu-id="6ccf2-113">The client code forces an error by requesting a division by zero.</span></span> <span data-ttu-id="6ccf2-114">Quando você executar o exemplo, as respostas e solicitações de operação são exibidas na janela do console de cliente.</span><span class="sxs-lookup"><span data-stu-id="6ccf2-114">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="6ccf2-115">Você pode ver a divisão por zero, que está sendo relatado como uma falha.</span><span class="sxs-lookup"><span data-stu-id="6ccf2-115">You see the division by zero being reported as a fault.</span></span> <span data-ttu-id="6ccf2-116">Pressione ENTER na janela do cliente para desligar o cliente.</span><span class="sxs-lookup"><span data-stu-id="6ccf2-116">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Add(15,3) = 18  
Subtract(145,76) = 69  
Multiply(9,81) = 729  
FaultException<MathFault>: Math fault while doing division. Problem: divide by zero  
  
Press <ENTER> to terminate client.  
```  
  
 <span data-ttu-id="6ccf2-117">O cliente faz isso capturando apropriado `FaultException<MathFault>` exceção:</span><span class="sxs-lookup"><span data-stu-id="6ccf2-117">The client does this by catching the appropriate `FaultException<MathFault>` exception:</span></span>  
  
```  
catch (FaultException<MathFault> e)  
{  
    Console.WriteLine("FaultException<MathFault>: Math fault while doing " + e.Detail.operation + ". Problem: " + e.Detail.problemType);  
    client.Abort();  
}  
```  
  
 <span data-ttu-id="6ccf2-118">Por padrão, os detalhes de exceções inesperadas não são enviados ao cliente para impedir que os detalhes da implementação do serviço de escape de limite seguro do serviço.</span><span class="sxs-lookup"><span data-stu-id="6ccf2-118">By default, the details of unexpected exceptions are not sent to the client to prevent details of the service implementation from escaping the secure boundary of the service.</span></span> <span data-ttu-id="6ccf2-119">`FaultContract` Fornece uma maneira de descrever as falhas em um contrato e marcar a determinados tipos de exceções, conforme apropriado para a transmissão para o cliente.</span><span class="sxs-lookup"><span data-stu-id="6ccf2-119">`FaultContract` provides a way to describe faults in a contract and mark certain types of exceptions as appropriate for transmission to the client.</span></span> <span data-ttu-id="6ccf2-120">`FaultException<T>` fornece o mecanismo de tempo de execução para o envio de falhas para consumidores.</span><span class="sxs-lookup"><span data-stu-id="6ccf2-120">`FaultException<T>` provides the run-time mechanism for sending faults to consumers.</span></span>  
  
 <span data-ttu-id="6ccf2-121">No entanto, é útil ver os detalhes internos de uma falha de serviço durante a depuração.</span><span class="sxs-lookup"><span data-stu-id="6ccf2-121">However, it is useful to see the internal details of a service failure when debugging.</span></span> <span data-ttu-id="6ccf2-122">Para desativar o comportamento seguro descrito anteriormente, você pode indicar que os detalhes de cada exceção sem tratamento no servidor devem ser incluídos na falha que é enviada ao cliente.</span><span class="sxs-lookup"><span data-stu-id="6ccf2-122">To turn off the secure behavior previously described, you can indicate that the details of every unhandled exception on the server should be included in the fault that is sent to the client.</span></span> <span data-ttu-id="6ccf2-123">Isso é feito definindo <xref:System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults%2A> para `true`.</span><span class="sxs-lookup"><span data-stu-id="6ccf2-123">This is accomplished by setting <xref:System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults%2A> to `true`.</span></span> <span data-ttu-id="6ccf2-124">Você pode defini-lo no código ou na configuração, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="6ccf2-124">You can either set it in code, or in configuration as shown in the following sample.</span></span>  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
    <behavior name="CalculatorServiceBehavior">  
      <serviceMetadata httpGetEnabled="True"/>  
      <serviceDebug includeExceptionDetailInFaults="True" />  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
 <span data-ttu-id="6ccf2-125">Além disso, o comportamento deve ser associado ao serviço, definindo o `behaviorConfiguration` atributo do serviço no arquivo de configuração para "CalculatorServiceBehavior".</span><span class="sxs-lookup"><span data-stu-id="6ccf2-125">Further, the behavior must be associated with the service by setting the `behaviorConfiguration` attribute of the service in the configuration file to "CalculatorServiceBehavior".</span></span>  
  
 <span data-ttu-id="6ccf2-126">Para capturar essas falhas no cliente, a não-genérica <xref:System.ServiceModel.FaultException> deve ser capturada.</span><span class="sxs-lookup"><span data-stu-id="6ccf2-126">To catch such faults on the client, the non-generic <xref:System.ServiceModel.FaultException> must be caught.</span></span>  
  
 <span data-ttu-id="6ccf2-127">Esse comportamento só deve ser usado para fins de depuração e nunca deve ser habilitado em produção.</span><span class="sxs-lookup"><span data-stu-id="6ccf2-127">This behavior should only be used for debugging purposes and should never be enabled in production.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="6ccf2-128">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="6ccf2-128">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="6ccf2-129">Certifique-se de que você tenha executado o [procedimento de configuração de uso único para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="6ccf2-129">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="6ccf2-130">Para compilar a edição em C# ou Visual Basic .NET da solução, siga as instruções em [compilando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="6ccf2-130">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="6ccf2-131">Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="6ccf2-131">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="6ccf2-132">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="6ccf2-132">The samples may already be installed on your machine.</span></span> <span data-ttu-id="6ccf2-133">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="6ccf2-133">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="6ccf2-134">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="6ccf2-134">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="6ccf2-135">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="6ccf2-135">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Service\Faults`  
  
## <a name="see-also"></a><span data-ttu-id="6ccf2-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6ccf2-136">See Also</span></span>
