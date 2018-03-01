---
title: "Serviços e transações"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- service contracts [WCF], designing services and transactions
ms.assetid: 864813ff-2709-4376-912d-f5c8d318c460
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: f6256db06825a79b5235b92e2ed205608f04aac7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="services-and-transactions"></a>Serviços e transações
[!INCLUDE[indigo1](../../../includes/indigo1-md.md)]aplicativos podem iniciar uma transação de dentro de um cliente e coordenar a transação na operação de serviço. Os clientes podem iniciar uma transação e chamar várias operações de serviço e certifique-se de que as operações de serviço sejam confirmadas ou revertidas como uma única unidade.  
  
 Você pode habilitar o comportamento de transação no contrato de serviço especificando um <xref:System.ServiceModel.ServiceBehaviorAttribute> e configuração de seu <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A> e <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> propriedades para operações de serviço que exigem transações de cliente. O <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> parâmetro especifica se a transação na qual o método é executado é preenchida automaticamente se nenhuma exceção sem tratamento é geradas. [!INCLUDE[crabout](../../../includes/crabout-md.md)]Esses atributos, consulte [atributos de transação de ServiceModel](../../../docs/framework/wcf/feature-details/servicemodel-transaction-attributes.md).  
  
 O trabalho é executado nas operações de serviço e gerenciado por um Gerenciador de recursos, como atualizações de banco de dados de log é parte da transação do cliente.  
  
 O exemplo a seguir demonstra o uso do <xref:System.ServiceModel.ServiceBehaviorAttribute> e <xref:System.ServiceModel.OperationBehaviorAttribute> atributos para controlar o comportamento de transação no lado do serviço.  
  
```  
[ServiceBehavior(TransactionIsolationLevel = System.Transactions.IsolationLevel.Serializable)]  
public class CalculatorService: ICalculatorLog  
{  
    [OperationBehavior(TransactionScopeRequired = true,  
                           TransactionAutoComplete = true)]  
    public double Add(double n1, double n2)  
    {  
        recordToLog(String.Format("Added {0} to {1}", n1, n2));  
        return n1 + n2;  
    }  
  
    [OperationBehavior(TransactionScopeRequired = true,   
                               TransactionAutoComplete = true)]  
    public double Subtract(double n1, double n2)  
    {  
        recordToLog(String.Format("Subtracted {0} from {1}", n1, n2));  
        return n1 - n2;  
    }  
  
    [OperationBehavior(TransactionScopeRequired = true,   
                                       TransactionAutoComplete = true)]  
    public double Multiply(double n1, double n2)  
    {  
        recordToLog(String.Format("Multiplied {0} by {1}", n1, n2));  
        return n1 * n2;  
    }  
  
    [OperationBehavior(TransactionScopeRequired = true,   
                                       TransactionAutoComplete = true)]  
    public double Divide(double n1, double n2)  
    {  
        recordToLog(String.Format("Divided {0} by {1}", n1, n2));  
        return n1 / n2;  
    }  
  
}  
```  
  
 Você pode habilitar transações e configurando o cliente de fluxo de transações e associações para usar o protocolo WS-AtomicTransaction e configuração do serviço de [ \<transactionFlow >](../../../docs/framework/configure-apps/file-schema/wcf/transactionflow.md) elemento `true`, conforme mostrado na configuração de exemplo a seguir.  
  
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
  
 Os clientes podem iniciar uma transação criando uma <xref:System.Transactions.TransactionScope> e chamar operações de serviço dentro do escopo da transação.  
  
```  
using (TransactionScope ts = new TransactionScope(TransactionScopeOption.RequiresNew))  
{  
    //Do work here  
    ts.Complete();  
}  
```  
  
## <a name="see-also"></a>Consulte também  
 [Suporte transacional em System.ServiceModel](../../../docs/framework/wcf/feature-details/transactional-support-in-system-servicemodel.md)  
 [Modelos de transação](../../../docs/framework/wcf/feature-details/transaction-models.md)  
 [Fluxo de transação WS](../../../docs/framework/wcf/samples/ws-transaction-flow.md)
