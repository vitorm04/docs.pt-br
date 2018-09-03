---
title: Integração de componentes transacionais de Enterprise Services
ms.date: 03/30/2017
ms.assetid: 05dab277-b8b2-48cf-b40c-826be128b175
ms.openlocfilehash: 1fd338e57dab16a02cd31de6b45d4c5291591043
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/03/2018
ms.locfileid: "43481851"
---
# <a name="integrating-enterprise-services-transactional-components"></a>Integração de componentes transacionais de Enterprise Services
Windows Communication Foundation (WCF) fornece um mecanismo automático para a integração com o Enterprise Services (consulte [integração de aplicativos COM+](../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)). No entanto, convém a flexibilidade para desenvolver serviços que usam internamente componentes transacionais hospedados em serviços corporativos. Como o recurso de transações do WCF é compilado com o <xref:System.Transactions> infra-estrutura, o processo para a integração do Enterprise Services com o WCF é idêntico ao que, para especificar a interoperabilidade entre <xref:System.Transactions> e os serviços corporativos, conforme descrito na [Interoperabilidade com serviços da empresa e transações COM+](https://go.microsoft.com/fwlink/?LinkId=94949).  
  
 Para fornecer o nível desejado de interoperabilidade entre a transação fluída de entrada e a transação de contexto COM+, a implementação do serviço deve criar uma <xref:System.Transactions.TransactionScope> da instância e usar o valor apropriado do <xref:System.Transactions.EnterpriseServicesInteropOption> enumeração.  
  
## <a name="integrating-enterprise-services-with-a-service-operation"></a>A integração do Enterprise Services com uma operação de serviço  
 O código a seguir demonstra uma operação, com fluxo de transação permitido, que cria um <xref:System.Transactions.TransactionScope> com o <xref:System.Transactions.EnterpriseServicesInteropOption.Full> opção. As seguintes condições se aplicam nesse cenário:  
  
-   Se o cliente flua de uma transação, a operação, incluindo a chamada para o componente de serviços corporativos, é executada dentro do escopo da transação. Usando o <xref:System.Transactions.EnterpriseServicesInteropOption.Full> garante que a transação esteja sincronizada com o <xref:System.EnterpriseServices> contexto, o que significa que a transação de ambiente para <xref:System.Transactions> e o <xref:System.EnterpriseServices> é o mesmo.  
  
-   Se o cliente não fluir uma transação, a configuração <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> para `true` cria um novo escopo de transação para a operação. Da mesma forma, usando <xref:System.Transactions.EnterpriseServicesInteropOption.Full> garante que a transação da operação é o mesmo que a transação usada dentro de <xref:System.EnterpriseServices> contexto do componente.  
  
 Quaisquer chamadas de método adicional também ocorrem dentro do escopo da transação da mesma operação.  
  
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
  
 Se nenhuma sincronização é necessária entre a transação atual de uma operação e chamadas para componentes transacionais de Enterprise Services, em seguida, use o <xref:System.Transactions.EnterpriseServicesInteropOption.None> opção ao instanciar o <xref:System.Transactions.TransactionScope> instância.  
  
## <a name="integrating-enterprise-services-with-a-client"></a>A integração com um cliente do Enterprise Services  
 O código a seguir demonstra o código de cliente usando um <xref:System.Transactions.TransactionScope> de instância com o <xref:System.Transactions.EnterpriseServicesInteropOption.Full> configuração. Nesse cenário, as chamadas para operações de serviço que dão suporte ao fluxo de transações ocorrem dentro do escopo da mesma transação que as chamadas para componentes de serviços corporativos.  
  
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
  
## <a name="see-also"></a>Consulte também  
 [Integração de aplicativos COM+](../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)  
 [Integração de aplicativos COM](../../../../docs/framework/wcf/feature-details/integrating-with-com-applications.md)
