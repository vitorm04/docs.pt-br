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
# <a name="integrating-enterprise-services-transactional-components"></a>Integração de componentes transacionais de Enterprise Services

A Windows Communication Foundation (WCF) fornece um mecanismo automático de integração com os Serviços Corporativos (consulte [Integração com aplicativos COM+).](integrating-with-com-plus-applications.md) No entanto, você pode querer a flexibilidade para desenvolver serviços que usam internamente componentes transacionais hospedados dentro dos Serviços Corporativos. Como o recurso Transações WCF <xref:System.Transactions> é construído sobre a infra-estrutura, o processo de integração dos <xref:System.Transactions> Serviços Corporativos com o WCF é idêntico ao para especificar a interoperabilidade entre e os Serviços Corporativos, conforme descrito na [Interoperabilidade com Serviços Corporativos e Transações COM+.](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.0/ms229974(v=vs.85))  
  
 Para fornecer o nível desejado de interoperabilidade entre a transação de fluxo de entrada <xref:System.Transactions.TransactionScope> e a transação de <xref:System.Transactions.EnterpriseServicesInteropOption> contexto COM+, a implementação do serviço deve criar uma instância e usar o valor apropriado a partir da enumeração.  
  
## <a name="integrating-enterprise-services-with-a-service-operation"></a>Integrando serviços corporativos com uma operação de serviços  
 O código a seguir demonstra uma operação, <xref:System.Transactions.TransactionScope> com <xref:System.Transactions.EnterpriseServicesInteropOption.Full> fluxo de transação Permitido, que cria um com a opção. As seguintes condições se aplicam neste cenário:  
  
- Se o cliente fluir uma transação, a operação, incluindo a chamada para o componente Serviços Corporativos, será executada no âmbito dessa transação. O <xref:System.Transactions.EnterpriseServicesInteropOption.Full> uso garante que a transação seja sincronizada com o contexto, o <xref:System.EnterpriseServices> que significa que a transação ambiental para <xref:System.Transactions> e a <xref:System.EnterpriseServices> é a mesma.  
  
- Se o cliente não fluir <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> uma `true` transação, a configuração cria um novo escopo de transação para a operação. Da mesma <xref:System.Transactions.EnterpriseServicesInteropOption.Full> forma, o uso garante que a transação da <xref:System.EnterpriseServices> operação seja a mesma da transação utilizada dentro do contexto do componente.  
  
 Quaisquer chamadas de método adicionais também ocorrem no âmbito da transação da mesma operação.  
  
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
  
 Se não for necessária sincronização entre a transação atual de uma operação <xref:System.Transactions.EnterpriseServicesInteropOption.None> e chamadas para componentes transacionais do Enterprise Services, use a opção ao instanciar a <xref:System.Transactions.TransactionScope> instância.  
  
## <a name="integrating-enterprise-services-with-a-client"></a>Integrando serviços corporativos com um cliente  
 O código a seguir <xref:System.Transactions.TransactionScope> demonstra o <xref:System.Transactions.EnterpriseServicesInteropOption.Full> código do cliente usando uma instância com a configuração. Nesse cenário, as chamadas para operações de serviço que suportam o fluxo de transações ocorrem no âmbito da mesma transação que as chamadas para componentes do Enterprise Services.  
  
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
  
## <a name="see-also"></a>Confira também

- [Integração com aplicativos COM+](../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)
- [Integração com aplicativos COM](../../../../docs/framework/wcf/feature-details/integrating-with-com-applications.md)
