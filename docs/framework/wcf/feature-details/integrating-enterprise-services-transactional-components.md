---
title: Integração de componentes transacionais de Enterprise Services
ms.date: 03/30/2017
ms.assetid: 05dab277-b8b2-48cf-b40c-826be128b175
ms.openlocfilehash: 865756506f34fecb1848675205715acfb261ba2d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54686498"
---
# <a name="integrating-enterprise-services-transactional-components"></a><span data-ttu-id="5d11b-102">Integração de componentes transacionais de Enterprise Services</span><span class="sxs-lookup"><span data-stu-id="5d11b-102">Integrating Enterprise Services Transactional Components</span></span>
<span data-ttu-id="5d11b-103">Windows Communication Foundation (WCF) fornece um mecanismo automático para a integração com o Enterprise Services (consulte [integração de aplicativos COM+](../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)).</span><span class="sxs-lookup"><span data-stu-id="5d11b-103">Windows Communication Foundation (WCF) provides an automatic mechanism for integrating with Enterprise Services (see [Integrating with COM+ Applications](../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)).</span></span> <span data-ttu-id="5d11b-104">No entanto, convém a flexibilidade para desenvolver serviços que usam internamente componentes transacionais hospedados em serviços corporativos.</span><span class="sxs-lookup"><span data-stu-id="5d11b-104">However, you may want the flexibility to develop services that internally use transactional components hosted within Enterprise Services.</span></span> <span data-ttu-id="5d11b-105">Como o recurso de transações do WCF é compilado com o <xref:System.Transactions> infra-estrutura, o processo para a integração do Enterprise Services com o WCF é idêntico ao que, para especificar a interoperabilidade entre <xref:System.Transactions> e os serviços corporativos, conforme descrito na [Interoperabilidade com serviços da empresa e transações COM+](https://go.microsoft.com/fwlink/?LinkId=94949).</span><span class="sxs-lookup"><span data-stu-id="5d11b-105">Because the WCF Transactions feature is built on the <xref:System.Transactions> infrastructure, the process for integrating Enterprise Services with WCF is identical to that for specifying interoperability between <xref:System.Transactions> and Enterprise Services, as outlined in [Interoperability with Enterprise Services and COM+ Transactions](https://go.microsoft.com/fwlink/?LinkId=94949).</span></span>  
  
 <span data-ttu-id="5d11b-106">Para fornecer o nível desejado de interoperabilidade entre a transação fluída de entrada e a transação de contexto COM+, a implementação do serviço deve criar uma <xref:System.Transactions.TransactionScope> da instância e usar o valor apropriado do <xref:System.Transactions.EnterpriseServicesInteropOption> enumeração.</span><span class="sxs-lookup"><span data-stu-id="5d11b-106">To provide the desired level of interoperability between the incoming flowed transaction and the COM+ context transaction, the service implementation must create a <xref:System.Transactions.TransactionScope> instance and use the appropriate value from the <xref:System.Transactions.EnterpriseServicesInteropOption> enumeration.</span></span>  
  
## <a name="integrating-enterprise-services-with-a-service-operation"></a><span data-ttu-id="5d11b-107">A integração do Enterprise Services com uma operação de serviço</span><span class="sxs-lookup"><span data-stu-id="5d11b-107">Integrating Enterprise Services with a Service Operation</span></span>  
 <span data-ttu-id="5d11b-108">O código a seguir demonstra uma operação, com fluxo de transação permitido, que cria um <xref:System.Transactions.TransactionScope> com o <xref:System.Transactions.EnterpriseServicesInteropOption.Full> opção.</span><span class="sxs-lookup"><span data-stu-id="5d11b-108">The following code demonstrates an operation, with Allowed transaction flow, that creates a <xref:System.Transactions.TransactionScope> with the <xref:System.Transactions.EnterpriseServicesInteropOption.Full> option.</span></span> <span data-ttu-id="5d11b-109">As seguintes condições se aplicam nesse cenário:</span><span class="sxs-lookup"><span data-stu-id="5d11b-109">The following conditions apply in this scenario:</span></span>  
  
-   <span data-ttu-id="5d11b-110">Se o cliente flua de uma transação, a operação, incluindo a chamada para o componente de serviços corporativos, é executada dentro do escopo da transação.</span><span class="sxs-lookup"><span data-stu-id="5d11b-110">If the client flows a transaction, the operation, including the call to the Enterprise Services component, is executed within the scope of that transaction.</span></span> <span data-ttu-id="5d11b-111">Usando o <xref:System.Transactions.EnterpriseServicesInteropOption.Full> garante que a transação esteja sincronizada com o <xref:System.EnterpriseServices> contexto, o que significa que a transação de ambiente para <xref:System.Transactions> e o <xref:System.EnterpriseServices> é o mesmo.</span><span class="sxs-lookup"><span data-stu-id="5d11b-111">Using <xref:System.Transactions.EnterpriseServicesInteropOption.Full> ensures that the transaction is synchronized with the <xref:System.EnterpriseServices> context, which means that the ambient transaction for <xref:System.Transactions> and the <xref:System.EnterpriseServices> is the same.</span></span>  
  
-   <span data-ttu-id="5d11b-112">Se o cliente não fluir uma transação, a configuração <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> para `true` cria um novo escopo de transação para a operação.</span><span class="sxs-lookup"><span data-stu-id="5d11b-112">If the client does not flow a transaction, setting <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> to `true` creates a new transaction scope for the operation.</span></span> <span data-ttu-id="5d11b-113">Da mesma forma, usando <xref:System.Transactions.EnterpriseServicesInteropOption.Full> garante que a transação da operação é o mesmo que a transação usada dentro de <xref:System.EnterpriseServices> contexto do componente.</span><span class="sxs-lookup"><span data-stu-id="5d11b-113">Similarly, using <xref:System.Transactions.EnterpriseServicesInteropOption.Full> ensures that the operation’s transaction is the same as the transaction used inside the <xref:System.EnterpriseServices> component's context.</span></span>  
  
 <span data-ttu-id="5d11b-114">Quaisquer chamadas de método adicional também ocorrem dentro do escopo da transação da mesma operação.</span><span class="sxs-lookup"><span data-stu-id="5d11b-114">Any additional method calls also occur within the scope of the same operation’s transaction.</span></span>  
  
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
  
 <span data-ttu-id="5d11b-115">Se nenhuma sincronização é necessária entre a transação atual de uma operação e chamadas para componentes transacionais de Enterprise Services, em seguida, use o <xref:System.Transactions.EnterpriseServicesInteropOption.None> opção ao instanciar o <xref:System.Transactions.TransactionScope> instância.</span><span class="sxs-lookup"><span data-stu-id="5d11b-115">If no synchronization is required between an operation’s current transaction and calls to transactional Enterprise Services components, then use the <xref:System.Transactions.EnterpriseServicesInteropOption.None> option when instantiating the <xref:System.Transactions.TransactionScope> instance.</span></span>  
  
## <a name="integrating-enterprise-services-with-a-client"></a><span data-ttu-id="5d11b-116">A integração com um cliente do Enterprise Services</span><span class="sxs-lookup"><span data-stu-id="5d11b-116">Integrating Enterprise Services with a Client</span></span>  
 <span data-ttu-id="5d11b-117">O código a seguir demonstra o código de cliente usando um <xref:System.Transactions.TransactionScope> de instância com o <xref:System.Transactions.EnterpriseServicesInteropOption.Full> configuração.</span><span class="sxs-lookup"><span data-stu-id="5d11b-117">The following code demonstrates client code using a <xref:System.Transactions.TransactionScope> instance with the <xref:System.Transactions.EnterpriseServicesInteropOption.Full> setting.</span></span> <span data-ttu-id="5d11b-118">Nesse cenário, as chamadas para operações de serviço que dão suporte ao fluxo de transações ocorrem dentro do escopo da mesma transação que as chamadas para componentes de serviços corporativos.</span><span class="sxs-lookup"><span data-stu-id="5d11b-118">In this scenario, calls to service operations that support transaction flow occur within the scope of the same transaction as the calls to Enterprise Services components.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="5d11b-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5d11b-119">See also</span></span>
- [<span data-ttu-id="5d11b-120">Integração de aplicativos COM+</span><span class="sxs-lookup"><span data-stu-id="5d11b-120">Integrating with COM+ Applications</span></span>](../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)
- [<span data-ttu-id="5d11b-121">Integração de aplicativos COM</span><span class="sxs-lookup"><span data-stu-id="5d11b-121">Integrating with COM Applications</span></span>](../../../../docs/framework/wcf/feature-details/integrating-with-com-applications.md)
