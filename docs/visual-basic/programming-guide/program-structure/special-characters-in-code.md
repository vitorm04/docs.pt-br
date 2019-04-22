---
title: Caracteres especiais no código (Visual Basic)
ms.date: 07/20/2015
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
ms.openlocfilehash: 65fcd10521742e287c7934080b3352a06668df7a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58835551"
---
# <a name="special-characters-in-code-visual-basic"></a>Caracteres especiais no código (Visual Basic)
Às vezes, você precisa usar caracteres especiais em seu código, ou seja, os caracteres que não estão em ordem alfabética ou numérica. A pontuação e caracteres especiais no conjunto de caracteres do Visual Basic têm vários usos, desde a organização do texto do programa para definir as tarefas que o compilador ou o programa compilado executa. Eles não especificam uma operação a ser executada.  
  
## <a name="parentheses"></a>Parênteses  
 Use parênteses quando você define um procedimento, como um `Sub` ou `Function`. Você deve colocar todas as listas de argumentos de procedimento entre parênteses. Você também usar parênteses para colocar as variáveis ou argumentos em grupos lógicos, especialmente para substituir a ordem padrão de precedência de operador em uma expressão complexa. O exemplo a seguir ilustra essa situação.  
  
 [!code-vb[VbVbcnConventions#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#11)]  
  
 Após a execução do código anterior, o valor de `d` é 8.225 e o valor de `e` é 3. O cálculo da `d` usa a prioridade padrão de `/` pela `+` e é equivalente a `d = b + (c / a)`. Os parênteses no cálculo de `e` substituir a precedência padrão.  
  
## <a name="separators"></a>Separadores  
 Separadores fazem o que seu nome sugere: separar seções de código. No Visual Basic, o caractere separador é os dois-pontos (`:`). Use separadores quando você deseja incluir várias instruções em uma única linha, em vez de linhas separadas. Isso economiza espaço e melhora a legibilidade do código. O exemplo a seguir mostra três instruções separadas por vírgulas.  
  
 [!code-vb[VbVbcnConventions#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#12)]  
  
 Para obter mais informações, confira [Como: Quebrar e combinar instruções no código](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md).  
  
 Os dois-pontos (`:`) caractere também é usado para identificar um rótulo de declaração. Para obter mais informações, confira [Como: Rotular instruções](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md).  
  
## <a name="concatenation"></a>Concatenação  
 Use o `&` operador para *concatenação*, ou vinculação de cadeias de caracteres. Não confunda isso com o `+` operador, que soma os valores numéricos. Se você usar o `+` operador para concatenar quando você opera em valores numéricos, você pode obter resultados incorretos. O exemplo a seguir demonstra isso.  
  
 [!code-vb[VbVbcnConventions#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#13)]  
  
 Após a execução do código anterior, o valor de `resultA` é 21.01 e o valor de `resultB` é "10.0111".  
  
## <a name="member-access-operators"></a>Operadores de acesso de membro  
 Para acessar um membro de um tipo, você pode usar o ponto (`.`) ou ponto de exclamação (`!`) operador entre o nome do tipo e o nome do membro.  
  
### <a name="dot--operator"></a>Ponto (.) Operador  
 Use o `.` operador em uma classe, estrutura, interface ou enumeração como um operador de acesso de membro. O membro pode ser um campo, propriedade, evento ou método. O exemplo a seguir ilustra essa situação.  
  
 [!code-vb[VbVbcnConventions#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#14)]  
  
### <a name="exclamation-point--operator"></a>Ponto de exclamação (!) Operador  
 Use o `!` operador apenas em uma classe ou interface como um operador de acesso do dicionário. A classe ou interface deve ter uma propriedade padrão que aceita um único `String` argumento. O identificador imediatamente após o `!` operador torna-se o valor do argumento passado para a propriedade padrão como uma cadeia de caracteres. O exemplo a seguir demonstra isso.  
  
 [!code-vb[VbVbcnConventions#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#15)]  
  
 As três linhas de saída `MsgBox` tudo exibir o valor `32856`. A primeira linha usa o tradicional acesso à propriedade `index`, o segundo faz uso do fato de que `index` é a propriedade padrão da classe `hasDefault`, e o terceiro usa o acesso ao dicionário para a classe.  
  
 Observe que o segundo operando do `!` operador deve ser um identificador válido do Visual Basic não incluído entre aspas duplas (`" "`). Em outras palavras, é possível usar um literal de cadeia de caracteres ou uma variável de cadeia de caracteres. A seguinte alteração para a última linha do `MsgBox` chamada gera um erro porque `"X"` é uma cadeia de caracteres literal.  
  
 `"Dictionary access returns " & hD!"X")`  
  
> [!NOTE]
>  Referências a coleções padrão devem ser explícitas. Em particular, você não pode usar o `!` operador em uma variável de associação tardia.  
  
 O `!` caractere também é usado como o `Single` caractere de tipo.  
  
## <a name="see-also"></a>Consulte também

- [Estrutura do Programa e Convenções de Código](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)
- [Caracteres de Tipo](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)
