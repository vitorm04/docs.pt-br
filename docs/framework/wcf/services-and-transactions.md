---
title: Serviços e transações
ms.date: 03/30/2017
helpviewer_keywords:
- service contracts [WCF], designing services and transactions
ms.assetid: 864813ff-2709-4376-912d-f5c8d318c460
ms.openlocfilehash: 4c59b83448f5a2c448843c12dae99c442441441f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79143272"
---
# <a name="services-and-transactions"></a>Serviços e transações
Os aplicativos da Windows Communication Foundation (WCF) podem iniciar uma transação de dentro de um cliente e coordenar a transação dentro da operação de serviço. Os clientes podem iniciar uma transação e invocar várias operações de serviço e garantir que as operações de serviço sejam comprometidas ou revertidas como uma única unidade.  
  
 Você pode habilitar o comportamento da transação no contrato de serviço especificando e <xref:System.ServiceModel.ServiceBehaviorAttribute> definindo suas <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A> propriedades para <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> operações de serviço que requerem transações de clientes. O <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> parâmetro especifica se a transação em que o método é executado é automaticamente concluída se nenhuma exceção não manipulada for lançada. Para obter mais informações sobre esses atributos, consulte [ServiceModel Transaction Attributes](./feature-details/servicemodel-transaction-attributes.md).  
  
 O trabalho que é realizado nas operações de serviço e gerenciado por um gestor de recursos, como o registro de atualizações de banco de dados, faz parte da transação do cliente.  
  
 A amostra a seguir <xref:System.ServiceModel.ServiceBehaviorAttribute> <xref:System.ServiceModel.OperationBehaviorAttribute> demonstra o uso dos atributos para controlar o comportamento de transação do lado do serviço.  
  
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
  
 Você pode habilitar transações e fluxo de transações configurando as vinculações de cliente e serviço `true`para usar o protocolo WS-AtomicTransaction e definindo o [ \<](../configure-apps/file-schema/wcf/transactionflow.md) elemento transactionFlow>para , conforme mostrado na configuração da amostra a seguir.  
  
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
  
 Os clientes podem iniciar <xref:System.Transactions.TransactionScope> uma transação criando e invocando operações de serviço no âmbito da transação.  
  
```csharp
using (TransactionScope ts = new TransactionScope(TransactionScopeOption.RequiresNew))  
{  
    //Do work here  
    ts.Complete();  
}  
```  
  
## <a name="see-also"></a>Confira também

- [Suporte transacional em System.ServiceModel](./feature-details/transactional-support-in-system-servicemodel.md)
- [Modelos de transação](./feature-details/transaction-models.md)
- [Fluxo de transação WS](./samples/ws-transaction-flow.md)
