---
title: Estático (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Static
helpviewer_keywords:
- static modifier
- Static keyword [Visual Basic]
ms.assetid: 19013910-4658-47b6-a22e-1744b527979e
ms.openlocfilehash: de4f67fc5b60de48383a8ca886cff02b03830318
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58814150"
---
# <a name="static-visual-basic"></a>Estático (Visual Basic)
Especifica que um ou mais variáveis locais declaradas devem continuar a existir e manter seus valores mais recentes após o encerramento do procedimento no qual eles são declarados.  
  
## <a name="remarks"></a>Comentários  
 Normalmente, uma variável local em um procedimento deixa de existir assim que o procedimento será interrompida. Uma variável estática continua a existir e mantém seu valor mais recente. Na próxima vez em que seu código chama o procedimento, a variável não for reiniciada, e ela ainda mantém o valor mais recente que você atribuiu a ele. Uma variável estática continua existindo durante a vida útil da classe ou módulo que é definido em.  
  
## <a name="rules"></a>Regras  
  
-   **Contexto da declaração.** Você pode usar `Static` somente nas variáveis locais. Isso significa que o contexto da declaração para um `Static` variável deve ser um procedimento ou um bloco em um procedimento, e ele não pode ser um arquivo de origem, namespace, classe, estrutura ou módulo.  
  
     Não é possível usar `Static` dentro de um procedimento de estrutura.  
  
-   Os tipos de dados de `Static` variáveis locais não podem ser inferidas. Para obter mais informações, consulte [inferência de tipo Local](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).  
  
-   **Modificadores combinados.** Não é possível especificar `Static` junto com `ReadOnly`, `Shadows`, ou `Shared` na mesma declaração.  
  
## <a name="behavior"></a>Comportamento  
 Quando você declara uma variável estática em uma `Shared` procedimento, apenas uma cópia da variável estática está disponível para o aplicativo inteiro. Você chama um `Shared` nome do procedimento, usando a classe, não uma variável que aponta para uma instância da classe.  
  
 Quando você declara uma variável estática em um procedimento que não seja `Shared`, somente uma cópia da variável está disponível para cada instância da classe. Você pode chamar um procedimento não compartilhado usando uma variável que aponta para uma instância específica da classe.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir demonstra o uso de `Static`.  
  
 [!code-vb[VbVbalrKeywords#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#5)]  
  
 O `Static` variável `totalSales` será inicializada como 0, apenas uma vez. Cada vez que você insere `updateSales`, `totalSales` ainda tem o valor mais recente que calculou para ela.  
  
 O `Static` modificador pode ser usado neste contexto:  
  
 [Instrução Dim](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
## <a name="see-also"></a>Consulte também

- [Sombras](../../../visual-basic/language-reference/modifiers/shadows.md)
- [Compartilhado](../../../visual-basic/language-reference/modifiers/shared.md)
- [Tempo de vida no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)
- [Declaração de Variável](../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [Estruturas](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [Inferência de Tipo de Variável Local](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [Objetos e Classes](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
