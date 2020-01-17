---
title: Integração de componentes transacionais de Enterprise Services
ms.date: 03/30/2017
ms.assetid: 05dab277-b8b2-48cf-b40c-826be128b175
ms.openlocfilehash: 5914f76639adc3ff569a3bfb8d6eb1db14313e76
ms.sourcegitcommit: 09b4090b78f52fd09b0e430cd4b26576f1fdf96e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/17/2020
ms.locfileid: "76211944"
---
# <a name="integrating-enterprise-services-transactional-components"></a>Integração de componentes transacionais de Enterprise Services

O Windows Communication Foundation (WCF) fornece um mecanismo automático para a integração com os serviços corporativos (consulte [integração com aplicativos com+](integrating-with-com-plus-applications.md)). No entanto, talvez você queira a flexibilidade para desenvolver serviços que usam internamente componentes transacionais hospedados nos serviços corporativos. Como o recurso de transações do WCF se baseia na infraestrutura de <xref:System.Transactions>, o processo de integração dos serviços corporativos ao WCF é idêntico àquele para especificar a interoperabilidade entre <xref:System.Transactions> e serviços corporativos, conforme descrito em [interoperabilidade com os serviços corporativos e as transações com+](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.0/ms229974(v=vs.85)).  
  
 Para fornecer o nível desejado de interoperabilidade entre a transação de fluxo de entrada e a transação de contexto COM+, a implementação do serviço deve criar uma instância de <xref:System.Transactions.TransactionScope> e usar o valor apropriado da enumeração <xref:System.Transactions.EnterpriseServicesInteropOption>.  
  
## <a name="integrating-enterprise-services-with-a-service-operation"></a>Integrando serviços corporativos a uma operação de serviço  
 O código a seguir demonstra uma operação, com fluxo de transações permitido, que cria um <xref:System.Transactions.TransactionScope> com a opção <xref:System.Transactions.EnterpriseServicesInteropOption.Full>. As seguintes condições se aplicam neste cenário:  
  
- Se o cliente fluir uma transação, a operação, incluindo a chamada para o componente Enterprise Services, será executada dentro do escopo dessa transação. O uso de <xref:System.Transactions.EnterpriseServicesInteropOption.Full> garante que a transação seja sincronizada com o contexto <xref:System.EnterpriseServices>, o que significa que a transação de ambiente para <xref:System.Transactions> e <xref:System.EnterpriseServices> é a mesma.  
  
- Se o cliente não fluir em uma transação, definir <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> como `true` criará um novo escopo de transação para a operação. Da mesma forma, o uso de <xref:System.Transactions.EnterpriseServicesInteropOption.Full> garante que a transação da operação seja igual à transação usada dentro do contexto do componente <xref:System.EnterpriseServices>.  
  
 Todas as chamadas de método adicionais também ocorrem dentro do escopo da transação da mesma operação.  
  
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
  
 Se nenhuma sincronização for necessária entre a transação atual de uma operação e as chamadas para componentes de serviços corporativos transacionais, use a opção <xref:System.Transactions.EnterpriseServicesInteropOption.None> ao instanciar a instância de <xref:System.Transactions.TransactionScope>.  
  
## <a name="integrating-enterprise-services-with-a-client"></a>Integrando serviços corporativos a um cliente  
 O código a seguir demonstra o código do cliente usando uma instância <xref:System.Transactions.TransactionScope> com a configuração <xref:System.Transactions.EnterpriseServicesInteropOption.Full>. Nesse cenário, as chamadas para operações de serviço que dão suporte ao fluxo de transações ocorrem dentro do escopo da mesma transação que as chamadas para componentes de serviços corporativos.  
  
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
  
## <a name="see-also"></a>Veja também

- [Integração de aplicativos COM+](../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)
- [Integração de aplicativos COM](../../../../docs/framework/wcf/feature-details/integrating-with-com-applications.md)
