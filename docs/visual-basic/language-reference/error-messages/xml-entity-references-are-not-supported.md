---
title: As referências de entidade XML não são suportadas
ms.date: 07/20/2015
f1_keywords:
- vbc31180
- bc31180
helpviewer_keywords:
- BC31180
ms.assetid: 2a393327-d8e2-4187-85b1-642b4f53b4ae
ms.openlocfilehash: 470e5577654ce8b6bbc2732a41c130a85ddc96e5
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874987"
---
# <a name="xml-entity-references-are-not-supported"></a>As referências de entidade XML não são suportadas

Uma referência de entidade (por exemplo, `©` ) que não está definida na especificação XML 1,0 é incluída como um valor para um literal XML. Somente `&` as `"` `<` referências de entidade XML,,, `>` e `'` são suportadas em literais XML.  
  
 **ID do erro:** BC31180  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
- Remova a referência de entidade sem suporte.  
  
## <a name="see-also"></a>Confira também

- [Especificação dos literais XML e do XML 1.0](../../programming-guide/language-features/xml/xml-literals-and-the-xml-1-0-specification.md)
- [Literais XML](../xml-literals/index.md)
- [XML](../../programming-guide/language-features/xml/index.md)
