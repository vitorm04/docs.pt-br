---
title: '&#39;&lt;expressão&gt; &#39; não pode ser usado como restrição de tipo'
ms.date: 07/20/2015
f1_keywords:
- bc32061
- vbc32061
helpviewer_keywords:
- BC32061
ms.assetid: b17821b7-fa14-4397-a211-6e2a14079f09
ms.openlocfilehash: 8e9aad2ec65e037b15e19ca2e624fdc8f28bc94e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="39ltexpressiongt39-cannot-be-used-as-a-type-constraint"></a>&#39;&lt;expressão&gt; &#39; não pode ser usado como restrição de tipo
Uma lista de restrições inclui uma expressão que não representa uma restrição válida em um parâmetro de tipo.  
  
 Uma lista de restrições impõe exigências no tipo de argumento passado para o parâmetro de tipo. Você pode especificar os requisitos a seguir em qualquer combinação:  
  
-   O argumento de tipo deve implementar uma ou mais interfaces  
  
-   O argumento de tipo deve herdar de no máximo uma classe  
  
-   O argumento de tipo deve expor um construtor sem parâmetros que pode acessar o código de criação (incluem o `New` restrição)  
  
 Se você não incluir qualquer interface ou classe específica na lista de restrição, você pode impor uma necessidade de mais geral, especificando um destes procedimentos:  
  
-   O argumento de tipo deve ser um tipo de valor (incluem o `Structure` restrição)  
  
-   O argumento de tipo deve ser um tipo de referência (incluem o `Class` restrição)  
  
 Não é possível especificar `Structure` e `Class` para o mesmo tipo de parâmetro e você não pode especificar um mais de uma vez.  
  
 **ID do erro:** BC32061  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Verifique se a expressão e seus elementos estão escritos corretamente.  
  
-   Se a expressão não está qualificada para a lista anterior de requisitos, remova-o da lista de restrições.  
  
-   Se a expressão se refere a uma interface ou classe, verifique se o compilador tem acesso a essa interface ou classe. Talvez você precise qualificar seu nome, e talvez seja necessário adicionar uma referência ao seu projeto. Para obter mais informações, consulte "Referências a projetos" [referências a elementos declarados](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).  
  
## <a name="see-also"></a>Consulte também  
 [Tipos genéricos no Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [Tipos de Valor e Tipos de Referência](../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)  
 [Referências a Elementos Declarados](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)  
 
