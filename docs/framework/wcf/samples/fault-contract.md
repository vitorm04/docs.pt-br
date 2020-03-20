---
title: Contrato de falha
ms.date: 03/30/2017
ms.assetid: b31b140e-dc3b-408b-b3c7-10b6fe769725
ms.openlocfilehash: c8e93f73d150132c9d6750b81ba2ade944808d40
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183660"
---
# <a name="fault-contract"></a><span data-ttu-id="b4f25-102">Contrato de falha</span><span class="sxs-lookup"><span data-stu-id="b4f25-102">Fault Contract</span></span>
<span data-ttu-id="b4f25-103">A amostra Contrato de Falha demonstra como comunicar informações de erro de um serviço para um cliente.</span><span class="sxs-lookup"><span data-stu-id="b4f25-103">The Fault Contract sample demonstrates how to communicate error information from a service to a client.</span></span> <span data-ttu-id="b4f25-104">A amostra é baseada no [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md), com algum código adicional adicionado ao serviço para converter uma exceção interna a uma falha.</span><span class="sxs-lookup"><span data-stu-id="b4f25-104">The sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md), with some additional code added to the service to convert an internal exception to a fault.</span></span> <span data-ttu-id="b4f25-105">O cliente tenta executar a divisão por zero para forçar uma condição de erro no serviço.</span><span class="sxs-lookup"><span data-stu-id="b4f25-105">The client attempts to perform division by zero to force an error condition on the service.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b4f25-106">O procedimento de configuração e as instruções de construção desta amostra estão localizados no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="b4f25-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="b4f25-107">O contrato da calculadora foi <xref:System.ServiceModel.FaultContractAttribute> modificado para incluir um como mostrado no código de amostra a seguir.</span><span class="sxs-lookup"><span data-stu-id="b4f25-107">The calculator contract has been modified to include a <xref:System.ServiceModel.FaultContractAttribute> as shown in the following sample code.</span></span>  
  
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
  
 <span data-ttu-id="b4f25-108">O <xref:System.ServiceModel.FaultContractAttribute> atributo `Divide` indica que a operação `MathFault`pode retornar uma falha do tipo .</span><span class="sxs-lookup"><span data-stu-id="b4f25-108">The <xref:System.ServiceModel.FaultContractAttribute> attribute indicates that the `Divide` operation may return a fault of type `MathFault`.</span></span> <span data-ttu-id="b4f25-109">Uma falha pode ser de qualquer tipo que possa ser serializada.</span><span class="sxs-lookup"><span data-stu-id="b4f25-109">A fault can be of any type that can be serialized.</span></span> <span data-ttu-id="b4f25-110">Neste caso, `MathFault` é um contrato de dados, como segue:</span><span class="sxs-lookup"><span data-stu-id="b4f25-110">In this case, the `MathFault` is a data contract, as follows:</span></span>  
  
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
  
 <span data-ttu-id="b4f25-111">O `Divide` método <xref:System.ServiceModel.FaultException%601> lança uma exceção quando uma divisão por exceção zero ocorre como mostrado no código de amostra a seguir.</span><span class="sxs-lookup"><span data-stu-id="b4f25-111">The `Divide` method throws a <xref:System.ServiceModel.FaultException%601> exception when a divide by zero exception occurs as shown in the following sample code.</span></span> <span data-ttu-id="b4f25-112">Essa exceção resulta em uma falha sendo enviada ao cliente.</span><span class="sxs-lookup"><span data-stu-id="b4f25-112">This exception results in a fault being sent to the client.</span></span>  
  
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
  
 <span data-ttu-id="b4f25-113">O código do cliente força um erro solicitando uma divisão por zero.</span><span class="sxs-lookup"><span data-stu-id="b4f25-113">The client code forces an error by requesting a division by zero.</span></span> <span data-ttu-id="b4f25-114">Quando você executa a amostra, as solicitações e respostas da operação são exibidas na janela do console cliente.</span><span class="sxs-lookup"><span data-stu-id="b4f25-114">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="b4f25-115">Você vê a divisão por zero sendo relatada como uma falha.</span><span class="sxs-lookup"><span data-stu-id="b4f25-115">You see the division by zero being reported as a fault.</span></span> <span data-ttu-id="b4f25-116">Pressione ENTER na janela do cliente para desligar o cliente.</span><span class="sxs-lookup"><span data-stu-id="b4f25-116">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
Add(15,3) = 18  
Subtract(145,76) = 69  
Multiply(9,81) = 729  
FaultException<MathFault>: Math fault while doing division. Problem: divide by zero  
  
