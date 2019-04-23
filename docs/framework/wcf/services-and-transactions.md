---
title: Serviços e transações
ms.date: 03/30/2017
helpviewer_keywords:
- service contracts [WCF], designing services and transactions
ms.assetid: 864813ff-2709-4376-912d-f5c8d318c460
ms.openlocfilehash: 9dfe34406bfda2c16bd2f0cd53796b2fcef07b57
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59138327"
---
# <a name="services-and-transactions"></a>Serviços e transações
Aplicativos do Windows Communication Foundation (WCF) podem iniciar uma transação de dentro de um cliente e coordenar a transação dentro da operação de serviço. Os clientes podem iniciar uma transação e invocar várias operações de serviço e certifique-se de que as operações de serviço são confirmadas ou revertidas como uma única unidade.  
  
 Você pode habilitar o comportamento de transação no contrato de serviço especificando um <xref:System.ServiceModel.ServiceBehaviorAttribute> e definindo seu <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A> e <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> propriedades para operações de serviço que exigem transações do cliente. O <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> parâmetro especifica se a transação na qual o método é executado é preenchida automaticamente se nenhuma exceção sem tratamento é geradas. Para obter mais informações sobre esses atributos, consulte [atributos de transação de ServiceModel](../../../docs/framework/wcf/feature-details/servicemodel-transaction-attributes.md).  
  
 O trabalho que é executado nas operações de serviço e gerenciado por um Gerenciador de recursos, como atualizações de banco de dados de registro em log é parte da transação do cliente.  
  
 O exemplo a seguir demonstra o uso do <xref:System.ServiceModel.ServiceBehaviorAttribute> e <xref:System.ServiceModel.OperationBehaviorAttribute> atributos para controlar o comportamento de transação do lado do serviço.  
  
```csharp
[ServiceBehavior(TransactionIsolationLevel = System.Transactions.IsolationLevel.Serializable)]  
public class CalculatorService: ICalculatorLog  
{  
    [OperationBehavior(TransactionScopeRequired = true,  
                           TransactionAutoComplete = true)]  
    public double Add(double n1, double n2)  
    {  
        recordToLog($"Added {n1} to {n2}");
        return n1 + n2;  
    }  
  
    [OperationBehavior(TransactionScopeRequired = true,   
                               TransactionAutoComplete = true)]  
    public double Subtract(double n1, double n2)  
    {  
        recordToLog($"Subtracted {n1} from {n2}");
        return n1 - n2;  
    }  
  
    [OperationBehavior(TransactionScopeRequired = true,   
                                       TransactionAutoComplete = true)]  
    public double Multiply(double n1, double n2)  
    {  
        recordToLog($"Multiplied {n1} by {n2}");
        return n1 * n2;  
    }  
  
    [OperationBehavior(TransactionScopeRequired = true,   
                                       TransactionAutoComplete = true)]  
    public double Divide(double n1, double n2)  
    {  
        recordToLog($"Divided {n1} by {n2}", n1, n2);
        return n1 / n2;  
    }  
  
}  
```  
  
 Você pode permitir que as transações e configurando o cliente de fluxo de transações e associações para usar o protocolo WS-AtomicTransaction e configuração de serviço a [ \<transactionFlow >](../../../docs/framework/configure-apps/file-schema/wcf/transactionflow.md) elemento `true`, conforme mostrado na configuração de exemplo a seguir.  
  
```xml  
<client>  
    <endpoint address="net.tcp://localhost/ServiceModelSamples/service"   
          binding="netTcpBinding"   
          bindingConfiguration="netTcpBindingWSAT"   
          contract="Microsoft.ServiceModel.Samples.ICalculatorLog" />  
</client>  
  
<bindings>  
    <netTcpBinding>  
        <binding name="netTcpBindingWSAT"  
                transactionFlow="true"  
                transactionProtocol="WSAtomicTransactionOctober2004" />  
     </netTcpBinding>  
</bindings>  
```  
  
 Os clientes podem iniciar uma transação, criando um <xref:System.Transactions.TransactionScope> e invocar operações de serviço dentro do escopo da transação.  
  
```csharp
using (TransactionScope ts = new TransactionScope(TransactionScopeOption.RequiresNew))  
{  
    //Do work here  
    ts.Complete();  
}  
```  
  
## <a name="see-also"></a>Consulte também

- [Suporte transacional em System.ServiceModel](../../../docs/framework/wcf/feature-details/transactional-support-in-system-servicemodel.md)
- [Modelos de transação](../../../docs/framework/wcf/feature-details/transaction-models.md)
- [Fluxo de transação WS](../../../docs/framework/wcf/samples/ws-transaction-flow.md)
