---
title: "Serviços e transações"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: service contracts [WCF], designing services and transactions
ms.assetid: 864813ff-2709-4376-912d-f5c8d318c460
caps.latest.revision: "10"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 7a206ff3d82378e825cd612a6564366ef1e07977
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="services-and-transactions"></a><span data-ttu-id="20ab3-102">Serviços e transações</span><span class="sxs-lookup"><span data-stu-id="20ab3-102">Services and Transactions</span></span>
[!INCLUDE[indigo1](../../../includes/indigo1-md.md)]<span data-ttu-id="20ab3-103">aplicativos podem iniciar uma transação de dentro de um cliente e coordenar a transação na operação de serviço.</span><span class="sxs-lookup"><span data-stu-id="20ab3-103"> applications can initiate a transaction from within a client and coordinate the transaction within the service operation.</span></span> <span data-ttu-id="20ab3-104">Os clientes podem iniciar uma transação e chamar várias operações de serviço e certifique-se de que as operações de serviço sejam confirmadas ou revertidas como uma única unidade.</span><span class="sxs-lookup"><span data-stu-id="20ab3-104">Clients can initiate a transaction and invoke several service operations and ensure that the service operations are either committed or rolled back as a single unit.</span></span>  
  
 <span data-ttu-id="20ab3-105">Você pode habilitar o comportamento de transação no contrato de serviço especificando um <xref:System.ServiceModel.ServiceBehaviorAttribute> e configuração de seu <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A> e <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> propriedades para operações de serviço que exigem transações de cliente.</span><span class="sxs-lookup"><span data-stu-id="20ab3-105">You can enable the transaction behavior in the service contract by specifying a <xref:System.ServiceModel.ServiceBehaviorAttribute> and setting its <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A> and <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> properties for service operations that require client transactions.</span></span> <span data-ttu-id="20ab3-106">O <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> parâmetro especifica se a transação na qual o método é executado é preenchida automaticamente se nenhuma exceção sem tratamento é geradas.</span><span class="sxs-lookup"><span data-stu-id="20ab3-106">The <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> parameter specifies whether the transaction in which the method executes is automatically completed if no unhandled exceptions are thrown.</span></span> [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="20ab3-107">Esses atributos, consulte [atributos de transação de ServiceModel](../../../docs/framework/wcf/feature-details/servicemodel-transaction-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="20ab3-107"> these attributes, see [ServiceModel Transaction Attributes](../../../docs/framework/wcf/feature-details/servicemodel-transaction-attributes.md).</span></span>  
  
 <span data-ttu-id="20ab3-108">O trabalho é executado nas operações de serviço e gerenciado por um Gerenciador de recursos, como atualizações de banco de dados de log é parte da transação do cliente.</span><span class="sxs-lookup"><span data-stu-id="20ab3-108">The work that is performed in the service operations and managed by a resource manager, such as logging database updates, is part of the client’s transaction.</span></span>  
  
 <span data-ttu-id="20ab3-109">O exemplo a seguir demonstra o uso do <xref:System.ServiceModel.ServiceBehaviorAttribute> e <xref:System.ServiceModel.OperationBehaviorAttribute> atributos para controlar o comportamento de transação no lado do serviço.</span><span class="sxs-lookup"><span data-stu-id="20ab3-109">The following sample demonstrates usage of the <xref:System.ServiceModel.ServiceBehaviorAttribute> and <xref:System.ServiceModel.OperationBehaviorAttribute> attributes to control service-side transaction behavior.</span></span>  
  
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
  
 <span data-ttu-id="20ab3-110">Você pode habilitar transações e configurando o cliente de fluxo de transações e associações para usar o protocolo WS-AtomicTransaction e configuração do serviço de [ \<transactionFlow >](../../../docs/framework/configure-apps/file-schema/wcf/transactionflow.md) elemento `true`, conforme mostrado na configuração de exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="20ab3-110">You can enable transactions and transaction flow by configuring the client and service bindings to use the WS-AtomicTransaction protocol, and setting the [\<transactionFlow>](../../../docs/framework/configure-apps/file-schema/wcf/transactionflow.md) element to `true`, as shown in the following sample configuration.</span></span>  
  
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
  
 <span data-ttu-id="20ab3-111">Os clientes podem iniciar uma transação criando uma <xref:System.Transactions.TransactionScope> e chamar operações de serviço dentro do escopo da transação.</span><span class="sxs-lookup"><span data-stu-id="20ab3-111">Clients can begin a transaction by creating a <xref:System.Transactions.TransactionScope> and invoking service operations within the scope of the transaction.</span></span>  
  
```  
using (TransactionScope ts = new TransactionScope(TransactionScopeOption.RequiresNew))  
{  
    //Do work here  
    ts.Complete();  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="20ab3-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="20ab3-112">See Also</span></span>  
 [<span data-ttu-id="20ab3-113">Suporte transacional em System. ServiceModel</span><span class="sxs-lookup"><span data-stu-id="20ab3-113">Transactional Support in System.ServiceModel</span></span>](../../../docs/framework/wcf/feature-details/transactional-support-in-system-servicemodel.md)  
 [<span data-ttu-id="20ab3-114">Modelos de transação</span><span class="sxs-lookup"><span data-stu-id="20ab3-114">Transaction Models</span></span>](../../../docs/framework/wcf/feature-details/transaction-models.md)  
 [<span data-ttu-id="20ab3-115">Fluxo de transação WS</span><span class="sxs-lookup"><span data-stu-id="20ab3-115">WS Transaction Flow</span></span>](../../../docs/framework/wcf/samples/ws-transaction-flow.md)
