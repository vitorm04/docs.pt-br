---
title: As referências de entidade XML não são suportadas
ms.date: 07/20/2015
f1_keywords:
- vbc31180
- bc31180
helpviewer_keywords:
- BC31180
ms.assetid: 2a393327-d8e2-4187-85b1-642b4f53b4ae
ms.openlocfilehash: dd7add295641e6a27c361c663d6075413b0f499c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58824683"
---
# <a name="xml-entity-references-are-not-supported"></a>As referências de entidade XML não são suportadas
Uma referência de entidade (por exemplo, `©`) que não está definido no XML 1.0 especificação é incluída como um valor para um literal XML. Somente `&`, `"`, `<`, `>`, e `'` referências de entidade XML têm suporte em literais XML.  
  
 **ID do erro:** BC31180  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Remova a referência de entidade sem suporte.  
  
## <a name="see-also"></a>Consulte também

- [Especificação dos Literais XML e do XML 1.0](../../../visual-basic/programming-guide/language-features/xml/xml-literals-and-the-xml-1-0-specification.md)
- [Literais XML](../../../visual-basic/language-reference/xml-literals/index.md)
- [XML](../../../visual-basic/programming-guide/language-features/xml/index.md)
