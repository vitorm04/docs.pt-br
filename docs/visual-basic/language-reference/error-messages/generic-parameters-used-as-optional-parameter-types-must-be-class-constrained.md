---
title: Parâmetros genéricos usados como tipos de parâmetro opcionais devem ter a classe restrita
ms.date: 07/20/2015
f1_keywords:
- vbc32124
- bc32124
helpviewer_keywords:
- BC32124
ms.assetid: 55aa8b2a-9ce3-4620-a710-2f9b0feb6143
ms.openlocfilehash: 9b0293472f5eda74c2bf8fb215e15ae5cf8d8b98
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58813893"
---
# <a name="generic-parameters-used-as-optional-parameter-types-must-be-class-constrained"></a>Parâmetros genéricos usados como tipos de parâmetro opcionais devem ter a classe restrita
Um procedimento é declarado com um parâmetro opcional que usa um parâmetro de tipo que não é restrito para ser um tipo de referência.  
  
 Você sempre deve fornecer um valor padrão para cada parâmetro opcional. Se o parâmetro é de um tipo de referência, o valor opcional deve ser `Nothing`, que é um valor válido para qualquer tipo de referência. No entanto, se o parâmetro é de um tipo de valor, esse tipo deve ser um tipo de dados elementares predefinido pelo Visual Basic. Isso ocorre porque um tipo de valor composto, como uma estrutura definida pelo usuário, tem nenhum valor padrão válido.  
  
 Quando você usa um parâmetro de tipo para um parâmetro opcional, você deve assegurar-se de um tipo de referência para evitar a possibilidade de um tipo de valor com nenhum valor padrão válido. Isso significa que você deve restringir o parâmetro de tipo com o `Class` palavra-chave ou com o nome de uma classe específica.  
  
 **ID do erro:** BC32124  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Restringir o parâmetro de tipo para aceitar apenas um tipo de referência, ou não usá-lo para o parâmetro opcional.  
  
## <a name="see-also"></a>Consulte também

- [Tipos genéricos no Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [Lista de Tipos](../../../visual-basic/language-reference/statements/type-list.md)
- [Instrução Class](../../../visual-basic/language-reference/statements/class-statement.md)
- [Parâmetros Opcionais](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md)
- [Estruturas](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [Nothing](../../../visual-basic/language-reference/nothing.md)
