---
title: Integração de componentes transacionais de Enterprise Services
ms.date: 03/30/2017
ms.assetid: 05dab277-b8b2-48cf-b40c-826be128b175
ms.openlocfilehash: c73be31bef67f1de818f7b04181a3540bbd7caa8
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991545"
---
# <a name="integrating-enterprise-services-transactional-components"></a>Integração de componentes transacionais de Enterprise Services
O Windows Communication Foundation (WCF) fornece um mecanismo automático para a integração com os serviços corporativos (consulte [integração com aplicativos com+](../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)). No entanto, talvez você queira a flexibilidade para desenvolver serviços que usam internamente componentes transacionais hospedados nos serviços corporativos. Como o recurso de transações do WCF é criado <xref:System.Transactions> na infraestrutura, o processo de integração dos serviços corporativos com o WCF é idêntico ao de especificar <xref:System.Transactions> a interoperabilidade entre o e os serviços corporativos, conforme descrito em [Interoperabilidade com os serviços corporativos e as transações com+](https://go.microsoft.com/fwlink/?LinkId=94949).  
  
 Para fornecer o nível desejado de interoperabilidade entre a transação de fluxo de entrada e a transação de contexto com+, a implementação do <xref:System.Transactions.TransactionScope> serviço deve criar uma instância e usar o <xref:System.Transactions.EnterpriseServicesInteropOption> valor apropriado da enumeração.  
  
## <a name="integrating-enterprise-services-with-a-service-operation"></a>Integrando serviços corporativos a uma operação de serviço  
 O código a seguir demonstra uma operação, com fluxo de transações permitido, que <xref:System.Transactions.TransactionScope> cria um <xref:System.Transactions.EnterpriseServicesInteropOption.Full> com a opção. As seguintes condições se aplicam neste cenário:  
  
- Se o cliente fluir uma transação, a operação, incluindo a chamada para o componente Enterprise Services, será executada dentro do escopo dessa transação. O <xref:System.Transactions.EnterpriseServicesInteropOption.Full> uso de garante que a transação seja sincronizada com o <xref:System.EnterpriseServices> contexto, o que significa que <xref:System.Transactions> a transação <xref:System.EnterpriseServices> de ambiente para e a é a mesma.  
  
- Se o cliente não fluir em uma transação, <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> a `true` configuração para criará um novo escopo de transação para a operação. Da mesma forma <xref:System.Transactions.EnterpriseServicesInteropOption.Full> , o uso de garante que a transação da operação seja igual à transação usada <xref:System.EnterpriseServices> dentro do contexto do componente.  
  
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
  
 Se nenhuma sincronização for necessária entre a transação atual de uma operação e as chamadas para componentes de serviços corporativos transacionais <xref:System.Transactions.EnterpriseServicesInteropOption.None> , use a opção ao <xref:System.Transactions.TransactionScope> instanciar a instância.  
  
## <a name="integrating-enterprise-services-with-a-client"></a>Integrando serviços corporativos a um cliente  
 O código a seguir demonstra o código do <xref:System.Transactions.TransactionScope> cliente usando uma <xref:System.Transactions.EnterpriseServicesInteropOption.Full> instância com a configuração. Nesse cenário, as chamadas para operações de serviço que dão suporte ao fluxo de transações ocorrem dentro do escopo da mesma transação que as chamadas para componentes de serviços corporativos.  
  
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
  
## <a name="see-also"></a>Consulte também

- [Integração de aplicativos COM+](../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)
- [Integração de aplicativos COM](../../../../docs/framework/wcf/feature-details/integrating-with-com-applications.md)
