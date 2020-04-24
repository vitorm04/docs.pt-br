---
title: Criando novos referências a entidades
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: a42f81b3-0403-4e34-b346-7d2129804e54
ms.openlocfilehash: 8c81aae89bbe5979dffdc47a369349bd2b3f2df7
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710980"
---
# <a name="creating-new-entity-references"></a>Criando novos referências a entidades
O método **CreateEntityReference** cria um novo nó **XmlEntityReference**. O modelo de objeto de documento XML (DOM) parece para ver se o nome de entidade que está sendo referenciado foi declarado. Se ele tiver sido, os nós filho do nó **XmlEntityReference** serão copiados do nó de declaração de entidade. Se não houver nenhuma declaração de entidade que corresponde, um nó vazia de texto é anexado como o único filho do nó de referência de entidade. Como os nós filho do nó **XmlEntityReference** são cópias de outros nós, esses nós filhos são somente leitura e não podem ser modificados.  
  
 Quando os nós são copiados, pode haver namespace no escopo na referência de entidade. Este namespace afeta a configuração de qualquer elemento ou nós de atributo gerado.  
  
> [!NOTE]
> O DOM adiciona nós filho a **EntityReference** somente quando você insere o nó **EntityReference** no documento. Os nós **EntityReference** recém-criados não têm nós filhos.  
  
 Embora **XmlDataDocument** seja uma classe derivada de **XmlDocument**, **XmlDataDocument** não dá suporte à criação de referências de entidade. Isso ocorre porque os filhos de **EntityReference** são somente leitura. Os filhos de um nó **EntityReference** podem abranger mais de uma região. Nesse caso, a parte de uma linha associada à região que contém uma parte de **EntityReference** será somente leitura.  
  
## <a name="see-also"></a>Veja também

- [XML Document Object Model (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
