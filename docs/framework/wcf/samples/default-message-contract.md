---
title: Contrato padrão de mensagem
ms.date: 03/30/2017
helpviewer_keywords:
- Message Contract
ms.assetid: 5a200b78-1a46-4104-b7fb-da6dbab33893
ms.openlocfilehash: 46b69697616ad7983daed16f8a180a4da7f61a16
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183763"
---
# <a name="default-message-contract"></a><span data-ttu-id="71586-102">Contrato padrão de mensagem</span><span class="sxs-lookup"><span data-stu-id="71586-102">Default Message Contract</span></span>
<span data-ttu-id="71586-103">A amostra Contrato de mensagem padrão demonstra um serviço onde uma mensagem personalizada definida pelo usuário é passada para e a partir de operações de serviço.</span><span class="sxs-lookup"><span data-stu-id="71586-103">The Default Message Contract sample demonstrates a service where a custom user-defined message is passed to and from service operations.</span></span> <span data-ttu-id="71586-104">Esta amostra é baseada no [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) que implementa uma interface de calculadora como um serviço digitado.</span><span class="sxs-lookup"><span data-stu-id="71586-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator interface as a typed service.</span></span> <span data-ttu-id="71586-105">Em vez das operações de serviço individuais para adição, subtração, multiplicação e divisão utilizadas no [Getting Started,](../../../../docs/framework/wcf/samples/getting-started-sample.md)esta amostra passa uma mensagem personalizada que contém tanto os operands quanto o operador, e retorna o resultado do cálculo aritmético.</span><span class="sxs-lookup"><span data-stu-id="71586-105">Instead of the individual service operations for addition, subtraction, multiplication, and division used in the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md), this sample passes a custom message that contains both the operands and the operator, and returns the result of the arithmetic calculation.</span></span>  
  
 <span data-ttu-id="71586-106">O cliente é um programa de console (.exe) e a biblioteca de serviços (.dll) é hospedada pelo Internet Information Services (IIS).</span><span class="sxs-lookup"><span data-stu-id="71586-106">The client is a console program (.exe) and the service library (.dll) is hosted by Internet Information Services (IIS).</span></span> <span data-ttu-id="71586-107">A atividade do cliente é visível na janela do console.</span><span class="sxs-lookup"><span data-stu-id="71586-107">Client activity is visible in the console window.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="71586-108">O procedimento de configuração e as instruções de construção desta amostra estão localizados no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="71586-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="71586-109">No serviço, é definida uma única operação de serviço que `MyMessage`aceita e retorna mensagens personalizadas do tipo .</span><span class="sxs-lookup"><span data-stu-id="71586-109">In the service, a single service operation is defined that accepts and returns custom messages of type `MyMessage`.</span></span> <span data-ttu-id="71586-110">Embora nesta amostra as mensagens de solicitação e resposta sejam do mesmo tipo, elas poderiam, naturalmente, ser contratos de mensagens diferentes, se necessário.</span><span class="sxs-lookup"><span data-stu-id="71586-110">Although in this sample the request and response messages are of the same type, they could of course be different message contracts if necessary.</span></span>  
  
