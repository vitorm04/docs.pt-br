---
title: Integração de componentes transacionais de Enterprise Services
ms.date: 03/30/2017
ms.assetid: 05dab277-b8b2-48cf-b40c-826be128b175
ms.openlocfilehash: 1c4fabfadb113c79b216fa10ff80b551ba0f9716
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596845"
---
# <a name="integrating-enterprise-services-transactional-components"></a><span data-ttu-id="90477-102">Integração de componentes transacionais de Enterprise Services</span><span class="sxs-lookup"><span data-stu-id="90477-102">Integrating Enterprise Services Transactional Components</span></span>

<span data-ttu-id="90477-103">O Windows Communication Foundation (WCF) fornece um mecanismo automático para a integração com os serviços corporativos (consulte [integração com aplicativos com+](integrating-with-com-plus-applications.md)).</span><span class="sxs-lookup"><span data-stu-id="90477-103">Windows Communication Foundation (WCF) provides an automatic mechanism for integrating with Enterprise Services (see [Integrating with COM+ Applications](integrating-with-com-plus-applications.md)).</span></span> <span data-ttu-id="90477-104">No entanto, talvez você queira a flexibilidade para desenvolver serviços que usam internamente componentes transacionais hospedados nos serviços corporativos.</span><span class="sxs-lookup"><span data-stu-id="90477-104">However, you may want the flexibility to develop services that internally use transactional components hosted within Enterprise Services.</span></span> <span data-ttu-id="90477-105">Como o recurso de transações do WCF é criado na <xref:System.Transactions> infraestrutura, o processo de integração dos serviços corporativos com o WCF é idêntico ao de especificar a interoperabilidade entre <xref:System.Transactions> o e os serviços corporativos, conforme descrito em [interoperabilidade com os serviços corporativos e as transações com+](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.0/ms229974(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="90477-105">Because the WCF Transactions feature is built on the <xref:System.Transactions> infrastructure, the process for integrating Enterprise Services with WCF is identical to that for specifying interoperability between <xref:System.Transactions> and Enterprise Services, as outlined in [Interoperability with Enterprise Services and COM+ Transactions](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.0/ms229974(v=vs.85)).</span></span>  
  
 <span data-ttu-id="90477-106">Para fornecer o nível desejado de interoperabilidade entre a transação de fluxo de entrada e a transação de contexto COM+, a implementação do serviço deve criar uma <xref:System.Transactions.TransactionScope> instância e usar o valor apropriado da <xref:System.Transactions.EnterpriseServicesInteropOption> enumeração.</span><span class="sxs-lookup"><span data-stu-id="90477-106">To provide the desired level of interoperability between the incoming flowed transaction and the COM+ context transaction, the service implementation must create a <xref:System.Transactions.TransactionScope> instance and use the appropriate value from the <xref:System.Transactions.EnterpriseServicesInteropOption> enumeration.</span></span>  
  
## <a name="integrating-enterprise-services-with-a-service-operation"></a><span data-ttu-id="90477-107">Integrando serviços corporativos a uma operação de serviço</span><span class="sxs-lookup"><span data-stu-id="90477-107">Integrating Enterprise Services with a Service Operation</span></span>  
 <span data-ttu-id="90477-108">O código a seguir demonstra uma operação, com fluxo de transações permitido, que cria um <xref:System.Transactions.TransactionScope> com a <xref:System.Transactions.EnterpriseServicesInteropOption.Full> opção.</span><span class="sxs-lookup"><span data-stu-id="90477-108">The following code demonstrates an operation, with Allowed transaction flow, that creates a <xref:System.Transactions.TransactionScope> with the <xref:System.Transactions.EnterpriseServicesInteropOption.Full> option.</span></span> <span data-ttu-id="90477-109">As seguintes condições se aplicam neste cenário:</span><span class="sxs-lookup"><span data-stu-id="90477-109">The following conditions apply in this scenario:</span></span>  
  
- <span data-ttu-id="90477-110">Se o cliente fluir uma transação, a operação, incluindo a chamada para o componente Enterprise Services, será executada dentro do escopo dessa transação.</span><span class="sxs-lookup"><span data-stu-id="90477-110">If the client flows a transaction, the operation, including the call to the Enterprise Services component, is executed within the scope of that transaction.</span></span> <span data-ttu-id="90477-111">O uso de <xref:System.Transactions.EnterpriseServicesInteropOption.Full> garante que a transação seja sincronizada com o <xref:System.EnterpriseServices> contexto, o que significa que a transação de ambiente para <xref:System.Transactions> e a <xref:System.EnterpriseServices> é a mesma.</span><span class="sxs-lookup"><span data-stu-id="90477-111">Using <xref:System.Transactions.EnterpriseServicesInteropOption.Full> ensures that the transaction is synchronized with the <xref:System.EnterpriseServices> context, which means that the ambient transaction for <xref:System.Transactions> and the <xref:System.EnterpriseServices> is the same.</span></span>  
  
- <span data-ttu-id="90477-112">Se o cliente não fluir em uma transação, <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> a configuração para `true` criará um novo escopo de transação para a operação.</span><span class="sxs-lookup"><span data-stu-id="90477-112">If the client does not flow a transaction, setting <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> to `true` creates a new transaction scope for the operation.</span></span> <span data-ttu-id="90477-113">Da mesma forma, o uso <xref:System.Transactions.EnterpriseServicesInteropOption.Full> de garante que a transação da operação seja igual à transação usada dentro do <xref:System.EnterpriseServices> contexto do componente.</span><span class="sxs-lookup"><span data-stu-id="90477-113">Similarly, using <xref:System.Transactions.EnterpriseServicesInteropOption.Full> ensures that the operation’s transaction is the same as the transaction used inside the <xref:System.EnterpriseServices> component's context.</span></span>  
  
 <span data-ttu-id="90477-114">Todas as chamadas de método adicionais também ocorrem dentro do escopo da transação da mesma operação.</span><span class="sxs-lookup"><span data-stu-id="90477-114">Any additional method calls also occur within the scope of the same operation’s transaction.</span></span>  
  
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
  
 <span data-ttu-id="90477-115">Se nenhuma sincronização for necessária entre a transação atual de uma operação e as chamadas para componentes de serviços corporativos transacionais, use a <xref:System.Transactions.EnterpriseServicesInteropOption.None> opção ao instanciar a <xref:System.Transactions.TransactionScope> instância.</span><span class="sxs-lookup"><span data-stu-id="90477-115">If no synchronization is required between an operation’s current transaction and calls to transactional Enterprise Services components, then use the <xref:System.Transactions.EnterpriseServicesInteropOption.None> option when instantiating the <xref:System.Transactions.TransactionScope> instance.</span></span>  
  
## <a name="integrating-enterprise-services-with-a-client"></a><span data-ttu-id="90477-116">Integrando serviços corporativos a um cliente</span><span class="sxs-lookup"><span data-stu-id="90477-116">Integrating Enterprise Services with a Client</span></span>  
 <span data-ttu-id="90477-117">O código a seguir demonstra o código do cliente usando uma <xref:System.Transactions.TransactionScope> instância com a <xref:System.Transactions.EnterpriseServicesInteropOption.Full> configuração.</span><span class="sxs-lookup"><span data-stu-id="90477-117">The following code demonstrates client code using a <xref:System.Transactions.TransactionScope> instance with the <xref:System.Transactions.EnterpriseServicesInteropOption.Full> setting.</span></span> <span data-ttu-id="90477-118">Nesse cenário, as chamadas para operações de serviço que dão suporte ao fluxo de transações ocorrem dentro do escopo da mesma transação que as chamadas para componentes de serviços corporativos.</span><span class="sxs-lookup"><span data-stu-id="90477-118">In this scenario, calls to service operations that support transaction flow occur within the scope of the same transaction as the calls to Enterprise Services components.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="90477-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="90477-119">See also</span></span>

- [<span data-ttu-id="90477-120">Integração com aplicativos COM+</span><span class="sxs-lookup"><span data-stu-id="90477-120">Integrating with COM+ Applications</span></span>](integrating-with-com-plus-applications.md)
- [<span data-ttu-id="90477-121">Integração com aplicativos COM</span><span class="sxs-lookup"><span data-stu-id="90477-121">Integrating with COM Applications</span></span>](integrating-with-com-applications.md)
