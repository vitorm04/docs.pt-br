---
title: 'Como: Personalizar feeds com o provedor de reflexão (WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, customizing
- WCF Data Services, customizing feeds
ms.assetid: 00c23dcf-9bb8-459a-a012-6c4d9bcad7e9
ms.openlocfilehash: fb22e87569a8e243813b3186232b6989abeb2a5e
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91161302"
---
# <a name="how-to-customize-feeds-with-the-reflection-provider-wcf-data-services"></a>Como: Personalizar feeds com o provedor de reflexão (WCF Data Services)

WCF Data Services permite que você personalize a serialização Atom em uma resposta do serviço de dados para que as propriedades de uma entidade possam ser mapeadas para elementos não utilizados que são definidos no protocolo AtomPub. Este tópico mostra como definir atributos de mapeamento para os tipos de entidade em um modelo de dados que é definido usando o provedor de reflexão. Para obter mais informações, consulte [personalização de feed](feed-customization-wcf-data-services.md).  
  
 O modelo de dados para este exemplo é definido no tópico [como criar um serviço de dados usando o provedor de reflexão](create-a-data-service-using-rp-wcf-data-services.md)  
  
## <a name="example"></a>Exemplo  

 No exemplo a seguir, ambas as propriedades do `Order` tipo são mapeadas para elementos Atom existentes. A `Product` Propriedade do `Item` tipo é mapeada para um atributo de feed personalizado em um namespace separado.  
  
 [!code-csharp[Astoria Custom Feeds#CustomIQueryableFeeds](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_custom_feeds/cs/orderitems.svc.cs#customiqueryablefeeds)]
 [!code-vb[Astoria Custom Feeds#CustomIQueryableFeeds](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_custom_feeds/vb/orderitems.svc.vb#customiqueryablefeeds)]  
  
## <a name="example"></a>Exemplo  

 O exemplo anterior retorna o seguinte resultado para o URI `http://myservice/OrderItems.svc/Orders(0)?$expand=Items` .  
  
 [!code-xml[Astoria Custom Feeds#IQueryableFeedResultInline](../../../../samples/snippets/xml/VS_Snippets_Misc/astoria_custom_feeds/xml/iqueryablefeedresultinline.xml#iqueryablefeedresultinline)]  
  
## <a name="see-also"></a>Confira também

- [Provedor de reflexão](reflection-provider-wcf-data-services.md)
