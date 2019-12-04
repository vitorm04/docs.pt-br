---
title: Contrato de falha
ms.date: 03/30/2017
ms.assetid: b31b140e-dc3b-408b-b3c7-10b6fe769725
ms.openlocfilehash: d8ea7010bef389b49f68c811565a641a580e230a
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74716951"
---
# <a name="fault-contract"></a><span data-ttu-id="e66c6-102">Contrato de falha</span><span class="sxs-lookup"><span data-stu-id="e66c6-102">Fault Contract</span></span>
<span data-ttu-id="e66c6-103">O exemplo de contrato de falha demonstra como comunicar informações de erro de um serviço para um cliente.</span><span class="sxs-lookup"><span data-stu-id="e66c6-103">The Fault Contract sample demonstrates how to communicate error information from a service to a client.</span></span> <span data-ttu-id="e66c6-104">O exemplo é baseado na [introdução](../../../../docs/framework/wcf/samples/getting-started-sample.md), com algum código adicional adicionado ao serviço para converter uma exceção interna em uma falha.</span><span class="sxs-lookup"><span data-stu-id="e66c6-104">The sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md), with some additional code added to the service to convert an internal exception to a fault.</span></span> <span data-ttu-id="e66c6-105">O cliente tenta executar a divisão por zero para forçar uma condição de erro no serviço.</span><span class="sxs-lookup"><span data-stu-id="e66c6-105">The client attempts to perform division by zero to force an error condition on the service.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e66c6-106">O procedimento de instalação e as instruções de Build para este exemplo estão localizados no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="e66c6-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="e66c6-107">O contrato da calculadora foi modificado para incluir um <xref:System.ServiceModel.FaultContractAttribute>, conforme mostrado no código de exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="e66c6-107">The calculator contract has been modified to include a <xref:System.ServiceModel.FaultContractAttribute> as shown in the following sample code.</span></span>  
  
```csharp
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
  
 <span data-ttu-id="e66c6-108">O atributo <xref:System.ServiceModel.FaultContractAttribute> indica que a operação de `Divide` pode retornar uma falha do tipo `MathFault`.</span><span class="sxs-lookup"><span data-stu-id="e66c6-108">The <xref:System.ServiceModel.FaultContractAttribute> attribute indicates that the `Divide` operation may return a fault of type `MathFault`.</span></span> <span data-ttu-id="e66c6-109">Uma falha pode ser de qualquer tipo que possa ser serializado.</span><span class="sxs-lookup"><span data-stu-id="e66c6-109">A fault can be of any type that can be serialized.</span></span> <span data-ttu-id="e66c6-110">Nesse caso, o `MathFault` é um contrato de dados, da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="e66c6-110">In this case, the `MathFault` is a data contract, as follows:</span></span>  
  
```csharp
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
  
 <span data-ttu-id="e66c6-111">O método `Divide` gera uma exceção de <xref:System.ServiceModel.FaultException%601> quando ocorre uma exceção de divisão por zero, conforme mostrado no código de exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="e66c6-111">The `Divide` method throws a <xref:System.ServiceModel.FaultException%601> exception when a divide by zero exception occurs as shown in the following sample code.</span></span> <span data-ttu-id="e66c6-112">Essa exceção resulta em uma falha que está sendo enviada ao cliente.</span><span class="sxs-lookup"><span data-stu-id="e66c6-112">This exception results in a fault being sent to the client.</span></span>  
  
```csharp
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
  
 <span data-ttu-id="e66c6-113">O código do cliente força um erro solicitando uma divisão por zero.</span><span class="sxs-lookup"><span data-stu-id="e66c6-113">The client code forces an error by requesting a division by zero.</span></span> <span data-ttu-id="e66c6-114">Quando você executa o exemplo, as solicitações de operação e as respostas são exibidas na janela do console do cliente.</span><span class="sxs-lookup"><span data-stu-id="e66c6-114">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="e66c6-115">Você vê a divisão por zero sendo relatada como uma falha.</span><span class="sxs-lookup"><span data-stu-id="e66c6-115">You see the division by zero being reported as a fault.</span></span> <span data-ttu-id="e66c6-116">Pressione ENTER na janela do cliente para desligar o cliente.</span><span class="sxs-lookup"><span data-stu-id="e66c6-116">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
Add(15,3) = 18  
Subtract(145,76) = 69  
Multiply(9,81) = 729  
FaultException<MathFault>: Math fault while doing division. Problem: divide by zero  
  
Press <ENTER> to terminate client.  
```  
  
 <span data-ttu-id="e66c6-117">O cliente faz isso capturando a exceção de `FaultException<MathFault>` apropriada:</span><span class="sxs-lookup"><span data-stu-id="e66c6-117">The client does this by catching the appropriate `FaultException<MathFault>` exception:</span></span>  
  
