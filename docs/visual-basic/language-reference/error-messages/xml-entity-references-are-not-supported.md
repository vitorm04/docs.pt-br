---
title: "Não há suporte para referências de entidade XML | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc31180
- bc31180
dev_langs:
- VB
helpviewer_keywords:
- BC31180
ms.assetid: 2a393327-d8e2-4187-85b1-642b4f53b4ae
caps.latest.revision: 6
author: stevehoag
ms.author: shoag
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 6516301e21bd0c2935921dfc2c7dff688759fe8d
ms.lasthandoff: 03/13/2017

---
# <a name="xml-entity-references-are-not-supported"></a>As referências de entidade XML não são suportadas
Uma referência de entidade (por exemplo, `©`) que não está definido no XML 1.0 especificação é incluída como um valor para um literal XML. Somente `&`, `"`, `<`, `>`, e `'` referências de entidade XML são suportadas em literais XML.  
  
 **ID do erro:** BC31180  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Remova a referência de entidade sem suporte.  
  
## <a name="see-also"></a>Consulte também  
 [Literais XML e do XML 1.0 especificação](../../../visual-basic/programming-guide/language-features/xml/xml-literals-and-the-xml-1-0-specification.md)   
 [Literais XML](../../../visual-basic/language-reference/xml-literals/index.md)   
 [XML](../../../visual-basic/programming-guide/language-features/xml/index.md)
