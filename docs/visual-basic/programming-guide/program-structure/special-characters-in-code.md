---
title: "Caracteres especiais no código (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.)
- vb.(
- vb.colon
- vb.!
- vb..
- 'vb.:'
helpviewer_keywords:
- special characters [Visual Basic], in code
- parentheses [Visual Basic], using in code
- colons (:)
- period character in code
- dot operator (.)
- dictionary access operator [Visual Basic]
- concatenation operators [Visual Basic], special characters in code
- concatenation operators [Visual Basic], vs. addition operator
- '! operator'
- separators [Visual Basic], using in code
- operators [Visual Basic], dictionary access
- ': separator character'
- member access operator [Visual Basic]
- addition operator [Visual Basic]
- operators [Visual Basic], member access
- . operator
- exclamation points
- separators
- exclamation point operator (!)
- Visual Basic code, special characters
ms.assetid: 310dce0c-45b5-4e0d-83e9-32df258d2a3e
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 11c5ef9ad41fc2362d9ba4f2cb5eb5b63a9ca31c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="special-characters-in-code-visual-basic"></a>Caracteres especiais no código (Visual Basic)
Às vezes, você precisa usar caracteres especiais em seu código, ou seja, caracteres não alfabéticos ou numéricos. A pontuação e caracteres especiais no [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] conjunto de caracteres têm vários usos, da organização de texto de programa para definir as tarefas que executa o compilador ou o programa compilado. Eles não especificam uma operação a ser executada.  
  
## <a name="parentheses"></a>Parênteses  
 Use parênteses quando você define um procedimento, como um `Sub` ou `Function`. Você deve colocar todas as listas de argumentos de procedimento entre parênteses. Você também usar parênteses para colocar as variáveis ou argumentos em grupos lógicos, especialmente para substituir a ordem padrão de precedência de operador em uma expressão complexa. O exemplo a seguir ilustra essa situação.  
  
 [!code-vb[VbVbcnConventions#11](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/special-characters-in-code_1.vb)]  
  
 Após a execução do código anterior, o valor de `d` é 8.225 e o valor de `e` é 3. O cálculo de `d` usa a prioridade padrão de `/` sobre `+` e é equivalente a `d = b + (c / a)`. Os parênteses no cálculo de `e` anular a precedência padrão.  
  
## <a name="separators"></a>Separadores  
 Separadores fazem o que seu nome sugere: separar seções de código. Em [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)], o caractere separador é dois-pontos (`:`). Use separadores quando você deseja incluir várias instruções em uma única linha, em vez de linhas separadas. Isso economiza espaço e melhora a legibilidade do seu código. O exemplo a seguir mostra três instruções separadas por vírgulas.  
  
 [!code-vb[VbVbcnConventions#12](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/special-characters-in-code_2.vb)]  
  
 Para obter mais informações, consulte [como: Break e combinar instruções no código](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md).  
  
 Os dois-pontos (`:`) caractere também é usado para identificar um rótulo de declaração. Para obter mais informações, consulte [como: instruções de rótulo](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md).  
  
## <a name="concatenation"></a>Concatenação  
 Use o `&` operador para *concatenação*, ou vincular cadeias de caracteres. Não confunda isso com o `+` operador, que soma os valores numéricos. Se você usar o `+` operador para concatenar quando você opera em valores numéricos, você pode obter resultados incorretos. O exemplo a seguir demonstra isso.  
  
 [!code-vb[VbVbcnConventions#13](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/special-characters-in-code_3.vb)]  
  
 Após a execução do código anterior, o valor de `resultA` é 21.01 e o valor de `resultB` é "10.0111".  
  
## <a name="member-access-operators"></a>Operadores de acesso de membro  
 Para acessar um membro de um tipo, você pode usar o ponto (`.`) ou ponto de exclamação (`!`) operador entre o nome do tipo e o nome do membro.  
  
### <a name="dot--operator"></a>Operador ponto (.) Operador  
 Use o `.` operador em uma classe, estrutura, interface ou enumeração como um operador de acesso de membro. O membro pode ser um campo, propriedade, evento ou método. O exemplo a seguir ilustra essa situação.  
  
 [!code-vb[VbVbcnConventions#14](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/special-characters-in-code_4.vb)]  
  
### <a name="exclamation-point--operator"></a>Ponto de exclamação (!) Operador  
 Use o `!` operador apenas em uma classe ou interface como um operador de acesso do dicionário. A classe ou interface deve ter uma propriedade padrão que aceita um único `String` argumento. O identificador imediatamente após o `!` operador torna-se o valor do argumento passado para a propriedade padrão como uma cadeia de caracteres. O exemplo a seguir demonstra isso.  
  
 [!code-vb[VbVbcnConventions#15](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/special-characters-in-code_5.vb)]  
  
 Saída de três linhas de `MsgBox` all Exibe o valor `32856`. A primeira linha usa o tradicional acesso à propriedade `index`, o segundo faz uso do fato de que `index` é a propriedade padrão da classe `hasDefault`, e o terceiro usa dicionário acesso à classe.  
  
 Observe que o segundo operando do `!` operador deve ser um identificador válido do Visual Basic não entre aspas duplas (`" "`). Em outras palavras, você não pode usar uma cadeia de caracteres literal ou variável de cadeia de caracteres. A seguinte alteração para a última linha do `MsgBox` chamada gera um erro porque `"X"` é uma de cadeia de caracteres literal.  
  
 `"Dictionary access returns " & hD!"X")`  
  
> [!NOTE]
>  Referências a coleções padrão devem ser explícitas. Em particular, você não pode usar o `!` operador em uma variável de associação tardia.  
  
 O `!` caractere também é usado como o `Single` caractere de tipo.  
  
## <a name="see-also"></a>Consulte também  
 [Estrutura do Programa e Convenções de Código](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)  
 [Caracteres de Tipo](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)
