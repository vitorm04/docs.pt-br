---
title: 'Como: Definir relações de entidade (WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, changing data
ms.assetid: cc255524-1534-4fae-b83c-250933d5a72b
ms.openlocfilehash: 63714f97e691b2ba0177a36a599b62ca7681dcf6
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70790639"
---
# <a name="how-to-define-entity-relationships-wcf-data-services"></a>Como: Definir relações de entidade (WCF Data Services)
Quando você adiciona uma nova entidade no [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], quaisquer relações entre a nova entidade e as entidades relacionadas não são definidas automaticamente. Você pode criar e alterar relações entre instâncias de entidade e fazer com que a biblioteca de cliente reflita essas alterações no serviço de dados. Para obter mais informações, consulte [atualizando o serviço de dados](updating-the-data-service-wcf-data-services.md).  
  
 O exemplo deste tópico usa o serviço de dados de exemplo Northwind e as classes de serviço de dados do cliente geradas automaticamente. Esse serviço e as classes de dados do cliente são criados quando você conclui o guia de [início rápido do WCF Data Services](quickstart-wcf-data-services.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir cria uma nova instância de objeto e, <xref:System.Data.Services.Client.DataServiceContext.AddRelatedObject%2A> em seguida, <xref:System.Data.Services.Client.DataServiceContext> chama o método no para criar o item no contexto junto com o link para a ordem relacionada. Uma mensagem http post é enviada ao serviço de dados quando o <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> método é chamado.  
  
 [!code-csharp[Astoria Northwind Client#AddOrderDetailToOrderAuto](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#addorderdetailtoorderauto)]
 [!code-vb[Astoria Northwind Client#AddOrderDetailToOrderAuto](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#addorderdetailtoorderauto)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como usar o <xref:System.Data.Services.Client.DataServiceContext.AddObject%2A> método para adicionar um `Order_Details` objeto a um objeto `Orders` relacionado com uma referência a um objeto `Products` específico. Os <xref:System.Data.Services.Client.DataServiceContext.AddLink%2A> métodos <xref:System.Data.Services.Client.DataServiceContext.SetLink%2A> e definem as relações. Neste exemplo, as propriedades de navegação no `Order_Details` objeto também são definidas explicitamente.  
  
 [!code-csharp[Astoria Northwind Client#AddOrderDetailToOrder](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#addorderdetailtoorder)]
 [!code-vb[Astoria Northwind Client#AddOrderDetailToOrder](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#addorderdetailtoorder)]  
  
## <a name="see-also"></a>Consulte também

- [WCF Data Services Client Library](wcf-data-services-client-library.md) (Biblioteca de clientes do WCF Data Services)
- [Como: Adicionar, modificar e excluir entidades](how-to-add-modify-and-delete-entities-wcf-data-services.md)
