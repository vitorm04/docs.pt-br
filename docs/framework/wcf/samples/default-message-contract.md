---
title: Contrato padrão de mensagem
ms.date: 03/30/2017
helpviewer_keywords:
- Message Contract
ms.assetid: 5a200b78-1a46-4104-b7fb-da6dbab33893
ms.openlocfilehash: 267cdffdc532aaa2b31de835c31d23e93aca8c54
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61990334"
---
# <a name="default-message-contract"></a><span data-ttu-id="738e8-102">Contrato padrão de mensagem</span><span class="sxs-lookup"><span data-stu-id="738e8-102">Default Message Contract</span></span>
<span data-ttu-id="738e8-103">O exemplo de contrato de mensagem padrão demonstra um serviço em que uma mensagem personalizada definida pelo usuário é passada de e para operações de serviço.</span><span class="sxs-lookup"><span data-stu-id="738e8-103">The Default Message Contract sample demonstrates a service where a custom user-defined message is passed to and from service operations.</span></span> <span data-ttu-id="738e8-104">Este exemplo se baseia a [guia de Introdução](../../../../docs/framework/wcf/samples/getting-started-sample.md) que implementa uma interface de Calculadora, como um serviço com tipo.</span><span class="sxs-lookup"><span data-stu-id="738e8-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator interface as a typed service.</span></span> <span data-ttu-id="738e8-105">Em vez das operações de serviço individuais para adição, subtração, multiplicação e divisão usada na [guia de Introdução](../../../../docs/framework/wcf/samples/getting-started-sample.md), este exemplo passa uma mensagem personalizada que contém os operandos e o operador e retorna o resultado do cálculo aritmético.</span><span class="sxs-lookup"><span data-stu-id="738e8-105">Instead of the individual service operations for addition, subtraction, multiplication, and division used in the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md), this sample passes a custom message that contains both the operands and the operator, and returns the result of the arithmetic calculation.</span></span>  
  
 <span data-ttu-id="738e8-106">O cliente é um programa de console (.exe) e a biblioteca de serviço (. dll) é hospedada pelo Internet Information Services (IIS).</span><span class="sxs-lookup"><span data-stu-id="738e8-106">The client is a console program (.exe) and the service library (.dll) is hosted by Internet Information Services (IIS).</span></span> <span data-ttu-id="738e8-107">Atividade do cliente está visível na janela do console.</span><span class="sxs-lookup"><span data-stu-id="738e8-107">Client activity is visible in the console window.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="738e8-108">As instruções de procedimento e compilação de configuração para este exemplo estão localizadas no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="738e8-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="738e8-109">No serviço, uma operação de serviço único é definida que aceita e retorna mensagens personalizadas do tipo `MyMessage`.</span><span class="sxs-lookup"><span data-stu-id="738e8-109">In the service, a single service operation is defined that accepts and returns custom messages of type `MyMessage`.</span></span> <span data-ttu-id="738e8-110">Embora neste exemplo as mensagens de solicitação e resposta são do mesmo tipo, ele pode estar claro contratos de mensagem diferentes se necessário.</span><span class="sxs-lookup"><span data-stu-id="738e8-110">Although in this sample the request and response messages are of the same type, they could of course be different message contracts if necessary.</span></span>  
  
