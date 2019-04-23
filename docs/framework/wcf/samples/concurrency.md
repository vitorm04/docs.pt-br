---
title: Concorrência
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, concurency sample
- Concurrency Sample [Windows Communication Foundation]
ms.assetid: f8dbdfb3-6858-4f95-abe3-3a1db7878926
ms.openlocfilehash: 5de918f71f4361af3409c8382781844824747c83
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59296596"
---
# <a name="concurrency"></a>Concorrência
O exemplo de simultaneidade demonstra como usar o <xref:System.ServiceModel.ServiceBehaviorAttribute> com o <xref:System.ServiceModel.ConcurrencyMode> enumeração, que controla se uma instância de um serviço processa mensagens consecutivamente ou simultaneamente. O exemplo se baseia a [guia de Introdução](../../../../docs/framework/wcf/samples/getting-started-sample.md), que implementa o `ICalculator` contrato de serviço. Este exemplo define um novo contrato, `ICalculatorConcurrency`, que herda de `ICalculator`, fornecendo duas operações adicionais para inspecionar o estado de simultaneidade de serviço. Alterando a configuração de simultaneidade, você pode observar a alteração no comportamento executando o cliente.  
  
 Neste exemplo, o cliente é um aplicativo de console (.exe) e o serviço é hospedado pelo Internet Information Services (IIS).  
  
> [!NOTE]
>  As instruções de procedimento e compilação de configuração para este exemplo estão localizadas no final deste tópico.  
  
 Há três modos de simultaneidade disponíveis:  
  
-   `Single`: Cada instância de serviço processa uma mensagem por vez. Este é o modo de simultaneidade padrão.  
  
-   `Multiple`: Cada instância de serviço processa várias mensagens simultaneamente. A implementação do serviço deve ser thread-safe para usar esse modo de simultaneidade.  
  
-   `Reentrant`: Cada instância de serviço processa uma mensagem por vez, mas aceita chamadas reentrantes. O serviço aceita somente essas chamadas quando ela é chamada. Reentrante é demonstrada na [Reentrant](../../../../docs/framework/wcf/samples/concurrencymode-reentrant.md) exemplo.  
  
 O uso de simultaneidade está relacionado ao modo de instanciação. No <xref:System.ServiceModel.InstanceContextMode.PerCall> instanciamento, simultaneidade não for relevante, porque cada mensagem é processada por uma nova instância de serviço. Na <xref:System.ServiceModel.InstanceContextMode.Single> instanciamento, tanto <xref:System.ServiceModel.ConcurrencyMode.Single> ou <xref:System.ServiceModel.ConcurrencyMode.Multiple> simultaneidade é relevante, dependendo se a instância única processa mensagens consecutivamente ou simultaneamente. Em <xref:System.ServiceModel.InstanceContextMode.PerSession> de instanciação, qualquer um dos modos de simultaneidade podem ser relevantes.  
  
 A classe de serviço Especifica o comportamento de simultaneidade com o `[ServiceBehavior(ConcurrencyMode=<setting>)]` atributo conforme mostrado no exemplo de código que segue. Alterando as linhas que são comentadas, você pode fazer experiências com o `Single` e `Multiple` modos de simultaneidade. Lembre-se recriar o serviço depois de alterar o modo de simultaneidade.  
  
```csharp
// Single allows a single message to be processed sequentially by each service instance.  
//[ServiceBehavior(ConcurrencyMode = ConcurrencyMode.Single, InstanceContextMode = InstanceContextMode.Single)]  
  
// Multiple allows concurrent processing of multiple messages by a service instance.  
// The service implementation should be thread-safe. This can be used to increase throughput.  
[ServiceBehavior(ConcurrencyMode=ConcurrencyMode.Multiple, InstanceContextMode = InstanceContextMode.Single)]  
  
// Uses Thread.Sleep to vary the execution time of each operation.  
public class CalculatorService : ICalculatorConcurrency  
{  
    int operationCount;  
  
    public double Add(double n1, double n2)  
    {  
        operationCount++;  
        System.Threading.Thread.Sleep(180);  
        return n1 + n2;  
    }  
  
    public double Subtract(double n1, double n2)  
    {  
        operationCount++;  
        System.Threading.Thread.Sleep(100);  
        return n1 - n2;  
    }  
  
    public double Multiply(double n1, double n2)  
    {  
        operationCount++;  
        System.Threading.Thread.Sleep(150);  
        return n1 * n2;  
    }  
  
    public double Divide(double n1, double n2)  
    {  
        operationCount++;  
        System.Threading.Thread.Sleep(120);  
        return n1 / n2;  
    }  
  
    public string GetConcurrencyMode()  
    {     
        // Return the ConcurrencyMode of the service.  
        ServiceHost host = (ServiceHost)OperationContext.Current.Host;  
        ServiceBehaviorAttribute behavior = host.Description.Behaviors.Find<ServiceBehaviorAttribute>();  
        return behavior.ConcurrencyMode.ToString();  
    }  
  
    public int GetOperationCount()  
    {     
        // Return the number of operations.  
        return operationCount;  
    }  
}  
```  
  
 O exemplo usa <xref:System.ServiceModel.ConcurrencyMode.Multiple> simultaneidade com <xref:System.ServiceModel.InstanceContextMode.Single> instanciação por padrão. O código do cliente foi modificado para usar um proxy assíncrono. Isso permite que o cliente para fazer várias chamadas para o serviço sem aguardar uma resposta entre cada chamada. Você pode observar a diferença no comportamento do modo de simultaneidade do serviço.  
  
 Quando você executar o exemplo, as respostas e solicitações de operação são exibidas na janela do console de cliente. O modo de simultaneidade que o serviço está sendo executado é exibido, cada operação é chamada e, em seguida, a contagem de operações é exibida. Observe que, quando o modo de simultaneidade é `Multiple`, os resultados são retornados em uma ordem diferente de como eles foram chamados, porque o serviço processa várias mensagens simultaneamente. Alterando o modo de simultaneidade para `Single`, os resultados são retornados na ordem em que eles foram chamados, porque o serviço processe cada mensagem em sequência. Pressione ENTER na janela do cliente para desligar o cliente.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1. Certifique-se de que você tenha executado o [procedimento de configuração de uso único para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Se você usar Svcutil.exe para gerar o cliente de proxy, certifique-se de que você inclua o `/async` opção.  
  
3. Para compilar a edição em C# ou Visual Basic .NET da solução, siga as instruções em [compilando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4. Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\Concurrency`  
