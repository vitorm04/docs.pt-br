---
title: Integração de componentes transacionais de Enterprise Services
ms.date: 03/30/2017
ms.assetid: 05dab277-b8b2-48cf-b40c-826be128b175
ms.openlocfilehash: 292573f911459d8a8419e09d81fd1e54dbc6c70b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184747"
---
# <a name="integrating-enterprise-services-transactional-components"></a><span data-ttu-id="7e275-102">Integração de componentes transacionais de Enterprise Services</span><span class="sxs-lookup"><span data-stu-id="7e275-102">Integrating Enterprise Services Transactional Components</span></span>

<span data-ttu-id="7e275-103">A Windows Communication Foundation (WCF) fornece um mecanismo automático de integração com os Serviços Corporativos (consulte [Integração com aplicativos COM+).](integrating-with-com-plus-applications.md)</span><span class="sxs-lookup"><span data-stu-id="7e275-103">Windows Communication Foundation (WCF) provides an automatic mechanism for integrating with Enterprise Services (see [Integrating with COM+ Applications](integrating-with-com-plus-applications.md)).</span></span> <span data-ttu-id="7e275-104">No entanto, você pode querer a flexibilidade para desenvolver serviços que usam internamente componentes transacionais hospedados dentro dos Serviços Corporativos.</span><span class="sxs-lookup"><span data-stu-id="7e275-104">However, you may want the flexibility to develop services that internally use transactional components hosted within Enterprise Services.</span></span> <span data-ttu-id="7e275-105">Como o recurso Transações WCF <xref:System.Transactions> é construído sobre a infra-estrutura, o processo de integração dos <xref:System.Transactions> Serviços Corporativos com o WCF é idêntico ao para especificar a interoperabilidade entre e os Serviços Corporativos, conforme descrito na [Interoperabilidade com Serviços Corporativos e Transações COM+.](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.0/ms229974(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="7e275-105">Because the WCF Transactions feature is built on the <xref:System.Transactions> infrastructure, the process for integrating Enterprise Services with WCF is identical to that for specifying interoperability between <xref:System.Transactions> and Enterprise Services, as outlined in [Interoperability with Enterprise Services and COM+ Transactions](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.0/ms229974(v=vs.85)).</span></span>  
  
 <span data-ttu-id="7e275-106">Para fornecer o nível desejado de interoperabilidade entre a transação de fluxo de entrada <xref:System.Transactions.TransactionScope> e a transação de <xref:System.Transactions.EnterpriseServicesInteropOption> contexto COM+, a implementação do serviço deve criar uma instância e usar o valor apropriado a partir da enumeração.</span><span class="sxs-lookup"><span data-stu-id="7e275-106">To provide the desired level of interoperability between the incoming flowed transaction and the COM+ context transaction, the service implementation must create a <xref:System.Transactions.TransactionScope> instance and use the appropriate value from the <xref:System.Transactions.EnterpriseServicesInteropOption> enumeration.</span></span>  
  
## <a name="integrating-enterprise-services-with-a-service-operation"></a><span data-ttu-id="7e275-107">Integrando serviços corporativos com uma operação de serviços</span><span class="sxs-lookup"><span data-stu-id="7e275-107">Integrating Enterprise Services with a Service Operation</span></span>  
 <span data-ttu-id="7e275-108">O código a seguir demonstra uma operação, <xref:System.Transactions.TransactionScope> com <xref:System.Transactions.EnterpriseServicesInteropOption.Full> fluxo de transação Permitido, que cria um com a opção.</span><span class="sxs-lookup"><span data-stu-id="7e275-108">The following code demonstrates an operation, with Allowed transaction flow, that creates a <xref:System.Transactions.TransactionScope> with the <xref:System.Transactions.EnterpriseServicesInteropOption.Full> option.</span></span> <span data-ttu-id="7e275-109">As seguintes condições se aplicam neste cenário:</span><span class="sxs-lookup"><span data-stu-id="7e275-109">The following conditions apply in this scenario:</span></span>  
  
- <span data-ttu-id="7e275-110">Se o cliente fluir uma transação, a operação, incluindo a chamada para o componente Serviços Corporativos, será executada no âmbito dessa transação.</span><span class="sxs-lookup"><span data-stu-id="7e275-110">If the client flows a transaction, the operation, including the call to the Enterprise Services component, is executed within the scope of that transaction.</span></span> <span data-ttu-id="7e275-111">O <xref:System.Transactions.EnterpriseServicesInteropOption.Full> uso garante que a transação seja sincronizada com o contexto, o <xref:System.EnterpriseServices> que significa que a transação ambiental para <xref:System.Transactions> e a <xref:System.EnterpriseServices> é a mesma.</span><span class="sxs-lookup"><span data-stu-id="7e275-111">Using <xref:System.Transactions.EnterpriseServicesInteropOption.Full> ensures that the transaction is synchronized with the <xref:System.EnterpriseServices> context, which means that the ambient transaction for <xref:System.Transactions> and the <xref:System.EnterpriseServices> is the same.</span></span>  
  
- <span data-ttu-id="7e275-112">Se o cliente não fluir <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> uma `true` transação, a configuração cria um novo escopo de transação para a operação.</span><span class="sxs-lookup"><span data-stu-id="7e275-112">If the client does not flow a transaction, setting <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> to `true` creates a new transaction scope for the operation.</span></span> <span data-ttu-id="7e275-113">Da mesma <xref:System.Transactions.EnterpriseServicesInteropOption.Full> forma, o uso garante que a transação da <xref:System.EnterpriseServices> operação seja a mesma da transação utilizada dentro do contexto do componente.</span><span class="sxs-lookup"><span data-stu-id="7e275-113">Similarly, using <xref:System.Transactions.EnterpriseServicesInteropOption.Full> ensures that the operation’s transaction is the same as the transaction used inside the <xref:System.EnterpriseServices> component's context.</span></span>  
  
 <span data-ttu-id="7e275-114">Quaisquer chamadas de método adicionais também ocorrem no âmbito da transação da mesma operação.</span><span class="sxs-lookup"><span data-stu-id="7e275-114">Any additional method calls also occur within the scope of the same operation’s transaction.</span></span>  
  
```csharp
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
  
 <span data-ttu-id="7e275-115">Se não for necessária sincronização entre a transação atual de uma operação <xref:System.Transactions.EnterpriseServicesInteropOption.None> e chamadas para componentes transacionais do Enterprise Services, use a opção ao instanciar a <xref:System.Transactions.TransactionScope> instância.</span><span class="sxs-lookup"><span data-stu-id="7e275-115">If no synchronization is required between an operation’s current transaction and calls to transactional Enterprise Services components, then use the <xref:System.Transactions.EnterpriseServicesInteropOption.None> option when instantiating the <xref:System.Transactions.TransactionScope> instance.</span></span>  
  
## <a name="integrating-enterprise-services-with-a-client"></a><span data-ttu-id="7e275-116">Integrando serviços corporativos com um cliente</span><span class="sxs-lookup"><span data-stu-id="7e275-116">Integrating Enterprise Services with a Client</span></span>  
 <span data-ttu-id="7e275-117">O código a seguir <xref:System.Transactions.TransactionScope> demonstra o <xref:System.Transactions.EnterpriseServicesInteropOption.Full> código do cliente usando uma instância com a configuração.</span><span class="sxs-lookup"><span data-stu-id="7e275-117">The following code demonstrates client code using a <xref:System.Transactions.TransactionScope> instance with the <xref:System.Transactions.EnterpriseServicesInteropOption.Full> setting.</span></span> <span data-ttu-id="7e275-118">Nesse cenário, as chamadas para operações de serviço que suportam o fluxo de transações ocorrem no âmbito da mesma transação que as chamadas para componentes do Enterprise Services.</span><span class="sxs-lookup"><span data-stu-id="7e275-118">In this scenario, calls to service operations that support transaction flow occur within the scope of the same transaction as the calls to Enterprise Services components.</span></span>  
  
```csharp
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
  
## <a name="see-also"></a><span data-ttu-id="7e275-119">Confira também</span><span class="sxs-lookup"><span data-stu-id="7e275-119">See also</span></span>

- [<span data-ttu-id="7e275-120">Integração com aplicativos COM+</span><span class="sxs-lookup"><span data-stu-id="7e275-120">Integrating with COM+ Applications</span></span>](../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)
- [<span data-ttu-id="7e275-121">Integração com aplicativos COM</span><span class="sxs-lookup"><span data-stu-id="7e275-121">Integrating with COM Applications</span></span>](../../../../docs/framework/wcf/feature-details/integrating-with-com-applications.md)