```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface ICalculator  
{  
    [OperationContract(Action="http://test/MyMessage_action",  
                  ReplyAction="http://test/MyMessage_action")]  
    MyMessage Calculate(MyMessage request);  
}  
```  
  
 <span data-ttu-id="738e8-111">A mensagem personalizada `MyMessage` é definido em uma classe anotada com <xref:System.ServiceModel.MessageContractAttribute>, <xref:System.ServiceModel.MessageHeaderAttribute> e <xref:System.ServiceModel.MessageBodyMemberAttribute> atributos.</span><span class="sxs-lookup"><span data-stu-id="738e8-111">The custom message `MyMessage` is defined in a class annotated with <xref:System.ServiceModel.MessageContractAttribute>, <xref:System.ServiceModel.MessageHeaderAttribute> and <xref:System.ServiceModel.MessageBodyMemberAttribute> attributes.</span></span> <span data-ttu-id="738e8-112">Somente o terceiro construtor é usado neste exemplo.</span><span class="sxs-lookup"><span data-stu-id="738e8-112">Only the third constructor is used in this sample.</span></span> <span data-ttu-id="738e8-113">Usar contratos de mensagem permite que você tenha controle total sobre a mensagem SOAP.</span><span class="sxs-lookup"><span data-stu-id="738e8-113">Using message contracts allows you to exercise full control over the SOAP message.</span></span> <span data-ttu-id="738e8-114">Neste exemplo, o <xref:System.ServiceModel.MessageHeaderAttribute> atributo é usado para colocar `Operation` em um cabeçalho SOAP.</span><span class="sxs-lookup"><span data-stu-id="738e8-114">In this sample, the <xref:System.ServiceModel.MessageHeaderAttribute> attribute is used to put `Operation` in a SOAP header.</span></span> <span data-ttu-id="738e8-115">Os operandos `N1`, `N2` e o `Result` aparecem dentro do corpo SOAP porque eles têm o <xref:System.ServiceModel.MessageBodyMemberAttribute> atributo aplicado.</span><span class="sxs-lookup"><span data-stu-id="738e8-115">The operands `N1`, `N2` and the `Result` appear within the SOAP body because they have the <xref:System.ServiceModel.MessageBodyMemberAttribute> attribute applied.</span></span>  
  
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
  
 <span data-ttu-id="738e8-116">A classe de implementação contém o código para o `Calculate` operação de serviço.</span><span class="sxs-lookup"><span data-stu-id="738e8-116">The implementation class contains the code for the `Calculate` service operation.</span></span> <span data-ttu-id="738e8-117">O `CalculateService` classe obtém os operandos e o operador de mensagem de solicitação e cria uma mensagem de resposta que contém o resultado do cálculo solicitado, conforme mostrado no código de exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="738e8-117">The `CalculateService` class obtains the operands and operator from the request message and creates a response message that contains the result of the requested calculation, as shown in the following sample code.</span></span>  
  
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
  
 <span data-ttu-id="738e8-118">O código de cliente gerado para o cliente foi criado com o [ferramenta de utilitário de metadados ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) ferramenta.</span><span class="sxs-lookup"><span data-stu-id="738e8-118">The generated client code for the client was created with the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) tool.</span></span> <span data-ttu-id="738e8-119">A ferramenta cria automaticamente os tipos de contrato de mensagem no código do cliente gerado, se necessário.</span><span class="sxs-lookup"><span data-stu-id="738e8-119">The tool automatically creates message contract types in the generated client code if necessary.</span></span> <span data-ttu-id="738e8-120">O `/messageContract` opção de comando pode ser especificada para forçar a geração de contratos de mensagem.</span><span class="sxs-lookup"><span data-stu-id="738e8-120">The `/messageContract` command option may be specified to force the generation of message contracts.</span></span>  
  
```console  
svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" /o:client\generatedClient.cs http://localhost/servicemodelsamples/service.svc/mex  
```  
  
 <span data-ttu-id="738e8-121">O código de exemplo a seguir demonstra o cliente usando o `MyMessage` mensagem.</span><span class="sxs-lookup"><span data-stu-id="738e8-121">The following sample code demonstrates the client using the `MyMessage` message.</span></span>  
  
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
  
 <span data-ttu-id="738e8-122">Quando você executar o exemplo, os cálculos são exibidos na janela do console de cliente.</span><span class="sxs-lookup"><span data-stu-id="738e8-122">When you run the sample, the calculations are displayed in the client console window.</span></span> <span data-ttu-id="738e8-123">Pressione ENTER na janela do cliente para desligar o cliente.</span><span class="sxs-lookup"><span data-stu-id="738e8-123">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
 <span data-ttu-id="738e8-124">Neste ponto, as mensagens personalizadas definidas pelo usuário passaram entre o cliente e a operação de serviço.</span><span class="sxs-lookup"><span data-stu-id="738e8-124">At this point, custom user-defined messages have passed between the client and the service operation.</span></span> <span data-ttu-id="738e8-125">O contrato de mensagem definidos os operandos e os resultados foram no corpo da mensagem e que o operador estava em um cabeçalho de mensagem.</span><span class="sxs-lookup"><span data-stu-id="738e8-125">The message contract defined that the operands and results were in the message body and that the operator was in a message header.</span></span> <span data-ttu-id="738e8-126">Log de mensagens pode ser configurado para observar a estrutura dessa mensagem.</span><span class="sxs-lookup"><span data-stu-id="738e8-126">Message logging can be configured to observe this message structure.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="738e8-127">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="738e8-127">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="738e8-128">Certifique-se de que você tenha executado o [procedimento de configuração de uso único para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="738e8-128">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="738e8-129">Para compilar a edição em C# ou Visual Basic .NET da solução, siga as instruções em [compilando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="738e8-129">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="738e8-130">Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="738e8-130">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="738e8-131">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="738e8-131">The samples may already be installed on your machine.</span></span> <span data-ttu-id="738e8-132">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="738e8-132">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="738e8-133">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="738e8-133">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="738e8-134">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="738e8-134">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Message\Default`  
