---
title: Comportamento padrão de serviço
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, defaults
- Default Service Behavior Sample [Windows Communication Foundation]
ms.assetid: 442d4f71-c64e-4c62-816a-a66c38e7d3ec
ms.openlocfilehash: 798231cbfddf17dd63a61f3e2a07a6490289e56f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183760"
---
# <a name="default-service-behavior"></a>Comportamento padrão de serviço
Esta amostra demonstra como as configurações de comportamento de serviço podem ser configuradas. A amostra é baseada no [Getting](../../../../docs/framework/wcf/samples/getting-started-sample.md)Started `ICalculator` , que implementa o contrato de serviço. Esta amostra define explicitamente comportamentos de serviço e <xref:System.ServiceModel.ServiceBehaviorAttribute> <xref:System.ServiceModel.OperationBehaviorAttribute> comportamentos de operação usando os atributos. Você pode configurar comportamentos em arquivos de configuração ou imperativamente em código (como esta amostra demonstra).  
  
 Nesta amostra, o cliente é um aplicativo de console (.exe) e o serviço é hospedado pelo Internet Information Services (IIS).  
  
> [!NOTE]
> O procedimento de configuração e as instruções de construção desta amostra estão localizados no final deste tópico.  
  
 A classe de serviço especifica <xref:System.ServiceModel.ServiceBehaviorAttribute> comportamentos <xref:System.ServiceModel.OperationBehaviorAttribute> com o e o mostrado na amostra de código a seguir. Todos os valores especificados são os padrões.  
  
```csharp
[ServiceBehavior(  
    AutomaticSessionShutdown=true,  
    ConcurrencyMode=ConcurrencyMode.Single,  
    InstanceContextMode=InstanceContextMode.PerSession,  
    IncludeExceptionDetailInFaults=false,  
    UseSynchronizationContext=true,  
    ValidateMustUnderstand=true)]  
public class CalculatorService : ICalculator  
{  
    [OperationBehavior(  
        TransactionAutoComplete=true,  
        TransactionScopeRequired=false,  
        Impersonation=ImpersonationOption.NotAllowed)]  
    public double Add(double n1, double n2)  
    {  
        System.Threading.Thread.Sleep(1600);  
        return n1 + n2;  
    }  
    ...  
}  
```  
  
 Os comportamentos de serviço <xref:System.ServiceModel.ServiceBehaviorAttribute> são especificados com o atributo. A tabela a seguir descreve alguns desses comportamentos.  
  
|Comportamento de serviço|Descrição|  
|----------------------|-----------------|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.AutomaticSessionShutdown%2A>|Desliga automaticamente uma sessão a pedido do cliente.|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A>|Especifica o modo de simultuou para cada instância de serviço.|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A>|Especifica o modo de contexto de ocorrência.|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.UseSynchronizationContext%2A>|Determina se deve usar o contexto de sincronização fornecido, se for definido. Use isso quando quiser controlar se `WindowsFormsSynchronizationContext` deve usar um aplicativo no Windows Forms.|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults%2A>|Determina se exceções gerais de execução não tratadas devem ser convertidas em uma `Fault<string>` e enviadas como uma mensagem de falha.|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A>|Especifica o nível de isolamento para transações.|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.ValidateMustUnderstand%2A>|Determina se os cabeçalhos de mensagem inesperados causam uma condição de erro.|  
  
 Os comportamentos de operação são <xref:System.ServiceModel.OperationBehaviorAttribute> especificados usando o atributo. A tabela a seguir descreve alguns desses comportamentos.  
  
|Comportamento da Operação|Descrição|  
|------------------------|-----------------|  
|<xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A>|Determina se a conclusão da operação de serviço compromete a transação atual.|  
|<xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A>|Determina se a operação de serviço se alista em uma transação fluída pelo cliente.|  
|<xref:System.ServiceModel.OperationBehaviorAttribute.Impersonation%2A>|Determina se a operação de serviço representa a identidade do chamador.|  
|<xref:System.ServiceModel.OperationBehaviorAttribute.ReleaseInstanceMode%2A>|Determina se as instâncias de serviço são recicladas no início ou no final da chamada de operação do serviço.|  
  
 Quando você executa a amostra, as solicitações e respostas da operação são exibidas na janela do console cliente. O atraso entre as chamadas é `System.Threading.Thread.Sleep()` resultado das chamadas feitas nas operações de serviço. O resto das amostras de comportamento explicam esses comportamentos com mais detalhes. Pressione ENTER na janela do cliente para desligar o cliente.  
  
```console  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
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
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\Default`  
