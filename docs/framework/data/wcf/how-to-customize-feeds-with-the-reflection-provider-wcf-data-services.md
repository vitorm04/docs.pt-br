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
ms.openlocfilehash: d3e2d587978a4c82784c8cfc8a7acc17cf601c3a
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/28/2019
ms.locfileid: "74569142"
---
# <a name="how-to-customize-feeds-with-the-reflection-provider-wcf-data-services"></a><span data-ttu-id="3c9f9-102">Como: Personalizar feeds com o provedor de reflexão (WCF Data Services)</span><span class="sxs-lookup"><span data-stu-id="3c9f9-102">How to: Customize Feeds with the Reflection Provider (WCF Data Services)</span></span>
<span data-ttu-id="3c9f9-103">WCF Data Services permite que você personalize a serialização Atom em uma resposta do serviço de dados para que as propriedades de uma entidade possam ser mapeadas para elementos não utilizados que são definidos no protocolo AtomPub.</span><span class="sxs-lookup"><span data-stu-id="3c9f9-103">WCF Data Services enables you to customize the Atom serialization in a data service response so that properties of an entity may be mapped to unused elements that are defined in the AtomPub protocol.</span></span> <span data-ttu-id="3c9f9-104">Este tópico mostra como definir atributos de mapeamento para os tipos de entidade em um modelo de dados que é definido usando o provedor de reflexão.</span><span class="sxs-lookup"><span data-stu-id="3c9f9-104">This topic shows how to define mapping attributes for the entity types in a data model that is defined by using the reflection provider.</span></span> <span data-ttu-id="3c9f9-105">Para obter mais informações, consulte [personalização de feed](feed-customization-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="3c9f9-105">For more information, see [Feed Customization](feed-customization-wcf-data-services.md).</span></span>  
  
 <span data-ttu-id="3c9f9-106">O modelo de dados para este exemplo é definido no tópico [como criar um serviço de dados usando o provedor de reflexão](create-a-data-service-using-rp-wcf-data-services.md)</span><span class="sxs-lookup"><span data-stu-id="3c9f9-106">The data model for this example is defined in the topic [How to: Create a Data Service Using the Reflection Provider](create-a-data-service-using-rp-wcf-data-services.md)</span></span>  
  
## <a name="example"></a><span data-ttu-id="3c9f9-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3c9f9-107">Example</span></span>  
 <span data-ttu-id="3c9f9-108">No exemplo a seguir, ambas as propriedades do tipo `Order` são mapeadas para elementos Atom existentes.</span><span class="sxs-lookup"><span data-stu-id="3c9f9-108">In the following example, both properties of the `Order` type are mapped to existing Atom elements.</span></span> <span data-ttu-id="3c9f9-109">A propriedade `Product` do tipo `Item` é mapeada para um atributo de feed personalizado em um namespace separado.</span><span class="sxs-lookup"><span data-stu-id="3c9f9-109">The `Product` property of the `Item` type is mapped to a custom feed attribute in a separate namespace.</span></span>  
  
 [!code-csharp[Astoria Custom Feeds#CustomIQueryableFeeds](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_custom_feeds/cs/orderitems.svc.cs#customiqueryablefeeds)]
 [!code-vb[Astoria Custom Feeds#CustomIQueryableFeeds](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_custom_feeds/vb/orderitems.svc.vb#customiqueryablefeeds)]  
  
## <a name="example"></a><span data-ttu-id="3c9f9-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3c9f9-110">Example</span></span>  
 <span data-ttu-id="3c9f9-111">O exemplo anterior retorna o seguinte resultado para o URI `http://myservice/OrderItems.svc/Orders(0)?$expand=Items`.</span><span class="sxs-lookup"><span data-stu-id="3c9f9-111">The previous example returns the following result for the URI `http://myservice/OrderItems.svc/Orders(0)?$expand=Items`.</span></span>  
  
 [!code-xml[Astoria Custom Feeds#IQueryableFeedResultInline](../../../../samples/snippets/xml/VS_Snippets_Misc/astoria_custom_feeds/xml/iqueryablefeedresultinline.xml#iqueryablefeedresultinline)]  
  
## <a name="see-also"></a><span data-ttu-id="3c9f9-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3c9f9-112">See also</span></span>

- [<span data-ttu-id="3c9f9-113">Provedor de reflexão</span><span class="sxs-lookup"><span data-stu-id="3c9f9-113">Reflection Provider</span></span>](reflection-provider-wcf-data-services.md)
