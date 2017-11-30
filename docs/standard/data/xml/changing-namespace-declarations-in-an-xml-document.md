---
title: "Alterando declarações namespace em um documento XML"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: a2758f40-e497-4964-8d8d-1bb68af14dcd
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 627882efcbc41310ee177cba984e4add5b07bd15
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="changing-namespace-declarations-in-an-xml-document"></a><span data-ttu-id="0cd1d-102">Alterando declarações namespace em um documento XML</span><span class="sxs-lookup"><span data-stu-id="0cd1d-102">Changing Namespace Declarations in an XML Document</span></span>
<span data-ttu-id="0cd1d-103">O **XmlDocument** expõe as declarações de namespace e **xmlns** atributos como parte do modelo de objeto do documento.</span><span class="sxs-lookup"><span data-stu-id="0cd1d-103">The **XmlDocument** exposes namespace declarations and **xmlns** attributes as part of the document object model.</span></span> <span data-ttu-id="0cd1d-104">Eles são armazenados na **XmlDocument**, portanto, quando você salvar o documento, ele pode preservar a localização desses atributos.</span><span class="sxs-lookup"><span data-stu-id="0cd1d-104">These are stored in the **XmlDocument**, so when you save the document, it can preserve the location of those attributes.</span></span> <span data-ttu-id="0cd1d-105">Alterar esses atributos não tem nenhum efeito o **nome**, **NamespaceURI**, e **prefixo** propriedades de outros nós já na árvore.</span><span class="sxs-lookup"><span data-stu-id="0cd1d-105">Changing these attributes has no affect on the **Name**, **NamespaceURI**, and **Prefix** properties of other nodes already in the tree.</span></span> <span data-ttu-id="0cd1d-106">Por exemplo, se você carregar o documento a seguir, o `test` elemento tem **NamespaceURI**`123.`</span><span class="sxs-lookup"><span data-stu-id="0cd1d-106">For example, if you load the following document, then the `test` element has **NamespaceURI** `123.`</span></span>  
  
```xml  
<test xmlns="123"/>  
```  
  
 <span data-ttu-id="0cd1d-107">Se você remover o `xmlns` atributo da seguinte maneira o `test` elemento ainda tem o **NamespaceURI** de `123`.</span><span class="sxs-lookup"><span data-stu-id="0cd1d-107">If you remove the `xmlns` attribute as follows, then the `test` element still has the **NamespaceURI** of `123`.</span></span>  
  
```vb  
doc.documentElement.RemoveAttribute("xmlns")  
```  
  
```csharp  
doc.documentElement.RemoveAttribute("xmlns");  
```  
  
 <span data-ttu-id="0cd1d-108">Da mesma forma, se você adicionar outra `xmlns` de atributo para o `doc` elemento da seguinte maneira, em seguida, o `test` ainda tem um elemento **NamespaceURI** `123`.</span><span class="sxs-lookup"><span data-stu-id="0cd1d-108">Likewise, if you add a different `xmlns` attribute to the `doc` element as follows, then the `test` element still has **NamespaceURI** `123`.</span></span>  
  
```vb  
doc.documentElement.SetAttribute("xmlns","456");  
```  
  
```csharp  
doc.documentElement.SetAttribute("xmlns","456");  
```  
  
 <span data-ttu-id="0cd1d-109">Portanto, alterar `xmlns` atributos não terá nenhum efeito até que você salve e recarregue o **XmlDocument** objeto.</span><span class="sxs-lookup"><span data-stu-id="0cd1d-109">Therefore, changing `xmlns` attributes will have no affect until you save and reload the **XmlDocument** object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0cd1d-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0cd1d-110">See Also</span></span>  
 [<span data-ttu-id="0cd1d-111">XML Document Object Model (DOM)</span><span class="sxs-lookup"><span data-stu-id="0cd1d-111">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
