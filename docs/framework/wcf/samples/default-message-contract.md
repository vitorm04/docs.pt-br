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
# <a name="default-message-contract"></a>Contrato padrão de mensagem
A amostra Contrato de mensagem padrão demonstra um serviço onde uma mensagem personalizada definida pelo usuário é passada para e a partir de operações de serviço. Esta amostra é baseada no [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) que implementa uma interface de calculadora como um serviço digitado. Em vez das operações de serviço individuais para adição, subtração, multiplicação e divisão utilizadas no [Getting Started,](../../../../docs/framework/wcf/samples/getting-started-sample.md)esta amostra passa uma mensagem personalizada que contém tanto os operands quanto o operador, e retorna o resultado do cálculo aritmético.  
  
 O cliente é um programa de console (.exe) e a biblioteca de serviços (.dll) é hospedada pelo Internet Information Services (IIS). A atividade do cliente é visível na janela do console.  
  
> [!NOTE]
> O procedimento de configuração e as instruções de construção desta amostra estão localizados no final deste tópico.  
  
 No serviço, é definida uma única operação de serviço que `MyMessage`aceita e retorna mensagens personalizadas do tipo . Embora nesta amostra as mensagens de solicitação e resposta sejam do mesmo tipo, elas poderiam, naturalmente, ser contratos de mensagens diferentes, se necessário.  
  
```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface ICalculator  
{  
    [OperationContract(Action="http://test/MyMessage_action",  
                  ReplyAction="http://test/MyMessage_action")]  
    MyMessage Calculate(MyMessage request);  
}  
```  
  
 A `MyMessage` mensagem personalizada é definida em <xref:System.ServiceModel.MessageContractAttribute>uma <xref:System.ServiceModel.MessageHeaderAttribute> <xref:System.ServiceModel.MessageBodyMemberAttribute> classe anotada com , e atributos. Apenas o terceiro construtor é usado nesta amostra. O uso de contratos de mensagem permite que você exerça controle total sobre a mensagem SOAP. Nesta amostra, <xref:System.ServiceModel.MessageHeaderAttribute> o atributo `Operation` é usado para colocar em um cabeçalho SOAP. Os `N1`operands `N2` , `Result` e o aparecimento dentro <xref:System.ServiceModel.MessageBodyMemberAttribute> do corpo SOAP porque eles têm o atributo aplicado.  
  
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
  
 A classe de implementação `Calculate` contém o código para a operação do serviço. A `CalculateService` classe obtém os operands e o operador da mensagem de solicitação e cria uma mensagem de resposta que contém o resultado do cálculo solicitado, conforme mostrado no código de amostra a seguir.  
  
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
  
 O código do cliente gerado para o cliente foi criado com a ferramenta [ServiceModel Metadata Utility Tool (Svcutil.exe).](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) A ferramenta cria automaticamente tipos de contrato de mensagem no código do cliente gerado, se necessário. A `/messageContract` opção de comando pode ser especificada para forçar a geração de contratos de mensagem.  
  
```console  
svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" /o:client\generatedClient.cs http://localhost/servicemodelsamples/service.svc/mex  
```  
  
 O código de amostra a `MyMessage` seguir demonstra o cliente usando a mensagem.  
  
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
  
 Quando você executa a amostra, os cálculos são exibidos na janela do console cliente. Pressione ENTER na janela do cliente para desligar o cliente.  
  
```console  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
 Neste ponto, mensagens personalizadas definidas pelo usuário passaram entre o cliente e a operação do serviço. O contrato de mensagem definia que os operands e os resultados estavam no corpo de mensagem e que o operador estava em um cabeçalho de mensagem. O registro de mensagens pode ser configurado para observar essa estrutura de mensagem.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1. Certifique-se de que você tenha realizado o [procedimento de configuração única para as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Para construir a edição C# ou Visual Basic .NET da solução, siga as instruções em [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Para executar a amostra em uma configuração de máquina única ou cruzada, siga as instruções em [Executar as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
> Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation). Este exemplo está localizado no seguinte diretório.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Message\Default`  
