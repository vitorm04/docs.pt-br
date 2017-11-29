---
title: "Integração de componentes transacionais de Enterprise Services"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 05dab277-b8b2-48cf-b40c-826be128b175
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 7c2420c700d893e6c2c19b72beed0e605ffd4853
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="integrating-enterprise-services-transactional-components"></a><span data-ttu-id="3e67e-102">Integração de componentes transacionais de Enterprise Services</span><span class="sxs-lookup"><span data-stu-id="3e67e-102">Integrating Enterprise Services Transactional Components</span></span>
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="3e67e-103">Fornece um mecanismo automático para a integração com os serviços corporativos (consulte [integrando aplicativos COM+](../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)).</span><span class="sxs-lookup"><span data-stu-id="3e67e-103"> provides an automatic mechanism for integrating with Enterprise Services (see [Integrating with COM+ Applications](../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)).</span></span> <span data-ttu-id="3e67e-104">No entanto, talvez você queira a flexibilidade para desenvolver serviços que internamente usa componentes transacionais hospedados em serviços corporativos.</span><span class="sxs-lookup"><span data-stu-id="3e67e-104">However, you may want the flexibility to develop services that internally use transactional components hosted within Enterprise Services.</span></span> <span data-ttu-id="3e67e-105">Porque o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] recurso de transações é criado sob o <xref:System.Transactions> infraestrutura, o processo de integração de serviços do Enterprise com [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] é idêntico para especificar a interoperabilidade entre <xref:System.Transactions> e Enterprise Serviços, conforme descrito na [interoperabilidade com serviços da empresa e transações COM+](http://go.microsoft.com/fwlink/?LinkId=94949).</span><span class="sxs-lookup"><span data-stu-id="3e67e-105">Because the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Transactions feature is built on the <xref:System.Transactions> infrastructure, the process for integrating Enterprise Services with [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] is identical to that for specifying interoperability between <xref:System.Transactions> and Enterprise Services, as outlined in [Interoperability with Enterprise Services and COM+ Transactions](http://go.microsoft.com/fwlink/?LinkId=94949).</span></span>  
  
 <span data-ttu-id="3e67e-106">Para fornecer o nível desejado de interoperabilidade entre a transação de fluxo de entrada e a transação de contexto COM+, a implementação do serviço deve criar um <xref:System.Transactions.TransactionScope> instância e usar o valor apropriado a <xref:System.Transactions.EnterpriseServicesInteropOption> enumeração.</span><span class="sxs-lookup"><span data-stu-id="3e67e-106">To provide the desired level of interoperability between the incoming flowed transaction and the COM+ context transaction, the service implementation must create a <xref:System.Transactions.TransactionScope> instance and use the appropriate value from the <xref:System.Transactions.EnterpriseServicesInteropOption> enumeration.</span></span>  
  
## <a name="integrating-enterprise-services-with-a-service-operation"></a><span data-ttu-id="3e67e-107">Integração de serviços corporativos com uma operação de serviço</span><span class="sxs-lookup"><span data-stu-id="3e67e-107">Integrating Enterprise Services with a Service Operation</span></span>  
 <span data-ttu-id="3e67e-108">O código a seguir demonstra uma operação, com o fluxo de transação permitido, que cria um <xref:System.Transactions.TransactionScope> com o <xref:System.Transactions.EnterpriseServicesInteropOption.Full> opção.</span><span class="sxs-lookup"><span data-stu-id="3e67e-108">The following code demonstrates an operation, with Allowed transaction flow, that creates a <xref:System.Transactions.TransactionScope> with the <xref:System.Transactions.EnterpriseServicesInteropOption.Full> option.</span></span> <span data-ttu-id="3e67e-109">As seguintes condições se aplicam neste cenário:</span><span class="sxs-lookup"><span data-stu-id="3e67e-109">The following conditions apply in this scenario:</span></span>  
  
-   <span data-ttu-id="3e67e-110">Se o cliente flui de uma transação, a operação, incluindo a chamada para o componente de serviços corporativos, é executada dentro do escopo da transação.</span><span class="sxs-lookup"><span data-stu-id="3e67e-110">If the client flows a transaction, the operation, including the call to the Enterprise Services component, is executed within the scope of that transaction.</span></span> <span data-ttu-id="3e67e-111">Usando <xref:System.Transactions.EnterpriseServicesInteropOption.Full> garante que a transação é sincronizada com o <xref:System.EnterpriseServices> contexto, o que significa que a transação de ambiente para <xref:System.Transactions> e <xref:System.EnterpriseServices> é o mesmo.</span><span class="sxs-lookup"><span data-stu-id="3e67e-111">Using <xref:System.Transactions.EnterpriseServicesInteropOption.Full> ensures that the transaction is synchronized with the <xref:System.EnterpriseServices> context, which means that the ambient transaction for <xref:System.Transactions> and the <xref:System.EnterpriseServices> is the same.</span></span>  
  
-   <span data-ttu-id="3e67e-112">Se o cliente não fluxo de uma transação, a configuração <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> para `true` cria um novo escopo de transação para a operação.</span><span class="sxs-lookup"><span data-stu-id="3e67e-112">If the client does not flow a transaction, setting <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> to `true` creates a new transaction scope for the operation.</span></span> <span data-ttu-id="3e67e-113">Da mesma forma, usando <xref:System.Transactions.EnterpriseServicesInteropOption.Full> garante que a transação da operação é o mesmo que a transação usada dentro de <xref:System.EnterpriseServices> contexto do componente.</span><span class="sxs-lookup"><span data-stu-id="3e67e-113">Similarly, using <xref:System.Transactions.EnterpriseServicesInteropOption.Full> ensures that the operation’s transaction is the same as the transaction used inside the <xref:System.EnterpriseServices> component's context.</span></span>  
  
 <span data-ttu-id="3e67e-114">As chamadas de método adicionais também ocorrem dentro do escopo da transação da mesma operação.</span><span class="sxs-lookup"><span data-stu-id="3e67e-114">Any additional method calls also occur within the scope of the same operation’s transaction.</span></span>  
  
```  
[ServiceContract()]  
public interface ICustomerServiceContract  
{  
   [OperationContract]  
   [TransactionFlow(TransactionFlowOption.Allowed)]  
   void UpdateCustomerNameOperation(int customerID, string newCustomerName);  
}  
  
[ServiceBehavior(TransactionIsolationLevel = System.Transactions.IsolationLevel.Serializable)]  
public class CustomerService : ICustomerServiceContract  
{  
   [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]  
   public void UpdateCustomerNameOperation(int customerID, string newCustomerName)  
   {  
   // Create a transaction scope with full ES interop  
      using (TransactionScope ts = new TransactionScope(  
                     TransactionScopeOption.Required,  
                     new TransactionOptions(),  
                     EnterpriseServicesInteropOption.Full))  
      {  
         // Create an Enterprise Services component  
         // Call UpdateCustomer method on an Enterprise Services   
         // component   
  
         // Call UpdateOtherCustomerData method on an Enterprise   
         // Services component   
         ts.Complete();  
      }  
  
      // Do UpdateAdditionalData on an non-Enterprise Services  
      // component  
   }  
}  
```  
  
 <span data-ttu-id="3e67e-115">Se nenhuma sincronização é necessária entre a transação atual de uma operação e chamadas para componentes transacionais de Enterprise Services, em seguida, use o <xref:System.Transactions.EnterpriseServicesInteropOption.None> opção ao instanciar o <xref:System.Transactions.TransactionScope> instância.</span><span class="sxs-lookup"><span data-stu-id="3e67e-115">If no synchronization is required between an operation’s current transaction and calls to transactional Enterprise Services components, then use the <xref:System.Transactions.EnterpriseServicesInteropOption.None> option when instantiating the <xref:System.Transactions.TransactionScope> instance.</span></span>  
  
## <a name="integrating-enterprise-services-with-a-client"></a><span data-ttu-id="3e67e-116">Integração de serviços da empresa com um cliente</span><span class="sxs-lookup"><span data-stu-id="3e67e-116">Integrating Enterprise Services with a Client</span></span>  
 <span data-ttu-id="3e67e-117">O código a seguir demonstra o código de cliente usando um <xref:System.Transactions.TransactionScope> instância com o <xref:System.Transactions.EnterpriseServicesInteropOption.Full> configuração.</span><span class="sxs-lookup"><span data-stu-id="3e67e-117">The following code demonstrates client code using a <xref:System.Transactions.TransactionScope> instance with the <xref:System.Transactions.EnterpriseServicesInteropOption.Full> setting.</span></span> <span data-ttu-id="3e67e-118">Nesse cenário, as chamadas para operações de serviço que dão suporte ao fluxo de transações ocorrem dentro do escopo da mesma transação, como as chamadas para os componentes de serviços corporativos.</span><span class="sxs-lookup"><span data-stu-id="3e67e-118">In this scenario, calls to service operations that support transaction flow occur within the scope of the same transaction as the calls to Enterprise Services components.</span></span>  
  
```  
static void Main()  
{  
    // Create a client  
    CalculatorClient client = new CalculatorClient();  
  
    // Create a transaction scope with full ES interop  
    using (TransactionScope ts = new TransactionScope(  
          TransactionScopeOption.Required,  
          new TransactionOptions(),  
          EnterpriseServicesInteropOption.Full))  
    {  
        // Call Add calculator service operation  
  
        // Create an Enterprise Services component  
  
        // Call UpdateCustomer method on an Enterprise Services   
        // component   
  
        ts.Complete();  
    }  
  
    // Closing the client gracefully closes the connection and   
    // cleans up resources  
    client.Close();  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="3e67e-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3e67e-119">See Also</span></span>  
 [<span data-ttu-id="3e67e-120">Integrando aplicativos COM+</span><span class="sxs-lookup"><span data-stu-id="3e67e-120">Integrating with COM+ Applications</span></span>](../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)  
 [<span data-ttu-id="3e67e-121">Integrando aplicativos COM</span><span class="sxs-lookup"><span data-stu-id="3e67e-121">Integrating with COM Applications</span></span>](../../../../docs/framework/wcf/feature-details/integrating-with-com-applications.md)
