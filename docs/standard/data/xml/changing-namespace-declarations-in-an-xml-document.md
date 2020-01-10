---
title: Alterando declarações namespace em um documento XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: a2758f40-e497-4964-8d8d-1bb68af14dcd
ms.openlocfilehash: b8aa670764deb8e77cfb67fd16dbcf8b1cc9b4c0
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75711123"
---
# <a name="changing-namespace-declarations-in-an-xml-document"></a><span data-ttu-id="ec9ee-102">Alterando declarações namespace em um documento XML</span><span class="sxs-lookup"><span data-stu-id="ec9ee-102">Changing Namespace Declarations in an XML Document</span></span>
<span data-ttu-id="ec9ee-103">**XmlDocument** expõe declarações de namespace e atributos **xmlns** como parte do modelo de objeto de documento.</span><span class="sxs-lookup"><span data-stu-id="ec9ee-103">The **XmlDocument** exposes namespace declarations and **xmlns** attributes as part of the document object model.</span></span> <span data-ttu-id="ec9ee-104">São armazenados em **XmlDocument**, para que, quando você salvar o documento, ele possa preservar o local desses atributos.</span><span class="sxs-lookup"><span data-stu-id="ec9ee-104">These are stored in the **XmlDocument**, so when you save the document, it can preserve the location of those attributes.</span></span> <span data-ttu-id="ec9ee-105">Alterar esses atributos não tem efeito nas propriedades **Name**, **NamespaceURI** e **Prefix** de outros nós já na árvore.</span><span class="sxs-lookup"><span data-stu-id="ec9ee-105">Changing these attributes has no affect on the **Name**, **NamespaceURI**, and **Prefix** properties of other nodes already in the tree.</span></span> <span data-ttu-id="ec9ee-106">Por exemplo, se você carregar o documento a seguir, o elemento `test` terá o **NamespaceURI** `123.`</span><span class="sxs-lookup"><span data-stu-id="ec9ee-106">For example, if you load the following document, then the `test` element has **NamespaceURI** `123.`</span></span>  
  
```xml  
<test xmlns="123"/>  
```  
  
 <span data-ttu-id="ec9ee-107">Se você remover o atributo `xmlns` como indicado a seguir, o elemento `test` ainda terá o **NamespaceURI**`123`.</span><span class="sxs-lookup"><span data-stu-id="ec9ee-107">If you remove the `xmlns` attribute as follows, then the `test` element still has the **NamespaceURI** of `123`.</span></span>  
  
```vb  
doc.documentElement.RemoveAttribute("xmlns")  
```  
  
```csharp  
doc.documentElement.RemoveAttribute("xmlns");  
```  
  
 <span data-ttu-id="ec9ee-108">Da mesma forma, se você adicionar um atributo `xmlns` diferente ao elemento `doc` da seguinte maneira, o elemento `test` ainda terá o **NamespaceURI** `123`.</span><span class="sxs-lookup"><span data-stu-id="ec9ee-108">Likewise, if you add a different `xmlns` attribute to the `doc` element as follows, then the `test` element still has **NamespaceURI** `123`.</span></span>  
  
```vb  
doc.documentElement.SetAttribute("xmlns","456")
```  
  
```csharp  
doc.documentElement.SetAttribute("xmlns","456");  
```  
  
 <span data-ttu-id="ec9ee-109">Portanto, alterar atributos `xmlns` não terá nenhum efeito até que você salve e recarregue o objeto **XmlDocument**.</span><span class="sxs-lookup"><span data-stu-id="ec9ee-109">Therefore, changing `xmlns` attributes will have no affect until you save and reload the **XmlDocument** object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec9ee-110">Veja também</span><span class="sxs-lookup"><span data-stu-id="ec9ee-110">See also</span></span>

- [<span data-ttu-id="ec9ee-111">DOM (Modelo de Objeto do Documento) de XML</span><span class="sxs-lookup"><span data-stu-id="ec9ee-111">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
