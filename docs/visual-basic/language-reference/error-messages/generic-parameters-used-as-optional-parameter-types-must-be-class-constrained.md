---
title: Parâmetros genéricos usados como tipos de parâmetro opcionais devem ter a classe restrita
ms.date: 07/20/2015
f1_keywords:
- vbc32124
- bc32124
helpviewer_keywords:
- BC32124
ms.assetid: 55aa8b2a-9ce3-4620-a710-2f9b0feb6143
ms.openlocfilehash: 7e2b59f758ef236717a912694576b514e2ae8a60
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="generic-parameters-used-as-optional-parameter-types-must-be-class-constrained"></a>Parâmetros genéricos usados como tipos de parâmetro opcionais devem ter a classe restrita
Um procedimento é declarado com um parâmetro opcional que usa um parâmetro de tipo que não está restrita a conter um tipo de referência.  
  
 Você sempre deve fornecer um valor padrão para cada parâmetro opcional. Se o parâmetro é de um tipo de referência, o valor opcional deve ser `Nothing`, que é um valor válido para qualquer tipo de referência. No entanto, se o parâmetro é de um tipo de valor, esse tipo deve ser um tipo de dados elementar predefinido pelo Visual Basic. Isso ocorre porque um tipo de valor composto, como uma estrutura definida pelo usuário, possui nenhum valor padrão válido.  
  
 Quando você usa um parâmetro de tipo para um parâmetro opcional, você deve assegurar-se de um tipo de referência para evitar a possibilidade de um tipo de valor sem nenhum valor padrão válido. Isso significa que você deve restringir o parâmetro de tipo com o `Class` palavra-chave ou com o nome de uma classe específica.  
  
 **ID do erro:** BC32124  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Restringir o parâmetro de tipo para aceitar somente um tipo de referência, ou não usá-lo para o parâmetro opcional.  
  
## <a name="see-also"></a>Consulte também  
 [Tipos genéricos no Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [Lista de Tipos](../../../visual-basic/language-reference/statements/type-list.md)  
 [Instrução Class](../../../visual-basic/language-reference/statements/class-statement.md)  
 [Parâmetros Opcionais](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md)  
 [Estruturas](../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [Nothing](../../../visual-basic/language-reference/nothing.md)