Press <ENTER> to terminate client.  
```  
  
 <span data-ttu-id="b4f25-117">O cliente faz isso `FaultException<MathFault>` pegando a exceção apropriada:</span><span class="sxs-lookup"><span data-stu-id="b4f25-117">The client does this by catching the appropriate `FaultException<MathFault>` exception:</span></span>  
  
```csharp
catch (FaultException<MathFault> e)  
{  
    Console.WriteLine("FaultException<MathFault>: Math fault while doing " + e.Detail.operation + ". Problem: " + e.Detail.problemType);  
    client.Abort();  
}  
```  
  
 <span data-ttu-id="b4f25-118">Por padrão, os detalhes de exceções inesperadas não são enviados ao cliente para evitar que detalhes da implementação do serviço escapem do limite seguro do serviço.</span><span class="sxs-lookup"><span data-stu-id="b4f25-118">By default, the details of unexpected exceptions are not sent to the client to prevent details of the service implementation from escaping the secure boundary of the service.</span></span> <span data-ttu-id="b4f25-119">`FaultContract`fornece uma maneira de descrever falhas em um contrato e marcar certos tipos de exceções conforme apropriado para transmissão ao cliente.</span><span class="sxs-lookup"><span data-stu-id="b4f25-119">`FaultContract` provides a way to describe faults in a contract and mark certain types of exceptions as appropriate for transmission to the client.</span></span> <span data-ttu-id="b4f25-120">`FaultException<T>`fornece o mecanismo de tempo de execução para o envio de falhas aos consumidores.</span><span class="sxs-lookup"><span data-stu-id="b4f25-120">`FaultException<T>` provides the run-time mechanism for sending faults to consumers.</span></span>  
  
 <span data-ttu-id="b4f25-121">No entanto, é útil ver os detalhes internos de uma falha de serviço ao depurar.</span><span class="sxs-lookup"><span data-stu-id="b4f25-121">However, it is useful to see the internal details of a service failure when debugging.</span></span> <span data-ttu-id="b4f25-122">Para desativar o comportamento seguro descrito anteriormente, você pode indicar que os detalhes de cada exceção não tratada no servidor devem ser incluídos na falha enviada ao cliente.</span><span class="sxs-lookup"><span data-stu-id="b4f25-122">To turn off the secure behavior previously described, you can indicate that the details of every unhandled exception on the server should be included in the fault that is sent to the client.</span></span> <span data-ttu-id="b4f25-123">Isso é feito <xref:System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults%2A> `true`definindo para .</span><span class="sxs-lookup"><span data-stu-id="b4f25-123">This is accomplished by setting <xref:System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults%2A> to `true`.</span></span> <span data-ttu-id="b4f25-124">Você pode defini-lo em código ou na configuração, como mostrado na amostra a seguir.</span><span class="sxs-lookup"><span data-stu-id="b4f25-124">You can either set it in code, or in configuration as shown in the following sample.</span></span>  
  
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
  
 <span data-ttu-id="b4f25-125">Além disso, o comportamento deve ser `behaviorConfiguration` associado ao serviço definindo o atributo do serviço no arquivo de configuração para "CalculadoraServiceBehavior".</span><span class="sxs-lookup"><span data-stu-id="b4f25-125">Further, the behavior must be associated with the service by setting the `behaviorConfiguration` attribute of the service in the configuration file to "CalculatorServiceBehavior".</span></span>  
  
 <span data-ttu-id="b4f25-126">Para pegar tais falhas no cliente, <xref:System.ServiceModel.FaultException> o não genérico deve ser pego.</span><span class="sxs-lookup"><span data-stu-id="b4f25-126">To catch such faults on the client, the non-generic <xref:System.ServiceModel.FaultException> must be caught.</span></span>  
  
 <span data-ttu-id="b4f25-127">Esse comportamento só deve ser utilizado para fins de depuração e nunca deve ser habilitado na produção.</span><span class="sxs-lookup"><span data-stu-id="b4f25-127">This behavior should only be used for debugging purposes and should never be enabled in production.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="b4f25-128">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="b4f25-128">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="b4f25-129">Certifique-se de que você tenha realizado o [procedimento de configuração única para as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="b4f25-129">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="b4f25-130">Para construir a edição C# ou Visual Basic .NET da solução, siga as instruções em [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="b4f25-130">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="b4f25-131">Para executar a amostra em uma configuração de máquina única ou cruzada, siga as instruções em [Executar as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="b4f25-131">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="b4f25-132">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="b4f25-132">The samples may already be installed on your machine.</span></span> <span data-ttu-id="b4f25-133">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="b4f25-133">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="b4f25-134">Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation).</span><span class="sxs-lookup"><span data-stu-id="b4f25-134">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="b4f25-135">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="b4f25-135">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Service\Faults`  
