---
title: 'Como: Corresponder uma cadeia de caracteres com um padrão (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- comparison operators [Visual Basic], comparing strings
- pattern matching
- strings [Visual Basic], comparing
- string comparison [Visual Basic], operators
- Visual Basic code, operators
- pattern matching [Visual Basic], string comparison
- string comparison [Visual Basic]
- Like operator [Visual Basic], pattern matching
- pattern matching, empty strings
- operators [Visual Basic], comparison
ms.assetid: 19a83804-b5af-4739-928b-ac93e64e457f
ms.openlocfilehash: c14aa35ce15549ad9eccabe2330a7c43b6795140
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59316265"
---
# <a name="how-to-match-a-string-against-a-pattern-visual-basic"></a>Como: Corresponder uma cadeia de caracteres com um padrão (Visual Basic)
Se você quiser saber se uma expressão do [tipo de dados de cadeia de caracteres](../../../../visual-basic/language-reference/data-types/string-data-type.md) satisfaz um padrão, em seguida, você pode usar o [operador Like](../../../../visual-basic/language-reference/operators/like-operator.md).  
  
 `Like` leva dois operandos. O operando esquerdo é uma expressão de cadeia de caracteres e o operando direito é uma cadeia de caracteres que contém o padrão a ser usado para correspondência. `Like` Retorna um `Boolean` valor que indica se a expressão de cadeia de caracteres satisfaz o padrão.  
  
 Você pode corresponder a cada caractere na expressão de cadeia de caracteres em relação a um caractere específico, um caractere curinga, uma lista de caracteres ou um intervalo de caracteres. As posições das especificações na cadeia de caracteres padrão correspondem para as posições dos caracteres a ser correspondida na expressão de cadeia de caracteres.  
  
### <a name="to-match-a-character-in-the-string-expression-against-a-specific-character"></a>Para corresponder um caractere na expressão de cadeia de caracteres com um caractere específico  
  
-   Coloque o caractere específico diretamente na cadeia de caracteres padrão. Determinados caracteres especiais devem ser colocados entre colchetes (`[ ]`). Para obter mais informações, consulte [operador Like](../../../../visual-basic/language-reference/operators/like-operator.md).  
  
     A exemplo a seguir testa se `myString` consiste exatamente o único caractere `H`.  
  
     [!code-vb[VbVbalrOperators#70](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#70)]  
  
### <a name="to-match-a-character-in-the-string-expression-against-a-wildcard-character"></a>Para corresponder um caractere na expressão de cadeia de caracteres com um caractere curinga  
  
-   Coloque um ponto de interrogação (`?`) na cadeia de caracteres padrão. Qualquer caractere válido nessa posição é uma correspondência com êxito.  
  
     A exemplo a seguir testa se `myString` consiste no caractere único `W` seguido por exatamente dois caracteres de todos os valores.  
  
     [!code-vb[VbVbalrOperators#71](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#71)]  
  
### <a name="to-match-a-character-in-the-string-expression-against-a-list-of-characters"></a>Para corresponder um caractere na expressão de cadeia de caracteres em uma lista de caracteres  
  
-   Coloque colchetes (`[ ]`) na cadeia de caracteres padrão e dentro dos colchetes coloque a lista de caracteres. Não separe os caracteres com vírgulas ou qualquer outro separador. Qualquer caractere único na lista é uma correspondência com êxito.  
  
     A exemplo a seguir testa se `myString` consiste em qualquer caractere válido seguido por exatamente um dos caracteres `A`, `C`, ou `E`.  
  
     [!code-vb[VbVbalrOperators#72](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#72)]  
  
     Observe que essa correspondência diferencia maiusculas de minúsculas.  
  
### <a name="to-match-a-character-in-the-string-expression-against-a-range-of-characters"></a>Para corresponder um caractere na expressão de cadeia de caracteres com um intervalo de caracteres  
  
-   Coloque colchetes (`[ ]`) na cadeia de caracteres padrão e dentro dos colchetes coloque os caracteres de menores e mais no intervalo, separados por um hífen (`–`). Qualquer caractere único dentro do intervalo é uma correspondência com êxito.  
  
     A exemplo a seguir testa se `myString` consiste em caracteres `num` seguidos por exatamente um dos caracteres `i`, `j`, `k`, `l`, `m`, ou `n`.  
  
     [!code-vb[VbVbalrOperators#73](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#73)]  
  
     Observe que essa correspondência diferencia maiusculas de minúsculas.  
  
## <a name="matching-empty-strings"></a>Correspondência de cadeias de caracteres vazias  
 `Like` trata a sequência `[]` como uma cadeia de caracteres de comprimento zero (`""`). Você pode usar `[]` para testar se a expressão de cadeia de caracteres inteira está vazia, mas você não pode usá-lo para testar se uma determinada posição na expressão de cadeia de caracteres está vazia. Se uma posição vazia é uma das opções que você precisa testar, você pode usar `Like` mais de uma vez.  
  
#### <a name="to-match-a-character-in-the-string-expression-against-a-list-of-characters-or-no-character"></a>Para corresponder um caractere na expressão de cadeia de caracteres em uma lista de caracteres ou nenhum caractere  
  
1. Chame o `Like` operador duas vezes na mesma expressão de cadeia de caracteres e conecte as duas chamadas com o [ou operador](../../../../visual-basic/language-reference/operators/or-operator.md) ou o [operador OrElse](../../../../visual-basic/language-reference/operators/orelse-operator.md).  
  
2. Na cadeia de caracteres padrão para a primeira `Like` cláusula, inclua a lista de caracteres entre colchetes (`[ ]`).  
  
3. Na cadeia de caracteres padrão para o segundo `Like` cláusula, não coloque qualquer caractere na posição em questão.  
  
     O exemplo a seguir testa o número de telefone de sete dígitos `phoneNum` para obter exatamente três dígitos numéricos, seguido por um espaço, um hífen (`–`), um período (`.`), ou nenhum caractere, seguidos por exatamente quatro dígitos numéricos.  
  
     [!code-vb[VbVbalrOperators#74](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#74)]  
  
## <a name="see-also"></a>Consulte também

- [Operadores de comparação](../../../../visual-basic/language-reference/operators/comparison-operators.md)
- [Operadores e expressões](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
- [Operador Like](../../../../visual-basic/language-reference/operators/like-operator.md)
- [Tipo de dados da cadeia de caracteres](../../../../visual-basic/language-reference/data-types/string-data-type.md)
