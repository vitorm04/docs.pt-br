---
title: Estático (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Static
helpviewer_keywords:
- static modifier
- Static keyword [Visual Basic]
ms.assetid: 19013910-4658-47b6-a22e-1744b527979e
ms.openlocfilehash: 2cbd99a026a5ebf0e215ee5732d62ccf639d3836
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33602048"
---
# <a name="static-visual-basic"></a>Estático (Visual Basic)
Especifica que um ou mais variáveis locais declaradas devem continuar a existir e manter seus valores mais recentes após o término do procedimento no qual eles são declarados.  
  
## <a name="remarks"></a>Comentários  
 Normalmente, uma variável local em um procedimento deixa de existir assim que o procedimento será interrompida. Uma variável estática continua existindo e retém seu valor mais recente. Na próxima vez que seu código chama o procedimento, a variável não for reiniciada, e ela ainda mantém o valor mais recente que você atribuiu a ele. Uma variável estática continua a existir para o tempo de vida da classe ou módulo que está definido no.  
  
## <a name="rules"></a>Regras  
  
-   **Contexto de declaração.** Você pode usar `Static` somente nas variáveis locais. Isso significa que o contexto da declaração para um `Static` variável deve ser um procedimento ou um bloco em um procedimento, e ele não pode ser um arquivo de origem, namespace, classe, estrutura ou módulo.  
  
     Não é possível usar `Static` dentro de um procedimento de estrutura.  
  
-   Os tipos de dados de `Static` variáveis locais não podem ser inferidas. Para obter mais informações, consulte [inferência de tipo Local](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).  
  
-   **Modificadores combinados.** Não é possível especificar `Static` junto com `ReadOnly`, `Shadows`, ou `Shared` na mesma declaração.  
  
## <a name="behavior"></a>Comportamento  
 Quando você declara uma variável estática em uma `Shared` procedimento, apenas uma cópia da variável estática está disponível para o aplicativo inteiro. Você chama um `Shared` nome do procedimento, usando a classe, não uma variável que aponta para uma instância da classe.  
  
 Quando você declara uma variável estática em um procedimento que não seja `Shared`, somente uma cópia da variável está disponível para cada instância da classe. Você pode chamar um procedimento não compartilhado usando uma variável que aponta para uma instância específica da classe.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir demonstra o uso de `Static`.  
  
 [!code-vb[VbVbalrKeywords#5](../../../visual-basic/language-reference/codesnippet/VisualBasic/static_1.vb)]  
  
 O `Static` variável `totalSales` foi inicializada para 0 somente uma vez. Cada vez que você inserir `updateSales`, `totalSales` ainda tem o valor mais recente que você calculou para ela.  
  
 O `Static` modificador pode ser usado neste contexto:  
  
 [Instrução Dim](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
## <a name="see-also"></a>Consulte também  
 [Sombras](../../../visual-basic/language-reference/modifiers/shadows.md)  
 [Compartilhado](../../../visual-basic/language-reference/modifiers/shared.md)  
 [Tempo de vida no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)  
 [Declaração de Variável](../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)  
 [Estruturas](../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [Inferência de Tipo de Variável Local](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [Objetos e Classes](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