```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface ICalculator  
{  
    [OperationContract(Action="http://test/MyMessage_action",  
                  ReplyAction="http://test/MyMessage_action")]  
    MyMessage Calculate(MyMessage request);  
}  
```  
  
 <span data-ttu-id="71586-111">A `MyMessage` mensagem personalizada é definida em <xref:System.ServiceModel.MessageContractAttribute>uma <xref:System.ServiceModel.MessageHeaderAttribute> <xref:System.ServiceModel.MessageBodyMemberAttribute> classe anotada com , e atributos.</span><span class="sxs-lookup"><span data-stu-id="71586-111">The custom message `MyMessage` is defined in a class annotated with <xref:System.ServiceModel.MessageContractAttribute>, <xref:System.ServiceModel.MessageHeaderAttribute> and <xref:System.ServiceModel.MessageBodyMemberAttribute> attributes.</span></span> <span data-ttu-id="71586-112">Apenas o terceiro construtor é usado nesta amostra.</span><span class="sxs-lookup"><span data-stu-id="71586-112">Only the third constructor is used in this sample.</span></span> <span data-ttu-id="71586-113">O uso de contratos de mensagem permite que você exerça controle total sobre a mensagem SOAP.</span><span class="sxs-lookup"><span data-stu-id="71586-113">Using message contracts allows you to exercise full control over the SOAP message.</span></span> <span data-ttu-id="71586-114">Nesta amostra, <xref:System.ServiceModel.MessageHeaderAttribute> o atributo `Operation` é usado para colocar em um cabeçalho SOAP.</span><span class="sxs-lookup"><span data-stu-id="71586-114">In this sample, the <xref:System.ServiceModel.MessageHeaderAttribute> attribute is used to put `Operation` in a SOAP header.</span></span> <span data-ttu-id="71586-115">Os `N1`operands `N2` , `Result` e o aparecimento dentro <xref:System.ServiceModel.MessageBodyMemberAttribute> do corpo SOAP porque eles têm o atributo aplicado.</span><span class="sxs-lookup"><span data-stu-id="71586-115">The operands `N1`, `N2` and the `Result` appear within the SOAP body because they have the <xref:System.ServiceModel.MessageBodyMemberAttribute> attribute applied.</span></span>  
  
```csharp
[MessageContract]  
public class MyMessage  
{  
    private string operation;  
    private double n1;  
    private double n2;  
    private double result;  
  
    //Constructor - create an empty message.  
  
    public MyMessage() {}  
  
    //Constructor - create a message and populate its members.  
  
    public MyMessage(double n1, double n2, string operation,
                     double result)  
    {  
        this.n1 = n1;  
        this.n2 = n2;  
        this.operation = operation;  
        this.result = result;  
    }  
  
    //Constructor - create a message from another message.  
  
    public MyMessage(MyMessage message)  
    {  
        this.n1 = message.n1;  
        this.n2 = message.n2;  
        this.operation = message.operation;  
        this.result = message.result;  
    }  
  
    [MessageHeader]  
    public string Operation  
    {  
        get { return operation; }  
        set { operation = value; }  
    }  
  
    [MessageBodyMember]  
    public double N1  
    {  
        get { return n1; }  
        set { n1 = value; }  
    }  
  
    [MessageBodyMember]  
    public double N2  
    {  
        get { return n2; }  
        set { n2 = value; }  
    }  
  
    [MessageBodyMember]  
    public double Result  
    {  
        get { return result; }  
        set { result = value; }  
    }  
}  
```  
  
 <span data-ttu-id="71586-116">A classe de implementação `Calculate` contém o código para a operação do serviço.</span><span class="sxs-lookup"><span data-stu-id="71586-116">The implementation class contains the code for the `Calculate` service operation.</span></span> <span data-ttu-id="71586-117">A `CalculateService` classe obtém os operands e o operador da mensagem de solicitação e cria uma mensagem de resposta que contém o resultado do cálculo solicitado, conforme mostrado no código de amostra a seguir.</span><span class="sxs-lookup"><span data-stu-id="71586-117">The `CalculateService` class obtains the operands and operator from the request message and creates a response message that contains the result of the requested calculation, as shown in the following sample code.</span></span>  
  
