---
title: Comportamento padrão de serviço
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, defaults
- Default Service Behavior Sample [Windows Communication Foundation]
ms.assetid: 442d4f71-c64e-4c62-816a-a66c38e7d3ec
ms.openlocfilehash: 6c144bddff4e485673dbdc7e218e82808c20aa61
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61990256"
---
# <a name="default-service-behavior"></a>Comportamento padrão de serviço
Este exemplo demonstra como as configurações de comportamento de serviço podem ser configuradas. O exemplo se baseia a [guia de Introdução](../../../../docs/framework/wcf/samples/getting-started-sample.md), que implementa o `ICalculator` contrato de serviço. Este exemplo define explicitamente os comportamentos de serviço e comportamentos de operação usando o <xref:System.ServiceModel.ServiceBehaviorAttribute> e <xref:System.ServiceModel.OperationBehaviorAttribute> atributos. Você pode configurar comportamentos em arquivos de configuração ou imperativa no código (como este exemplo demonstra).  
  
 Neste exemplo, o cliente é um aplicativo de console (.exe) e o serviço é hospedado pelo Internet Information Services (IIS).  
  
> [!NOTE]
>  As instruções de procedimento e compilação de configuração para este exemplo estão localizadas no final deste tópico.  
  
 A classe de serviço Especifica os comportamentos com o <xref:System.ServiceModel.ServiceBehaviorAttribute> e o <xref:System.ServiceModel.OperationBehaviorAttribute> conforme mostrado no exemplo de código a seguir. Todos os valores especificados são os padrões.  
  
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
  
 Comportamentos de serviço são especificados com o <xref:System.ServiceModel.ServiceBehaviorAttribute> atributo. A tabela a seguir descreve alguns desses comportamentos.  
  
|Comportamento de serviço|Descrição|  
|----------------------|-----------------|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.AutomaticSessionShutdown%2A>|Desliga automaticamente uma sessão de solicitação do cliente.|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A>|Especifica o modo de simultaneidade para cada instância de serviço.|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A>|Especifica o modo de contexto de instância.|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.UseSynchronizationContext%2A>|Determina se é necessário usar o contexto de sincronização fornecido, se houver um definido. Use essa opção quando quiser controlar se é necessário usar um `WindowsFormsSynchronizationContext` em aplicativos de formulários do Windows.|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults%2A>|Determina se as exceções de execução gerais sem tratamento são a ser convertido em um `Fault<string>` e enviadas como uma mensagem de falha.|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A>|Especifica o nível de isolamento para transações.|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.ValidateMustUnderstand%2A>|Determina se os cabeçalhos de mensagem inesperada causam uma condição de erro.|  
  
 Comportamentos de operação são especificados usando o <xref:System.ServiceModel.OperationBehaviorAttribute> atributo. A tabela a seguir descreve alguns desses comportamentos.  
  
|Comportamento da operação|Descrição|  
|------------------------|-----------------|  
|<xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A>|Determina se a conclusão da operação de serviço confirma a transação atual.|  
|<xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A>|Determina se a operação de serviço se inscreve em uma transação fluída de cliente.|  
|<xref:System.ServiceModel.OperationBehaviorAttribute.Impersonation%2A>|Determina se a operação de serviço representa a identidade do chamador.|  
|<xref:System.ServiceModel.OperationBehaviorAttribute.ReleaseInstanceMode%2A>|Determina se as instâncias de serviço são recicladas no início ou final da chamada da operação de serviço.|  
  
 Quando você executar o exemplo, as respostas e solicitações de operação são exibidas na janela do console de cliente. O atraso entre as chamadas é o resultado das chamadas para `System.Threading.Thread.Sleep()` feitas nas operações de serviço. O restante dos exemplos de comportamento explicar esses comportamentos em mais detalhes. Pressione ENTER na janela do cliente para desligar o cliente.  
  
```console  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1. Certifique-se de que você tenha executado o [procedimento de configuração de uso único para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Para compilar a edição em C# ou Visual Basic .NET da solução, siga as instruções em [compilando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\Default`  
