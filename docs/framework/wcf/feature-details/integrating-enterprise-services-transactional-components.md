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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a236a34dd20661d62d59a3712a1800ff1f9a11ad
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="integrating-enterprise-services-transactional-components"></a>Integração de componentes transacionais de Enterprise Services
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]Fornece um mecanismo automático para a integração com os serviços corporativos (consulte [integrando aplicativos COM+](../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)). No entanto, talvez você queira a flexibilidade para desenvolver serviços que internamente usa componentes transacionais hospedados em serviços corporativos. Porque o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] recurso de transações é criado sob o <xref:System.Transactions> infraestrutura, o processo de integração de serviços do Enterprise com [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] é idêntico para especificar a interoperabilidade entre <xref:System.Transactions> e Enterprise Serviços, conforme descrito na [interoperabilidade com serviços da empresa e transações COM+](http://go.microsoft.com/fwlink/?LinkId=94949).  
  
 Para fornecer o nível desejado de interoperabilidade entre a transação de fluxo de entrada e a transação de contexto COM+, a implementação do serviço deve criar um <xref:System.Transactions.TransactionScope> instância e usar o valor apropriado a <xref:System.Transactions.EnterpriseServicesInteropOption> enumeração.  
  
## <a name="integrating-enterprise-services-with-a-service-operation"></a>Integração de serviços corporativos com uma operação de serviço  
 O código a seguir demonstra uma operação, com o fluxo de transação permitido, que cria um <xref:System.Transactions.TransactionScope> com o <xref:System.Transactions.EnterpriseServicesInteropOption.Full> opção. As seguintes condições se aplicam neste cenário:  
  
-   Se o cliente flui de uma transação, a operação, incluindo a chamada para o componente de serviços corporativos, é executada dentro do escopo da transação. Usando <xref:System.Transactions.EnterpriseServicesInteropOption.Full> garante que a transação é sincronizada com o <xref:System.EnterpriseServices> contexto, o que significa que a transação de ambiente para <xref:System.Transactions> e <xref:System.EnterpriseServices> é o mesmo.  
  
-   Se o cliente não fluxo de uma transação, a configuração <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> para `true` cria um novo escopo de transação para a operação. Da mesma forma, usando <xref:System.Transactions.EnterpriseServicesInteropOption.Full> garante que a transação da operação é o mesmo que a transação usada dentro de <xref:System.EnterpriseServices> contexto do componente.  
  
 As chamadas de método adicionais também ocorrem dentro do escopo da transação da mesma operação.  
  
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
  
## <a name="integrating-enterprise-services-with-a-client"></a>Integração de serviços da empresa com um cliente  
 O código a seguir demonstra o código de cliente usando um <xref:System.Transactions.TransactionScope> instância com o <xref:System.Transactions.EnterpriseServicesInteropOption.Full> configuração. Nesse cenário, as chamadas para operações de serviço que dão suporte ao fluxo de transações ocorrem dentro do escopo da mesma transação, como as chamadas para os componentes de serviços corporativos.  
  
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
 [Integrando aplicativos COM+](../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)  
 [Integrando aplicativos COM](../../../../docs/framework/wcf/feature-details/integrating-with-com-applications.md)
