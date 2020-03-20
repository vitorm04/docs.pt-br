---
title: Unidirecional
ms.date: 03/30/2017
ms.assetid: 74e3e03d-cd15-4191-a6a5-1efa2dcb9e73
ms.openlocfilehash: 3203762e05c794ed28b65d8fded6972fac1f5820
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183436"
---
# <a name="one-way"></a>Unidirecional
Esta amostra demonstra um contato de serviço com operações de serviço unidirecional. O cliente não espera que as operações de serviço se completem, como é o caso das operações de serviço bidirecional. Esta amostra é baseada no Getting `wsHttpBinding` [Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) e usa a ligação. O serviço nesta amostra é um aplicativo de console auto-hospedado para permitir que você observe o serviço que recebe e processa solicitações. O cliente também é um aplicativo de console.  
  
> [!NOTE]
> O procedimento de configuração e as instruções de construção desta amostra estão localizados no final deste tópico.  
  
 Para criar um contrato de serviço unidirecional, <xref:System.ServiceModel.OperationContractAttribute> defina seu contrato <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> `true` de serviço, aplique a classe em cada operação e defina como mostrado no seguinte código de amostra:  
  
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
  
 Para demonstrar que o cliente não espera que as operações de serviço se completem, o código de serviço nesta amostra implementa um atraso de cinco segundos, como mostrado no seguinte código de amostra:  
  
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
  
 Quando o cliente liga para o serviço, a chamada retorna sem esperar que a operação do serviço seja concluída.  
  
 Quando você executa a amostra, as atividades de cliente e serviço são exibidas nas janelas de serviço e console do cliente. Você pode ver o serviço receber mensagens do cliente. Pressione ENTER em cada janela do console para desligar o serviço e o cliente.  
  
 O cliente termina à frente do serviço, demonstrando que um cliente não espera que as operações de serviço unidirecional se concluam. A saída do cliente é a seguinte:  
  
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
> HTTP é, por definição, um protocolo de solicitação/resposta; quando uma solicitação é feita, uma resposta é devolvida. Isso é verdade mesmo para uma operação de serviço unidirecional que é exposta em HTTP. Quando a operação é chamada, o serviço retorna um código de status HTTP de 202 antes da operação de serviço ser executada. Este código de status significa que a solicitação foi aceita para processamento, mas o processamento ainda não foi concluído. O cliente que ligou para os blocos da operação até receber a resposta 202 do serviço. Isso pode causar algum comportamento inesperado quando várias mensagens unidirecionais são enviadas usando uma vinculação configurada para usar sessões. A `wsHttpBinding` vinculação usada nesta amostra é configurada para usar sessões por padrão para estabelecer um contexto de segurança. Por padrão, as mensagens em uma sessão são garantidas para chegar na ordem em que são enviadas. Por causa disso, quando a segunda mensagem em uma sessão é enviada, ela não é processada até que a primeira mensagem tenha sido processada. O resultado disso é que o cliente não recebe a resposta 202 para uma mensagem até que o processamento da mensagem anterior tenha sido concluído. O cliente, portanto, parece bloquear cada chamada de operação subseqüente. Para evitar esse comportamento, essa amostra configura o tempo de execução para despachar mensagens simultaneamente a instâncias distintas para processamento. A amostra <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> `PerCall` define para que cada mensagem possa ser processada por uma instância diferente. <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A>é definido `Multiple` para permitir que mais de um segmento despacha mensagens de cada vez.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1. Certifique-se de que você tenha realizado o [procedimento de configuração única para as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Para construir a edição C# ou Visual Basic .NET da solução, siga as instruções em [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Para executar a amostra em uma configuração de máquina única ou cruzada, siga as instruções em [Executar as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!NOTE]
> Execute o serviço antes de executar o cliente e desligue o cliente antes de desligar o serviço. Isso evita uma exceção do cliente quando o cliente não pode fechar a sessão de segurança de forma limpa porque o serviço se foi.  
  
> [!IMPORTANT]
> Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation). Este exemplo está localizado no seguinte diretório.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Service\Oneway`  
