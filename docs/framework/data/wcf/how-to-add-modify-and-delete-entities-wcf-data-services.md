---
title: 'Como: Adicionar, modificar e excluir entidades (WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, changing data
ms.assetid: a00f8933-b232-4445-95ba-adc634f055d8
ms.openlocfilehash: 501bec59a61b51ec4bece4b0ce2f941189b35ed0
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/28/2019
ms.locfileid: "74569192"
---
# <a name="how-to-add-modify-and-delete-entities-wcf-data-services"></a>Como: Adicionar, modificar e excluir entidades (WCF Data Services)
Com as bibliotecas de cliente do WCF Data Services, você pode criar, atualizar e excluir dados de entidade em um serviço de dados executando ações equivalentes em objetos no <xref:System.Data.Services.Client.DataServiceContext>. Para obter mais informações, consulte [atualizando o serviço de dados](updating-the-data-service-wcf-data-services.md).  
  
 O exemplo deste tópico usa o serviço de dados de exemplo Northwind e as classes de serviço de dados do cliente geradas automaticamente. Esse serviço e as classes de dados do cliente são criados quando você conclui o guia de [início rápido do WCF Data Services](quickstart-wcf-data-services.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir cria uma nova instância de objeto e, em seguida, chama o método <xref:System.Data.Services.Client.DataServiceContext.AddObject%2A> no <xref:System.Data.Services.Client.DataServiceContext> para criar o item no contexto. Uma mensagem HTTP POST é enviada ao serviço de dados quando o método <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> é chamado.  
  
 [!code-csharp[Astoria Northwind Client#AddProduct](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#addproduct)]
 [!code-vb[Astoria Northwind Client#AddProduct](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#addproduct)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir recupera e modifica um objeto existente e, em seguida, chama o método <xref:System.Data.Services.Client.DataServiceContext.UpdateObject%2A> no <xref:System.Data.Services.Client.DataServiceContext> para marcar o item no contexto como atualizado. Uma mensagem de MESCLAgem HTTP é enviada ao serviço de dados quando o método <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> é chamado.  
  
 [!code-csharp[Astoria Northwind Client#ModifyCustomer](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#modifycustomer)]
 [!code-vb[Astoria Northwind Client#ModifyCustomer](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#modifycustomer)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir chama o método <xref:System.Data.Services.Client.DataServiceContext.DeleteObject%2A> no <xref:System.Data.Services.Client.DataServiceContext> para marcar o item no contexto como excluído. Uma mensagem HTTP DELETE é enviada ao serviço de dados quando o método <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> é chamado.  
  
 [!code-csharp[Astoria Northwind Client#DeleteProduct](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#deleteproduct)]
 [!code-vb[Astoria Northwind Client#DeleteProduct](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#deleteproduct)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir cria uma nova instância de objeto e, em seguida, chama o método <xref:System.Data.Services.Client.DataServiceContext.AddRelatedObject%2A> no <xref:System.Data.Services.Client.DataServiceContext> para criar o item no contexto junto com o link para a ordem relacionada. Uma mensagem HTTP POST é enviada ao serviço de dados quando o método <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> é chamado.  
  
 [!code-csharp[Astoria Northwind Client#AddOrderDetailToOrderAuto](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#addorderdetailtoorderauto)]
 [!code-vb[Astoria Northwind Client#AddOrderDetailToOrderAuto](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#addorderdetailtoorderauto)]  
  
## <a name="see-also"></a>Consulte também

- [WCF Data Services Client Library](wcf-data-services-client-library.md) (Biblioteca de clientes do WCF Data Services)
- [Como anexar uma entidade existente ao DataServiceContext](attach-an-existing-entity-to-dc-wcf-data.md)
- [Como definir relações entre entidades](how-to-define-entity-relationships-wcf-data-services.md)
- [Operações de envio em lote](batching-operations-wcf-data-services.md)