```csharp
// Service class which implements the service contract.  
public class CalculatorService : ICalculator  
{  
    // Perform a calculation.  
  
    public MyMessage Calculate(MyMessage request)  
    {  
        MyMessage response = new MyMessage(request);  
        switch (request.Operation)  
        {  
            case "+":  
                response.Result = request.N1 + request.N2;  
                break;  
            case "-":  
                response.Result = request.N1 - request.N2;  
                break;  
            case "*":  
                response.Result = request.N1 * request.N2;  
                break;  
            case "/":  
                response.Result = request.N1 / request.N2;  
                break;  
            default:  
                response.Result = 0.0D;  
                break;  
        }  
        return response;  
    }  
}  
```  
  
 <span data-ttu-id="71586-118">O código do cliente gerado para o cliente foi criado com a ferramenta [ServiceModel Metadata Utility Tool (Svcutil.exe).](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)</span><span class="sxs-lookup"><span data-stu-id="71586-118">The generated client code for the client was created with the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) tool.</span></span> <span data-ttu-id="71586-119">A ferramenta cria automaticamente tipos de contrato de mensagem no código do cliente gerado, se necessário.</span><span class="sxs-lookup"><span data-stu-id="71586-119">The tool automatically creates message contract types in the generated client code if necessary.</span></span> <span data-ttu-id="71586-120">A `/messageContract` opção de comando pode ser especificada para forçar a geração de contratos de mensagem.</span><span class="sxs-lookup"><span data-stu-id="71586-120">The `/messageContract` command option may be specified to force the generation of message contracts.</span></span>  
  
```console  
svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" /o:client\generatedClient.cs http://localhost/servicemodelsamples/service.svc/mex  
```  
  
 <span data-ttu-id="71586-121">O código de amostra a `MyMessage` seguir demonstra o cliente usando a mensagem.</span><span class="sxs-lookup"><span data-stu-id="71586-121">The following sample code demonstrates the client using the `MyMessage` message.</span></span>  
  
```csharp
// Create a client with given client endpoint configuration  
CalculatorClient client = new CalculatorClient();  
  
// Perform addition using a typed message.  
  
MyMessage request = new MyMessage()
                    {  
                        N1 = 100D,  
                        N2 = 15.99D,  
                        Operation = "+"  
                    };
MyMessage response = ((ICalculator)client).Calculate(request);  
Console.WriteLine("Add({0},{1}) = {2}", request.N1, request.N2, response.Result);  
```  
  
 <span data-ttu-id="71586-122">Quando você executa a amostra, os cálculos são exibidos na janela do console cliente.</span><span class="sxs-lookup"><span data-stu-id="71586-122">When you run the sample, the calculations are displayed in the client console window.</span></span> <span data-ttu-id="71586-123">Pressione ENTER na janela do cliente para desligar o cliente.</span><span class="sxs-lookup"><span data-stu-id="71586-123">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
 <span data-ttu-id="71586-124">Neste ponto, mensagens personalizadas definidas pelo usuário passaram entre o cliente e a operação do serviço.</span><span class="sxs-lookup"><span data-stu-id="71586-124">At this point, custom user-defined messages have passed between the client and the service operation.</span></span> <span data-ttu-id="71586-125">O contrato de mensagem definia que os operands e os resultados estavam no corpo de mensagem e que o operador estava em um cabeçalho de mensagem.</span><span class="sxs-lookup"><span data-stu-id="71586-125">The message contract defined that the operands and results were in the message body and that the operator was in a message header.</span></span> <span data-ttu-id="71586-126">O registro de mensagens pode ser configurado para observar essa estrutura de mensagem.</span><span class="sxs-lookup"><span data-stu-id="71586-126">Message logging can be configured to observe this message structure.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="71586-127">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="71586-127">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="71586-128">Certifique-se de que você tenha realizado o [procedimento de configuração única para as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="71586-128">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="71586-129">Para construir a edição C# ou Visual Basic .NET da solução, siga as instruções em [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="71586-129">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="71586-130">Para executar a amostra em uma configuração de máquina única ou cruzada, siga as instruções em [Executar as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="71586-130">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="71586-131">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="71586-131">The samples may already be installed on your machine.</span></span> <span data-ttu-id="71586-132">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="71586-132">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="71586-133">Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation).</span><span class="sxs-lookup"><span data-stu-id="71586-133">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="71586-134">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="71586-134">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Message\Default`  
