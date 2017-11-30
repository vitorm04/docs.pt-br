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
# <a name="changing-namespace-declarations-in-an-xml-document"></a>Alterando declarações namespace em um documento XML
O **XmlDocument** expõe as declarações de namespace e **xmlns** atributos como parte do modelo de objeto do documento. Eles são armazenados na **XmlDocument**, portanto, quando você salvar o documento, ele pode preservar a localização desses atributos. Alterar esses atributos não tem nenhum efeito o **nome**, **NamespaceURI**, e **prefixo** propriedades de outros nós já na árvore. Por exemplo, se você carregar o documento a seguir, o `test` elemento tem **NamespaceURI**`123.`  
  
```xml  
<test xmlns="123"/>  
```  
  
 Se você remover o `xmlns` atributo da seguinte maneira o `test` elemento ainda tem o **NamespaceURI** de `123`.  
  
```vb  
doc.documentElement.RemoveAttribute("xmlns")  
```  
  
```csharp  
doc.documentElement.RemoveAttribute("xmlns");  
```  
  
 Da mesma forma, se você adicionar outra `xmlns` de atributo para o `doc` elemento da seguinte maneira, em seguida, o `test` ainda tem um elemento **NamespaceURI** `123`.  
  
```vb  
doc.documentElement.SetAttribute("xmlns","456");  
```  
  
```csharp  
doc.documentElement.SetAttribute("xmlns","456");  
```  
  
 Portanto, alterar `xmlns` atributos não terá nenhum efeito até que você salve e recarregue o **XmlDocument** objeto.  
  
## <a name="see-also"></a>Consulte também  
 [XML Document Object Model (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
