---
title: 'Como: Adicionar, modificar e excluir entidades (WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, changing data
ms.assetid: a00f8933-b232-4445-95ba-adc634f055d8
ms.openlocfilehash: 66f115bf3bf51b4b5612240c4e34eaf9e08bec0d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61765551"
---
# <a name="how-to-add-modify-and-delete-entities-wcf-data-services"></a>Como: Adicionar, modificar e excluir entidades (WCF Data Services)
Com o [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] bibliotecas de cliente, você pode criar, atualizar e excluir dados de entidade em um serviço de dados, executando as ações equivalentes em objetos no <xref:System.Data.Services.Client.DataServiceContext>. Para obter mais informações, consulte [atualização do serviço de dados](../../../../docs/framework/data/wcf/updating-the-data-service-wcf-data-services.md).  
  
 O exemplo deste tópico usa o serviço de dados de exemplo Northwind e as classes de serviço de dados do cliente geradas automaticamente. Esse serviço e as classes de dados do cliente são criadas quando você concluir o [início rápido do WCF Data Services](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir cria uma nova instância de objeto e, em seguida, chama o <xref:System.Data.Services.Client.DataServiceContext.AddObject%2A> método no <xref:System.Data.Services.Client.DataServiceContext> para criar o item no contexto. Uma mensagem HTTP POST é enviada para os dados de serviço quando o <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> método é chamado.  
  
 [!code-csharp[Astoria Northwind Client#AddProduct](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#addproduct)]
 [!code-vb[Astoria Northwind Client#AddProduct](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#addproduct)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir recupera e modifica um objeto existente e, em seguida, chama o <xref:System.Data.Services.Client.DataServiceContext.UpdateObject%2A> método no <xref:System.Data.Services.Client.DataServiceContext> para marcar o item no contexto como atualizados. Uma mensagem HTTP MERGE é enviada para os dados de serviço quando o <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> método é chamado.  
  
 [!code-csharp[Astoria Northwind Client#ModifyCustomer](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#modifycustomer)]
 [!code-vb[Astoria Northwind Client#ModifyCustomer](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#modifycustomer)]  
  
## <a name="example"></a>Exemplo  
 A exemplo a seguir chama o <xref:System.Data.Services.Client.DataServiceContext.DeleteObject%2A> método no <xref:System.Data.Services.Client.DataServiceContext> para marcar o item no contexto como excluído. Uma mensagem HTTP DELETE é enviada para os dados de serviço quando o <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> método é chamado.  
  
 [!code-csharp[Astoria Northwind Client#DeleteProduct](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#deleteproduct)]
 [!code-vb[Astoria Northwind Client#DeleteProduct](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#deleteproduct)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir cria uma nova instância de objeto e, em seguida, chama o <xref:System.Data.Services.Client.DataServiceContext.AddRelatedObject%2A> método no <xref:System.Data.Services.Client.DataServiceContext> para criar o item no contexto junto com o link para o pedido relacionado. Uma mensagem HTTP POST é enviada para os dados de serviço quando o <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> método é chamado.  
  
 [!code-csharp[Astoria Northwind Client#AddOrderDetailToOrderAuto](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#addorderdetailtoorderauto)]
 [!code-vb[Astoria Northwind Client#AddOrderDetailToOrderAuto](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#addorderdetailtoorderauto)]  
  
## <a name="see-also"></a>Consulte também

- [WCF Data Services Client Library](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md) (Biblioteca de clientes do WCF Data Services)
- [Como: Anexar uma entidade existente ao DataServiceContext](../../../../docs/framework/data/wcf/attach-an-existing-entity-to-dc-wcf-data.md)
- [Como: Definir relações entre entidades](../../../../docs/framework/data/wcf/how-to-define-entity-relationships-wcf-data-services.md)
- [Operações de envio em lote](../../../../docs/framework/data/wcf/batching-operations-wcf-data-services.md)
