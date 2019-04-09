---
title: Unidirecional
ms.date: 03/30/2017
ms.assetid: 74e3e03d-cd15-4191-a6a5-1efa2dcb9e73
ms.openlocfilehash: 53718b6523bb76e30233540323d5f4f87d466fed
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59131320"
---
# <a name="one-way"></a>Unidirecional
Este exemplo demonstra um contato de serviço com operações de serviço unidirecional. O cliente não aguarda a conclusão como é o caso com operações de serviço bidirecional das operações de serviço. Este exemplo se baseia a [guia de Introdução](../../../../docs/framework/wcf/samples/getting-started-sample.md) e usa o `wsHttpBinding` associação. O serviço neste exemplo é um aplicativo de console auto-hospedado para que você possa observar o serviço que recebe e processa as solicitações. O cliente também é um aplicativo de console.  
  
> [!NOTE]
>  As instruções de procedimento e compilação de configuração para este exemplo estão localizadas no final deste tópico.  
  
 Para criar um contrato de serviço unidirecional, definir seu contrato de serviço, se aplicam a <xref:System.ServiceModel.OperationContractAttribute> de classe para cada operação e defina <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> para `true` conforme mostrado no código de exemplo a seguir:  
  
```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface IOneWayCalculator  
{  
    [OperationContract(IsOneWay=true)]  
    void Add(double n1, double n2);  
    [OperationContract(IsOneWay = true)]  
    void Subtract(double n1, double n2);  
    [OperationContract(IsOneWay = true)]  
    void Multiply(double n1, double n2);  
    [OperationContract(IsOneWay = true)]  
    void Divide(double n1, double n2);  
}  
```  
  
 Para demonstrar que o cliente não aguarda a conclusão das operações de serviço, o código de serviço neste exemplo implementa um atraso de cinco segundos, conforme mostrado no código de exemplo a seguir:  
  
```csharp
// This service class implements the service contract.  
// This code writes output to the console window.  
 [ServiceBehavior(ConcurrencyMode = ConcurrencyMode.Multiple,  
    InstanceContextMode = InstanceContextMode.PerCall)]  
public class CalculatorService : IOneWayCalculator  
{  
    public void Add(double n1, double n2)  
    {  
        Console.WriteLine("Received Add({0},{1}) - sleeping", n1, n2);  
        System.Threading.Thread.Sleep(1000 * 5);  
        double result = n1 + n2;  
        Console.WriteLine("Processing Add({0},{1}) - result: {2}", n1, n2, result);  
    }  
    ...  
}  
```  
  
 Quando o cliente chama o serviço, a chamada retorna sem aguardar a conclusão da operação de serviço.  
  
 Quando você executar o exemplo, as atividades do cliente e o serviço são exibidas nas janelas do console de serviço e cliente. Você pode ver as mensagens de recebimento do serviço do cliente. Pressione ENTER em cada janela de console para desligar o serviço e o cliente.  
  
 O cliente concluir à frente do serviço, demonstrando que um cliente não aguarda a conclusão das operações de serviço unidirecional. A saída do cliente é da seguinte maneira:  
  
```console  
Add(100,15.99)  
Subtract(145,76.54)  
Multiply(9,81.25)  
Divide(22,7)  
  
Press <ENTER> to terminate client.  
```  
  
 A seguinte saída de serviço é mostrada:  
  
```console  
The service is ready.  
Press <ENTER> to terminate service.  
  
Received Add(100,15.99) - sleeping  
Received Subtract(145,76.54) - sleeping  
Received Multiply(9,81.25) - sleeping  
Received Divide(22,7) - sleeping  
Processing Add(100,15.99) - result: 115.99  
Processing Subtract(145,76.54) - result: 68.46  
Processing Multiply(9,81.25) - result: 731.25  
Processing Divide(22,7) - result: 3.14285714285714  
```  
  
> [!NOTE]
>  HTTP é, por definição, um protocolo de solicitação/resposta; Quando uma solicitação é feita, uma resposta é retornada. Isso é verdadeiro mesmo para uma operação de serviço unidirecional que é exposta no HTTP. Quando a operação é chamada, o serviço retornará um código de status HTTP de 202 antes que a operação de serviço foi executada. Esse código de status significa que a solicitação foi aceita para processamento, mas o processamento ainda não foi concluído. O cliente que chamou a operação bloqueia até que ele recebe a resposta 202 do serviço. Isso pode causar um comportamento inesperado quando várias mensagens unidirecionais são enviadas usando uma associação que está configurada para usar sessões. O `wsHttpBinding` associação usada nesse exemplo é configurada para usar sessões por padrão para estabelecer um contexto de segurança. Por padrão, mensagens em uma sessão são garantidas de chegar na ordem em que elas são enviadas. Por isso, quando a segunda mensagem em uma sessão é enviada, ela não é processada até que a primeira mensagem foi processada. O resultado disso é que o cliente não recebe uma mensagem de resposta 202 até que o processamento da mensagem anterior foi concluído. O cliente, portanto, é exibida para o bloco em cada chamada de operação subsequente. Para evitar esse comportamento, este exemplo configura o tempo de execução para distribuir mensagens simultaneamente para instâncias distintas para processamento. Os conjuntos de exemplo <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> para `PerCall` para que cada mensagem pode ser processada por uma instância diferente. <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> é definido como `Multiple` para permitir que mais de um thread enviar mensagens por vez.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1.  Certifique-se de que você tenha executado o [procedimento de configuração de uso único para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Para compilar a edição em C# ou Visual Basic .NET da solução, siga as instruções em [compilando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!NOTE]
>  Execute o serviço antes de executar o cliente e desligar o cliente antes de desligar o serviço. Isso evita uma exceção do cliente quando o cliente não é possível fechar a sessão de segurança corretamente porque o serviço não existe mais.  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Service\Oneway`  
