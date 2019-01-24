---
title: 'Como: Personalizar Feeds com o provedor de reflexão (WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, customizing
- WCF Data Services, customizing feeds
ms.assetid: 00c23dcf-9bb8-459a-a012-6c4d9bcad7e9
ms.openlocfilehash: fe6e65a0030ca016f280e6b2c1106b4aa302d26e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54637697"
---
# <a name="how-to-customize-feeds-with-the-reflection-provider-wcf-data-services"></a>Como: Personalizar Feeds com o provedor de reflexão (WCF Data Services)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] permite personalizar a serialização Atom em uma resposta do serviço de dados para que as propriedades de uma entidade podem ser mapeadas para elementos não utilizados que são definidos no protocolo AtomPub. Este tópico mostra como definir atributos de mapeamento para tipos de entidade em um modelo de dados é definido usando o provedor de reflexão. Para obter mais informações, consulte [personalização de Feed](../../../../docs/framework/data/wcf/feed-customization-wcf-data-services.md).  
  
 O modelo de dados para este exemplo é definido no tópico [como: Criar um serviço de dados usando o provedor de reflexão](../../../../docs/framework/data/wcf/create-a-data-service-using-rp-wcf-data-services.md)  
  
## <a name="example"></a>Exemplo  
 No exemplo a seguir, ambas as propriedades do `Order` tipo são mapeados para elementos de Atom existentes. O `Product` propriedade do `Item` tipo é mapeado para um atributo de feed personalizado em um namespace separado.  
  
 [!code-csharp[Astoria Custom Feeds#CustomIQueryableFeeds](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria custom feeds/cs/orderitems.svc.cs#customiqueryablefeeds)]
 [!code-vb[Astoria Custom Feeds#CustomIQueryableFeeds](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria custom feeds/vb/orderitems.svc.vb#customiqueryablefeeds)]  
  
## <a name="example"></a>Exemplo  
 O exemplo anterior retorna o resultado a seguir para o URI `http://myservice/OrderItems.svc/Orders(0)?$expand=Items`.  
  
 [!code-xml[Astoria Custom Feeds#IQueryableFeedResultInline](../../../../samples/snippets/xml/VS_Snippets_Misc/astoria custom feeds/xml/iqueryablefeedresultinline.xml#iqueryablefeedresultinline)]  
  
## <a name="see-also"></a>Consulte também
- [Provedor de reflexão](../../../../docs/framework/data/wcf/reflection-provider-wcf-data-services.md)
