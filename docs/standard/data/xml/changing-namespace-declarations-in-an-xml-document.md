---
title: Alterando declarações namespace em um documento XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: a2758f40-e497-4964-8d8d-1bb68af14dcd
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5457eab1f34eb3e7424d508509f5dd6a42ffb51f
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73976941"
---
# <a name="changing-namespace-declarations-in-an-xml-document"></a>Alterando declarações namespace em um documento XML
**XmlDocument** expõe declarações de namespace e atributos **xmlns** como parte do modelo de objeto de documento. São armazenados em **XmlDocument**, para que, quando você salvar o documento, ele possa preservar o local desses atributos. Alterar esses atributos não tem efeito nas propriedades **Name**, **NamespaceURI** e **Prefix** de outros nós já na árvore. Por exemplo, se você carregar o documento a seguir, o elemento `test` terá **NamespaceURI** `123.`  
  
```xml  
<test xmlns="123"/>  
```  
  
 Se você remover o atributo `xmlns` como indicado a seguir, o elemento `test` ainda terá o **NamespaceURI** `123`.  
  
```vb  
doc.documentElement.RemoveAttribute("xmlns")  
```  
  
```csharp  
doc.documentElement.RemoveAttribute("xmlns");  
```  
  
 Da mesma forma, se você adicionar um atributo diferente de `xmlns` ao elemento `doc` como indicado a seguir, o elemento `test` ainda terá **NamespaceURI** `123`.  
  
```vb  
doc.documentElement.SetAttribute("xmlns","456")
```  
  
```csharp  
doc.documentElement.SetAttribute("xmlns","456");  
```  
  
 Portanto, alterar atributos `xmlns` não terá nenhum efeito até que você salve e recarregue o objeto **XmlDocument**.  
  
## <a name="see-also"></a>Consulte também

- [DOM (Modelo de Objeto do Documento) de XML](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
