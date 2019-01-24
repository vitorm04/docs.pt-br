---
title: 'Como: Interceptar mensagens de serviço de dados (WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, customizing
- query interceptors [WCF Data Services]
ms.assetid: 24b9df1b-b54b-4795-a033-edf333675de6
ms.openlocfilehash: b5fdbaa25f55caf3de2f0591b7258d4a7dcb1b7e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54586391"
---
# <a name="how-to-intercept-data-service-messages-wcf-data-services"></a>Como: Interceptar mensagens de serviço de dados (WCF Data Services)
Com o [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], você pode interceptar mensagens de solicitação de modo que você possa adicionar lógica personalizada a uma operação. Para interceptar uma mensagem, você pode usar métodos especialmente atribuídos no serviço de dados. Para obter mais informações, consulte [interceptores](../../../../docs/framework/data/wcf/interceptors-wcf-data-services.md).  
  
 O exemplo neste tópico usa o serviço de dados de exemplo Northwind. Esse serviço é criado quando você concluir o [início rápido do WCF Data Services](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).  
  
### <a name="to-define-a-query-interceptor-for-the-orders-entity-set"></a>Para definir um interceptor de consulta para o conjunto de entidades Orders  
  
1.  No projeto do serviço de dados Northwind, abra o arquivo Northwind.svc.  
  
2.  Na página de código para a classe `Northwind`, adicione a instrução `using` a seguir (`Imports` no Visual Basic).  
  
     [!code-csharp[Astoria Northwind Service#UsingLinqExpressions](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind service/cs/northwind2.svc.cs#usinglinqexpressions)]
     [!code-vb[Astoria Northwind Service#UsingLinqExpressions](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind service/vb/northwind2.svc.vb#usinglinqexpressions)]  
  
3.  Na classe `Northwind`, defina um método de operação de serviço chamado `OnQueryOrders` da seguinte maneira:  
  
     [!code-csharp[Astoria Northwind Service#QueryInterceptorDef](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind service/cs/northwind2.svc.cs#queryinterceptordef)]
     [!code-vb[Astoria Northwind Service#QueryInterceptorDef](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind service/vb/northwind2.svc.vb#queryinterceptordef)]  
  
### <a name="to-define-a-change-interceptor-for-the-products-entity-set"></a>Para definir um interceptor de alteração para o conjunto de entidades Products  
  
1.  No projeto do serviço de dados Northwind, abra o arquivo Northwind.svc.  
  
2.  Na classe `Northwind`, defina um método de operação de serviço chamado `OnChangeProducts` da seguinte maneira:  
  
     [!code-csharp[Astoria Northwind Service#ChangeInterceptorDef](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind service/cs/northwind2.svc.cs#changeinterceptordef)]
     [!code-vb[Astoria Northwind Service#ChangeInterceptorDef](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind service/vb/northwind2.svc.vb#changeinterceptordef)]  
  
## <a name="example"></a>Exemplo  
 Este exemplo define um método de interceptor de consulta para o conjunto de entidades `Orders` que retorna uma expressão lambda. Esta expressão contém um delegado que filtra `Orders` solicitado com base em `Customers` relacionado que tem um nome de contato específico. O nome, por sua vez, é determinado com base no usuário solicitante. Este exemplo presume que o serviço de dados esteja hospedado dentro de um aplicativo ASP.NET que usa WCF, e a autenticação esteja habilitada. A classe <xref:System.Web.HttpContext> é usada para recuperar o princípio da solicitação atual.  
  
 [!code-csharp[Astoria Northwind Service#QueryInterceptor](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind service/cs/northwind2.svc.cs#queryinterceptor)]
 [!code-vb[Astoria Northwind Service#QueryInterceptor](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind service/vb/northwind2.svc.vb#queryinterceptor)]  
  
## <a name="example"></a>Exemplo  
 Este exemplo define um método de interceptador de alteração para o conjunto de entidades `Products`. Este método valida a entrada para o serviço para uma operação <xref:System.Data.Services.UpdateOperations.Add> ou <xref:System.Data.Services.UpdateOperations.Change> e gera uma exceção se uma alteração está sendo feita a um produto descontinuado. Ele também bloqueia a exclusão dos produtos como uma operação sem suporte.  
  
 [!code-csharp[Astoria Northwind Service#ChangeInterceptor](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind service/cs/northwind2.svc.cs#changeinterceptor)]
 [!code-vb[Astoria Northwind Service#ChangeInterceptor](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind service/vb/northwind2.svc.vb#changeinterceptor)]  
  
## <a name="see-also"></a>Consulte também
- [Como: Definir uma operação de serviço](../../../../docs/framework/data/wcf/how-to-define-a-service-operation-wcf-data-services.md)
- [Defining WCF Data Services](../../../../docs/framework/data/wcf/defining-wcf-data-services.md) (Definindo o WCF Data Services)
