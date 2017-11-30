---
title: "Como: Personalizar Feeds com o provedor de reflexão (WCF Data Services)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, customizing
- WCF Data Services, customizing feeds
ms.assetid: 00c23dcf-9bb8-459a-a012-6c4d9bcad7e9
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 26a7d3f0316a62f1e3fd655e6b00ca23297c8d7b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-customize-feeds-with-the-reflection-provider-wcf-data-services"></a><span data-ttu-id="a143f-102">Como: Personalizar Feeds com o provedor de reflexão (WCF Data Services)</span><span class="sxs-lookup"><span data-stu-id="a143f-102">How to: Customize Feeds with the Reflection Provider (WCF Data Services)</span></span>
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]<span data-ttu-id="a143f-103">permite que você personalize a serialização Atom em uma resposta do serviço de dados para que as propriedades de uma entidade podem ser mapeadas para elementos não utilizados são definidos no protocolo de AtomPub.</span><span class="sxs-lookup"><span data-stu-id="a143f-103"> enables you to customize the Atom serialization in a data service response so that properties of an entity may be mapped to unused elements that are defined in the AtomPub protocol.</span></span> <span data-ttu-id="a143f-104">Este tópico mostra como definir atributos de mapeamento para tipos de entidade em um modelo de dados é definido usando o provedor de reflexão.</span><span class="sxs-lookup"><span data-stu-id="a143f-104">This topic shows how to define mapping attributes for the entity types in a data model that is defined by using the reflection provider.</span></span> <span data-ttu-id="a143f-105">Para obter mais informações, consulte [personalização Feed](../../../../docs/framework/data/wcf/feed-customization-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="a143f-105">For more information, see [Feed Customization](../../../../docs/framework/data/wcf/feed-customization-wcf-data-services.md).</span></span>  
  
 <span data-ttu-id="a143f-106">O modelo de dados para este exemplo é definido no tópico [como: criar um serviço de dados usando o provedor de reflexão](../../../../docs/framework/data/wcf/create-a-data-service-using-rp-wcf-data-services.md)</span><span class="sxs-lookup"><span data-stu-id="a143f-106">The data model for this example is defined in the topic [How to: Create a Data Service Using the Reflection Provider](../../../../docs/framework/data/wcf/create-a-data-service-using-rp-wcf-data-services.md)</span></span>  
  
## <a name="example"></a><span data-ttu-id="a143f-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a143f-107">Example</span></span>  
 <span data-ttu-id="a143f-108">No exemplo a seguir, ambas as propriedades do `Order` tipo são mapeados para elementos de Atom existentes.</span><span class="sxs-lookup"><span data-stu-id="a143f-108">In the following example, both properties of the `Order` type are mapped to existing Atom elements.</span></span> <span data-ttu-id="a143f-109">O `Product` propriedade o `Item` tipo é mapeado para um atributo de feed personalizado em um namespace separado.</span><span class="sxs-lookup"><span data-stu-id="a143f-109">The `Product` property of the `Item` type is mapped to a custom feed attribute in a separate namespace.</span></span>  
  
 [!code-csharp[Astoria Custom Feeds#CustomIQueryableFeeds](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria custom feeds/cs/orderitems.svc.cs#customiqueryablefeeds)]
 [!code-vb[Astoria Custom Feeds#CustomIQueryableFeeds](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria custom feeds/vb/orderitems.svc.vb#customiqueryablefeeds)]  
  
## <a name="example"></a><span data-ttu-id="a143f-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a143f-110">Example</span></span>  
 <span data-ttu-id="a143f-111">O exemplo anterior retorna o resultado a seguir para o URI `http://myservice/OrderItems.svc/Orders(0)?$expand=Items`.</span><span class="sxs-lookup"><span data-stu-id="a143f-111">The previous example returns the following result for the URI `http://myservice/OrderItems.svc/Orders(0)?$expand=Items`.</span></span>  
  
 [!code-xml[Astoria Custom Feeds#IQueryableFeedResultInline](../../../../samples/snippets/xml/VS_Snippets_Misc/astoria custom feeds/xml/iqueryablefeedresultinline.xml#iqueryablefeedresultinline)]  
  
## <a name="see-also"></a><span data-ttu-id="a143f-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a143f-112">See Also</span></span>  
 [<span data-ttu-id="a143f-113">Provedor de reflexão</span><span class="sxs-lookup"><span data-stu-id="a143f-113">Reflection Provider</span></span>](../../../../docs/framework/data/wcf/reflection-provider-wcf-data-services.md)
