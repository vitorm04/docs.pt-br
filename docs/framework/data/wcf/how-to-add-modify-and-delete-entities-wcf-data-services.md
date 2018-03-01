---
title: 'Como: adicionar, modificar e excluir entidades (WCF Data Services)'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, changing data
ms.assetid: a00f8933-b232-4445-95ba-adc634f055d8
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 0899a179ae51c4884f30fd93fddbcfe289d8d7a2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-modify-and-delete-entities-wcf-data-services"></a>Como: adicionar, modificar e excluir entidades (WCF Data Services)
Com o [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] bibliotecas de cliente, você pode criar, atualizar e excluir dados de entidade em um serviço de dados executando as ações equivalentes em objetos de <xref:System.Data.Services.Client.DataServiceContext>. Para obter mais informações, consulte [atualizar o serviço de dados](../../../../docs/framework/data/wcf/updating-the-data-service-wcf-data-services.md).  
  
 O exemplo deste tópico usa o serviço de dados de exemplo Northwind e as classes de serviço de dados do cliente geradas automaticamente. Esse serviço e as classes de dados do cliente são criadas quando você concluir o [WCF Data Services quickstart](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir cria uma nova instância de objeto e, em seguida, chama o <xref:System.Data.Services.Client.DataServiceContext.AddObject%2A> método sobre o <xref:System.Data.Services.Client.DataServiceContext> para criar o item no contexto. Uma mensagem HTTP POST é enviada para os dados de serviço quando o <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> método é chamado.  
  
 [!code-csharp[Astoria Northwind Client#AddProduct](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#addproduct)]
 [!code-vb[Astoria Northwind Client#AddProduct](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#addproduct)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir recupera e modifica um objeto existente e, em seguida, chama o <xref:System.Data.Services.Client.DataServiceContext.UpdateObject%2A> método o <xref:System.Data.Services.Client.DataServiceContext> marcar o item no contexto como atualizado. Uma mensagem HTTP MERGE é enviada para os dados de serviço quando o <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> método é chamado.  
  
 [!code-csharp[Astoria Northwind Client#ModifyCustomer](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#modifycustomer)]
 [!code-vb[Astoria Northwind Client#ModifyCustomer](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#modifycustomer)]  
  
## <a name="example"></a>Exemplo  
 A exemplo a seguir chama o <xref:System.Data.Services.Client.DataServiceContext.DeleteObject%2A> método o <xref:System.Data.Services.Client.DataServiceContext> para marcar o item no contexto como excluído. Uma mensagem HTTP DELETE é enviada para os dados de serviço quando o <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> método é chamado.  
  
 [!code-csharp[Astoria Northwind Client#DeleteProduct](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#deleteproduct)]
 [!code-vb[Astoria Northwind Client#DeleteProduct](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#deleteproduct)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir cria uma nova instância de objeto e, em seguida, chama o <xref:System.Data.Services.Client.DataServiceContext.AddRelatedObject%2A> método sobre o <xref:System.Data.Services.Client.DataServiceContext> para criar o item de contexto junto com o link para o pedido relacionado. Uma mensagem HTTP POST é enviada para os dados de serviço quando o <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> método é chamado.  
  
 [!code-csharp[Astoria Northwind Client#AddOrderDetailToOrderAuto](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#addorderdetailtoorderauto)]
 [!code-vb[Astoria Northwind Client#AddOrderDetailToOrderAuto](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#addorderdetailtoorderauto)]  
  
## <a name="see-also"></a>Consulte também  
 [WCF Data Services Client Library](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md) (Biblioteca de clientes do WCF Data Services)  
 [Como anexar uma entidade existente ao DataServiceContext](../../../../docs/framework/data/wcf/attach-an-existing-entity-to-dc-wcf-data.md)  
 [Como definir relações entre entidades](../../../../docs/framework/data/wcf/how-to-define-entity-relationships-wcf-data-services.md)  
 [Operações de envio em lote](../../../../docs/framework/data/wcf/batching-operations-wcf-data-services.md)
