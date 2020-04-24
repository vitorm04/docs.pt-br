---
title: Atualizações dinâmicas a NodeLists e a NamedNodeMaps
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 76c511fd-6704-4ca4-8078-860a68d898ad
ms.openlocfilehash: 58dfde94c2f37b0a09ee795b9df20296c9f86da6
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710967"
---
# <a name="dynamic-updates-to-nodelists-and-namednodemaps"></a>Atualizações dinâmicas a NodeLists e a NamedNodeMaps
Como **XmlNodeList** e **XmlNamedNodeMap** contêm um conjunto de nós, mas o documento XML é carregado na memória e está sendo alterado, o W3C (World Wide Web Consortium) indica que os objetos que contêm conjuntos de nós precisam ser dinâmicos. Isto é, se o documento subjacente é modificada, então os dados nesses dois objetos também deve alterar. Portanto, se você tiver um **XmlNodeList** que contenha todos os elementos filho de um elemento específico (por exemplo, o elemento X), inclua um elemento adicional, o elemento Q, no documento sob o elemento X. **XmlNodeList** também deve ter esse novo elemento Q adicionado à coleção. O mesmo vale em ordem inversa. Se um nó é adicionado a **XmlNodeList**, o documento subjacente é atualizado também.  
  
## <a name="see-also"></a>Veja também

- [XML Document Object Model (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
