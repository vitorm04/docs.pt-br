---
title: "Contrato padrão de mensagem"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Message Contract
ms.assetid: 5a200b78-1a46-4104-b7fb-da6dbab33893
caps.latest.revision: "35"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d1219f2c1a173f454827c7450e66d90a500d87e6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="default-message-contract"></a>Contrato padrão de mensagem
O exemplo de contrato de mensagem padrão demonstra um serviço em que uma mensagem personalizada definida pelo usuário é passada para e de operações de serviço. Este exemplo se baseia o [Introdução](../../../../docs/framework/wcf/samples/getting-started-sample.md) que implementa uma interface de cálculo como um serviço com tipo. Em vez de operações de serviço individuais para adição, subtração, multiplicação e divisão usada no [Introdução](../../../../docs/framework/wcf/samples/getting-started-sample.md), este exemplo passa uma mensagem personalizada que contém os operandos e o operador e retorna o resultado do cálculo aritmético.  
  
 O cliente é um programa de console (.exe) e a biblioteca de serviço (. dll) é hospedada por serviços de informações da Internet (IIS). Atividade do cliente estiver visível na janela do console.  
  
> [!NOTE]
>  As instruções de procedimento e a compilação de configuração para este exemplo estão localizadas no final deste tópico.  
  
 No serviço, uma operação de serviço único é definida que aceita e retorna mensagens personalizadas do tipo `MyMessage`. Embora esse exemplo as mensagens de solicitação e resposta são do mesmo tipo, ele pode estar claro contratos de mensagem diferentes se necessário.  
  
```  
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface ICalculator  
{  
    [OperationContract(Action="http://test/MyMessage_action",  
                  ReplyAction="http://test/MyMessage_action")]  
    MyMessage Calculate(MyMessage request);  
}  
```  
  
 A mensagem personalizada `MyMessage` é definido em uma classe anotada com <xref:System.ServiceModel.MessageContractAttribute>, <xref:System.ServiceModel.MessageHeaderAttribute> e <xref:System.ServiceModel.MessageBodyMemberAttribute> atributos. O terceiro construtor somente é usado neste exemplo. Usar contratos de mensagem permite que você tenha controle total sobre a mensagem SOAP. Neste exemplo, o <xref:System.ServiceModel.MessageHeaderAttribute> atributo é usado para colocar `Operation` em um cabeçalho SOAP. Os operandos `N1`, `N2` e `Result` aparecer dentro do corpo SOAP porque eles têm o <xref:System.ServiceModel.MessageBodyMemberAttribute> atributo aplicado.  
  
```  
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
  
 A classe de implementação contém o código para o `Calculate` operação de serviço. O `CalculateService` classe obtém os operandos e o operador da mensagem de solicitação e cria uma mensagem de resposta que contém o resultado do cálculo solicitado, como mostrado no código de exemplo a seguir.  
  
```  
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
  
 O código de cliente gerada para o cliente foi criado com o [Ferramenta Utilitária de metadados ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) ferramenta. A ferramenta cria automaticamente os tipos de contrato de mensagem no código do cliente gerado, se necessário. O `/messageContract` opção de comando pode ser especificada para forçar a geração de contratos de mensagem.  
  
```  
svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" /o:client\generatedClient.cs http://localhost/servicemodelsamples/service.svc/mex  
```  
  
 O código de exemplo a seguir demonstra o cliente usando o `MyMessage` mensagem.  
  
```  
// Create a client with given client endpoint configuration  
CalculatorClient client = new CalculatorClient();  
  
// Perform addition using a typed message.  
  
MyMessage request = new MyMessage();  
request.N1 = 100D;  
request.N2 = 15.99D;  
request.Operation = "+";  
MyMessage response = ((ICalculator)client).Calculate(request);  
Console.WriteLine("Add({0},{1}) = {2}", request.N1, request.N2, response.Result);  
```  
  
 Quando você executar o exemplo, os cálculos são exibidos na janela do console do cliente. Pressione ENTER na janela do cliente para desligar o cliente.  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
 Neste ponto, as mensagens personalizadas definidas pelo usuário passaram entre o cliente e a operação de serviço. O contrato de mensagem definidos os operandos e os resultados foram no corpo da mensagem e que o operador estava em um cabeçalho de mensagem. Log de mensagens pode ser configurado para observar essa estrutura de mensagem.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1.  Certifique-se de que você executou o [único procedimento de instalação para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Para compilar o c# ou Visual Basic .NET edição da solução, siga as instruções em [compilar os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Message\Default`  
  
## <a name="see-also"></a>Consulte também
