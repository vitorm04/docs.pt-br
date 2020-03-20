---
title: Simultaneidade
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, concurency sample
- Concurrency Sample [Windows Communication Foundation]
ms.assetid: f8dbdfb3-6858-4f95-abe3-3a1db7878926
ms.openlocfilehash: eb6140895bb922bd159f1abf536a0d0b12d4f96c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183942"
---
# <a name="concurrency"></a>Simultaneidade
A amostra De Concorrência <xref:System.ServiceModel.ServiceBehaviorAttribute> demonstra <xref:System.ServiceModel.ConcurrencyMode> o uso do com a enumeração, que controla se uma instância de um serviço processa mensagens sequencialmente ou simultaneamente. A amostra é baseada no [Getting](../../../../docs/framework/wcf/samples/getting-started-sample.md)Started `ICalculator` , que implementa o contrato de serviço. Esta amostra define um `ICalculatorConcurrency`novo contrato, `ICalculator`que herda de , fornecendo duas operações adicionais para inspecionar o estado da concorrência do serviço. Alterando a configuração de simultu, você pode observar a mudança de comportamento executando o cliente.  
  
 Nesta amostra, o cliente é um aplicativo de console (.exe) e o serviço é hospedado pelo Internet Information Services (IIS).  
  
> [!NOTE]
> O procedimento de configuração e as instruções de construção desta amostra estão localizados no final deste tópico.  
  
 Existem três modos de simultuá-lo disponíveis:  
  
- `Single`: Cada instância de serviço processa uma mensagem por vez. Este é o modo de simultaneidade padrão.  
  
- `Multiple`: Cada instância de serviço processa várias mensagens simultaneamente. A implementação do serviço deve ser segura para threads para usar este modo de concorrência.  
  
- `Reentrant`: Cada instância de serviço processa uma mensagem por vez, mas aceita chamadas reentrantes. O serviço só aceita essas chamadas quando está chamando. O reentrante é demonstrado na amostra [ConcurrencyMode.Reentrant.](../../../../docs/framework/wcf/samples/concurrencymode-reentrant.md)  
  
 O uso de simultuou-se em relação ao modo de instancing. Em <xref:System.ServiceModel.InstanceContextMode.PerCall> instancing, a concorrência não é relevante, porque cada mensagem é processada por uma nova instância de serviço. Na <xref:System.ServiceModel.InstanceContextMode.Single> instancing, <xref:System.ServiceModel.ConcurrencyMode.Single> <xref:System.ServiceModel.ConcurrencyMode.Multiple> ou a concorrência é relevante, dependendo se a instância única processa mensagens sequencialmente ou simultaneamente. Em <xref:System.ServiceModel.InstanceContextMode.PerSession> instancing, qualquer um dos modos de simultuário pode ser relevante.  
  
 A classe de serviço especifica `[ServiceBehavior(ConcurrencyMode=<setting>)]` o comportamento de concorrência com o atributo mostrado na amostra de código a seguir. Ao alterar quais linhas são comentadas, `Single` `Multiple` você pode experimentar com os modos e simultâneo. Lembre-se de reconstruir o serviço depois de alterar o modo de simultuável.  
  
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
  
 A amostra <xref:System.ServiceModel.ConcurrencyMode.Multiple> usa <xref:System.ServiceModel.InstanceContextMode.Single> simultâneo com instancing por padrão. O código do cliente foi modificado para usar um proxy assíncrono. Isso permite que o cliente faça várias chamadas para o serviço sem esperar por uma resposta entre cada chamada. Você pode observar a diferença de comportamento do modo de concorrência de serviço.  
  
 Quando você executa a amostra, as solicitações e respostas da operação são exibidas na janela do console cliente. O modo de concorrência em que o serviço está sendo executado é exibido, cada operação é chamada e, em seguida, a contagem de operação é exibida. Observe que quando o `Multiple`modo de simultâneo é , os resultados são retornados em uma ordem diferente de como eles foram chamados, porque o serviço processa várias mensagens simultaneamente. Ao alterar o modo `Single`de simultâneo para , os resultados são devolvidos na ordem em que foram chamados, pois o serviço processa cada mensagem sequencialmente. Pressione ENTER na janela do cliente para desligar o cliente.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1. Certifique-se de que você tenha realizado o [procedimento de configuração única para as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Se você usar svcutil.exe para gerar o cliente `/async` proxy, certifique-se de incluir a opção.  
  
3. Para construir a edição C# ou Visual Basic .NET da solução, siga as instruções em [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4. Para executar a amostra em uma configuração de máquina única ou cruzada, siga as instruções em [Executar as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
> Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation). Este exemplo está localizado no seguinte diretório.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\Concurrency`  
