---
title: "Caracteres especiais no código (Visual Basic) | Documentos do Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.)
- vb.(
- vb.colon
- vb.!
- vb..
- 'vb.:'
dev_langs:
- VB
helpviewer_keywords:
- special characters, in code
- parentheses, using in code
- colons (:)
- period character in code
- dot operator (.)
- dictionary access operator
- concatenation operators, special characters in code
- concatenation operators, vs. addition operator
- '! operator'
- separators, using in code
- operators [Visual Basic], dictionary access
- ': separator character'
- member access operator
- addition operator
- operators [Visual Basic], member access
- . operator
- exclamation points
- separators
- exclamation point operator (!)
- Visual Basic code, special characters
ms.assetid: 310dce0c-45b5-4e0d-83e9-32df258d2a3e
caps.latest.revision: 21
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
ms.openlocfilehash: 6d4b6e74ef3dfab3a7174da07cff7100fa4b2a2f
ms.lasthandoff: 03/13/2017

---
# <a name="special-characters-in-code-visual-basic"></a>Caracteres especiais no código (Visual Basic)
Às vezes, você precisa usar caracteres especiais em seu código, ou seja, caracteres não alfabéticos ou numéricos. A pontuação e caracteres especiais na [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] conjunto de caracteres têm vários usos, desde a organização do texto do programa para definir as tarefas que o compilador ou o programa compilado executa. Eles não especificam uma operação a ser executada.  
  
## <a name="parentheses"></a>Parênteses  
 Use parênteses quando você define um procedimento, como um `Sub` ou `Function`. Você deve colocar todas as listas de argumentos de procedimento entre parênteses. Você também usar parênteses para colocar as variáveis ou argumentos em grupos lógicos, especialmente para substituir a ordem padrão de precedência de operador em uma expressão complexa. O exemplo a seguir ilustra essa situação.  
  
 [!code-vb[VbVbcnConventions n º&11;](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/special-characters-in-code_1.vb)]  
  
 Após a execução do código anterior, o valor de `d` é 8.225 e o valor de `e` é 3. O cálculo de `d` usa a prioridade padrão de `/` pela `+` e é equivalente a `d = b + (c / a)`. Os parênteses no cálculo de `e` substituem a precedência padrão.  
  
## <a name="separators"></a>Separadores  
 Separadores fazem o que seu nome sugere: separar seções de código. Em [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)], o caractere separador é dois-pontos (`:`). Use separadores quando você deseja incluir várias instruções em uma única linha, em vez de linhas separadas. Isso economiza espaço e melhora a legibilidade do código. O exemplo a seguir mostra três instruções separadas por vírgulas.  
  
 [!code-vb[VbVbcnConventions&#12;](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/special-characters-in-code_2.vb)]  
  
 Para obter mais informações, consulte [como: Break e combinar instruções no código](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md).  
  
 Os dois-pontos (`:`) caractere também é usado para identificar um rótulo de declaração. Para obter mais informações, consulte [como: Label Statements](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md).  
  
## <a name="concatenation"></a>Concatenação  
 Use o `&` operador para *concatenação*, ou vincular cadeias de caracteres. Não confunda isso com o `+` operador, que soma os valores numéricos. Se você usar o `+` operador para concatenar quando você opera em valores numéricos, você pode obter resultados incorretos. O exemplo a seguir demonstra isso.  
  
 [!code-vb[VbVbcnConventions&13;](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/special-characters-in-code_3.vb)]  
  
 Após a execução do código anterior, o valor de `resultA` é 21.01 e o valor de `resultB` é "10.0111".  
  
## <a name="member-access-operators"></a>Operadores de acesso de membro  
 Para acessar um membro de um tipo, você pode usar o ponto (`.`) ou ponto de exclamação (`!`) operador entre o nome do tipo e o nome do membro.  
  
### <a name="dot--operator"></a>Operador ponto (.) Operador  
 Use o `.` operador em uma classe, estrutura, interface ou enumeração como um operador de acesso de membro. O membro pode ser um campo, propriedade, evento ou método. O exemplo a seguir ilustra essa situação.  
  
 [!code-vb[VbVbcnConventions&#14;](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/special-characters-in-code_4.vb)]  
  
### <a name="exclamation-point--operator"></a>Ponto de exclamação (!) Operador  
 Use o `!` operador apenas em uma classe ou interface como um operador de acesso de dicionário. A classe ou interface deve ter uma propriedade padrão que aceita um único `String` argumento. O identificador imediatamente após o `!` operador torna-se o valor do argumento passado para a propriedade padrão como uma cadeia de caracteres. O exemplo a seguir demonstra isso.  
  
 [!code-vb[VbVbcnConventions&#15;](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/special-characters-in-code_5.vb)]  
  
 Saída de três linhas de `MsgBox` all Exibe o valor `32856`. A primeira linha usa o acesso à propriedade tradicional `index`, o segundo faz uso do fato de que `index` é a propriedade padrão da classe `hasDefault`, e o terceiro usa dicionário acesso à classe.  
  
 Observe que o segundo operando do `!` operador deve ser um identificador válido Visual Basic não entre aspas duplas (`" "`). Em outras palavras, você não pode usar uma cadeia de caracteres literal ou variável de cadeia de caracteres. A seguinte alteração para a última linha do `MsgBox` chamada gera um erro porque `"X"` é uma de cadeia de caracteres literal.  
  
 `"Dictionary access returns " & hD!"X")`  
  
> [!NOTE]
>  Referências às coleções padrão devem ser explícitas. Em particular, você não pode usar o `!` operador em uma variável de associação tardia.  
  
 O `!` caractere também é usado como o `Single` caractere de tipo.  
  
## <a name="see-also"></a>Consulte também  
 [Estrutura do programa e convenções de código](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)   
 [Caracteres de Tipo](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)