```csharp
catch (FaultException<MathFault> e)  
{  
    Console.WriteLine("FaultException<MathFault>: Math fault while doing " + e.Detail.operation + ". Problem: " + e.Detail.problemType);  
    client.Abort();  
}  
```  
  
 <span data-ttu-id="e66c6-118">Por padrão, os detalhes de exceções inesperadas não são enviados ao cliente para evitar que os detalhes da implementação do serviço escapem o limite de segurança do serviço.</span><span class="sxs-lookup"><span data-stu-id="e66c6-118">By default, the details of unexpected exceptions are not sent to the client to prevent details of the service implementation from escaping the secure boundary of the service.</span></span> <span data-ttu-id="e66c6-119">`FaultContract` fornece uma maneira de descrever as falhas em um contrato e marcar determinados tipos de exceções conforme apropriado para a transmissão para o cliente.</span><span class="sxs-lookup"><span data-stu-id="e66c6-119">`FaultContract` provides a way to describe faults in a contract and mark certain types of exceptions as appropriate for transmission to the client.</span></span> <span data-ttu-id="e66c6-120">`FaultException<T>` fornece o mecanismo de tempo de execução para o envio de falhas aos consumidores.</span><span class="sxs-lookup"><span data-stu-id="e66c6-120">`FaultException<T>` provides the run-time mechanism for sending faults to consumers.</span></span>  
  
 <span data-ttu-id="e66c6-121">No entanto, é útil ver os detalhes internos de uma falha de serviço durante a depuração.</span><span class="sxs-lookup"><span data-stu-id="e66c6-121">However, it is useful to see the internal details of a service failure when debugging.</span></span> <span data-ttu-id="e66c6-122">Para desativar o comportamento seguro descrito anteriormente, você pode indicar que os detalhes de cada exceção sem tratamento no servidor devem ser incluídos na falha que é enviada ao cliente.</span><span class="sxs-lookup"><span data-stu-id="e66c6-122">To turn off the secure behavior previously described, you can indicate that the details of every unhandled exception on the server should be included in the fault that is sent to the client.</span></span> <span data-ttu-id="e66c6-123">Isso é feito com a definição de <xref:System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults%2A> para `true`.</span><span class="sxs-lookup"><span data-stu-id="e66c6-123">This is accomplished by setting <xref:System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults%2A> to `true`.</span></span> <span data-ttu-id="e66c6-124">Você pode defini-lo no código ou na configuração, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="e66c6-124">You can either set it in code, or in configuration as shown in the following sample.</span></span>  
  
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
  
 <span data-ttu-id="e66c6-125">Além disso, o comportamento deve ser associado ao serviço definindo o atributo `behaviorConfiguration` do serviço no arquivo de configuração como "CalculatorServiceBehavior".</span><span class="sxs-lookup"><span data-stu-id="e66c6-125">Further, the behavior must be associated with the service by setting the `behaviorConfiguration` attribute of the service in the configuration file to "CalculatorServiceBehavior".</span></span>  
  
 <span data-ttu-id="e66c6-126">Para detectar essas falhas no cliente, o <xref:System.ServiceModel.FaultException> não genérico deve ser detectado.</span><span class="sxs-lookup"><span data-stu-id="e66c6-126">To catch such faults on the client, the non-generic <xref:System.ServiceModel.FaultException> must be caught.</span></span>  
  
 <span data-ttu-id="e66c6-127">Esse comportamento só deve ser usado para fins de depuração e nunca deve ser habilitado na produção.</span><span class="sxs-lookup"><span data-stu-id="e66c6-127">This behavior should only be used for debugging purposes and should never be enabled in production.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="e66c6-128">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="e66c6-128">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="e66c6-129">Verifique se você executou o [procedimento de configuração única para os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e66c6-129">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="e66c6-130">Para compilar a C# edição do ou Visual Basic .NET da solução, siga as instruções em [criando os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e66c6-130">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="e66c6-131">Para executar o exemplo em uma configuração de computador único ou cruzado, siga as instruções em [executando os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e66c6-131">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="e66c6-132">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="e66c6-132">The samples may already be installed on your machine.</span></span> <span data-ttu-id="e66c6-133">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="e66c6-133">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="e66c6-134">Se esse diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos de Windows Workflow Foundation (WF) para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] amostras.</span><span class="sxs-lookup"><span data-stu-id="e66c6-134">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="e66c6-135">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="e66c6-135">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Service\Faults`  
