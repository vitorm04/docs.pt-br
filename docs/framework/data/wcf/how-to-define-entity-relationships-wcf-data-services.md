---
title: Como definir relações de entidade (WCF Data Services)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, changing data
ms.assetid: cc255524-1534-4fae-b83c-250933d5a72b
ms.openlocfilehash: f693579883ae03a6c8df3e9a9f4941e1f9940a4c
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/28/2019
ms.locfileid: "74569115"
---
# <a name="how-to-define-entity-relationships-wcf-data-services"></a>Como definir relações de entidade (WCF Data Services)
Quando você adiciona uma nova entidade no WCF Data Services, quaisquer relações entre a nova entidade e as entidades relacionadas não são definidas automaticamente. Você pode criar e alterar relações entre instâncias de entidade e fazer com que a biblioteca de cliente reflita essas alterações no serviço de dados. Para obter mais informações, consulte [atualizando o serviço de dados](updating-the-data-service-wcf-data-services.md).  
  
 O exemplo deste tópico usa o serviço de dados de exemplo Northwind e as classes de serviço de dados do cliente geradas automaticamente. Esse serviço e as classes de dados do cliente são criados quando você conclui o guia de [início rápido do WCF Data Services](quickstart-wcf-data-services.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir cria uma nova instância de objeto e, em seguida, chama o método <xref:System.Data.Services.Client.DataServiceContext.AddRelatedObject%2A> no <xref:System.Data.Services.Client.DataServiceContext> para criar o item no contexto junto com o link para a ordem relacionada. Uma mensagem HTTP POST é enviada ao serviço de dados quando o método <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> é chamado.  
  
 [!code-csharp[Astoria Northwind Client#AddOrderDetailToOrderAuto](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#addorderdetailtoorderauto)]
 [!code-vb[Astoria Northwind Client#AddOrderDetailToOrderAuto](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#addorderdetailtoorderauto)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como usar o método <xref:System.Data.Services.Client.DataServiceContext.AddObject%2A> para adicionar um objeto de `Order_Details` a um objeto `Orders` relacionado com uma referência a um objeto `Products` específico. Os métodos <xref:System.Data.Services.Client.DataServiceContext.AddLink%2A> e <xref:System.Data.Services.Client.DataServiceContext.SetLink%2A> definem as relações. Neste exemplo, as propriedades de navegação no objeto `Order_Details` também são definidas explicitamente.  
  
 [!code-csharp[Astoria Northwind Client#AddOrderDetailToOrder](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#addorderdetailtoorder)]
 [!code-vb[Astoria Northwind Client#AddOrderDetailToOrder](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#addorderdetailtoorder)]  
  
## <a name="see-also"></a>Consulte também

- [WCF Data Services Client Library](wcf-data-services-client-library.md) (Biblioteca de clientes do WCF Data Services)
- [Como adicionar, modificar e excluir entidades](how-to-add-modify-and-delete-entities-wcf-data-services.md)
