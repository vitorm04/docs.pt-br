---
title: Como criar uma expressão lambda (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- lambda expressions [Visual Basic]
- expressions [Visual Basic], lambda
ms.assetid: 3279bd5c-80f7-410a-a7ba-f7085ed36aa5
ms.openlocfilehash: f437166bc5206b4145d6508aa2131ec94d6eca95
ms.sourcegitcommit: 70c76a12449439bac0f7a359866be5a0311ce960
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/25/2018
ms.locfileid: "39244884"
---
# <a name="how-to-create-a-lambda-expression-visual-basic"></a>Como criar uma expressão lambda (Visual Basic)
Um *expressão lambda* é uma função ou sub-rotina que não tem um nome. Uma expressão lambda pode ser usada sempre que um tipo de delegado é válido.  
  
### <a name="to-create-a-single-line-lambda-expression-function"></a>Para criar uma função de expressão lambda de linha única  
  
1.  Em qualquer situação em que um tipo de delegado pode ser usado, digite a palavra-chave `Function`, conforme mostrado no exemplo a seguir:  
  
     `Dim add1 =`   `Function`  
  
2.  Entre parênteses, diretamente após `Function`, digite os parâmetros da função. Observe que você não especificar um nome após `Function`.  
  
     `Dim add1 = Function`   `(num As Integer)`  
  
3.  A seguir a lista de parâmetros, digite uma única expressão como corpo da função. O valor que avalia a expressão é o valor retornado pela função. Você não usar um `As` cláusula para especificar o tipo de retorno.  
  
     [!code-vb[VbVbalrLambdas#1](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_1.vb)]  
  
     Para chamar a expressão lambda, passando um argumento de inteiro.  
  
     [!code-vb[VbVbalrLambdas#2](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_2.vb)]  
  
4.  Como alternativa, o mesmo resultado é realizado pelo exemplo a seguir:  
  
     [!code-vb[VbVbalrLambdas#3](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_3.vb)]  
  
### <a name="to-create-a-single-line-lambda-expression-subroutine"></a>Para criar uma sub-rotina de expressão lambda de linha única  
  
1.  Em qualquer situação em que um tipo de delegado pode ser usado, digite a palavra-chave `Sub`, conforme mostrado no exemplo a seguir.  
  
     `Dim add1 =`   `Sub`  
  
2.  Entre parênteses, diretamente após `Sub`, digite os parâmetros da sub-rotina. Observe que você não especificar um nome após `Sub`.  
  
     `Dim add1 = Sub`   `(msg As String)`  
  
3.  A seguir a lista de parâmetros, digite uma única instrução, como o corpo da sub-rotina.  
  
     [!code-vb[VbVbalrLambdas#17](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_4.vb)]  
  
     Para chamar a expressão lambda, passando um argumento de cadeia de caracteres.  
  
     [!code-vb[VbVbalrLambdas#18](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_5.vb)]  
  
### <a name="to-create-a-multiline-lambda-expression-function"></a>Para criar uma função de expressão lambda com várias linhas  
  
1.  Em qualquer situação em que um tipo de delegado pode ser usado, digite a palavra-chave `Function`, conforme mostrado no exemplo a seguir.  
  
     `Dim add1 =`   `Function`  
  
2.  Entre parênteses, diretamente após `Function`, digite os parâmetros da função. Observe que você não especificar um nome após `Function`.  
  
     `Dim add1 = Function`   `(index As Integer)`  
  
3.  Pressione ENTER. O `End Function` instrução é adicionada automaticamente.  
  
4.  Dentro do corpo da função, adicione o seguinte código para criar uma expressão e o valor de retorno. Você não usar um `As` cláusula para especificar o tipo de retorno.  
  
     [!code-vb[VbVbalrLambdas#19](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_6.vb)]  
  
     Para chamar a expressão lambda, passando um argumento de inteiro.  
  
     [!code-vb[VbVbalrLambdas#20](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_7.vb)]  
  
### <a name="to-create-a-multiline-lambda-expression-subroutine"></a>Para criar uma sub-rotina de expressão lambda com várias linhas  
  
1.  Em qualquer situação em que um tipo de delegado pode ser usado, digite a palavra-chave `Sub`, conforme mostrado no exemplo a seguir:  
  
     `Dim add1 =`   `Sub`  
  
2.  Entre parênteses, diretamente após `Sub`, digite os parâmetros da sub-rotina. Observe que você não especificar um nome após `Sub`.  
  
     `Dim add1 = Sub`  `(msg As String)`  
  
3.  Pressione ENTER. O `End Sub` instrução é adicionada automaticamente.  
  
4.  Dentro do corpo da função, adicione o seguinte código para ser executado quando a sub-rotina é invocada.  
  
     [!code-vb[VbVbalrLambdas#21](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_8.vb)]  
  
     Para chamar a expressão lambda, passando um argumento de cadeia de caracteres.  
  
     [!code-vb[VbVbalrLambdas#22](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_9.vb)]  
  
## <a name="example"></a>Exemplo  
 Um uso comum de expressões lambda é definir uma função que pode ser passada como o argumento para um parâmetro cujo tipo é `Delegate`. No exemplo a seguir, o <xref:System.Diagnostics.Process.GetProcesses%2A> método retorna uma matriz de processos em execução no computador local. O <xref:System.Linq.Enumerable.Where%2A> método a partir de <xref:System.Linq.Enumerable> classe requer um `Boolean` delegar como seu argumento. A expressão lambda no exemplo é usada para essa finalidade. Ele retorna `True` para cada processo que tem apenas um thread, e eles estão selecionados em `filteredList`.  
  
 [!code-vb[VbVbalrLambdas#10](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_10.vb)]  
  
 O exemplo anterior é equivalente ao código a seguir, que é escrito em [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] sintaxe:  
  
 [!code-vb[VbVbalrLambdas#11](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_11.vb)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Linq.Enumerable>  
 [Expressões Lambda](./lambda-expressions.md)  
 [Instrução Function](../../../../visual-basic/language-reference/statements/function-statement.md)  
 [Instrução Sub](../../../../visual-basic/language-reference/statements/sub-statement.md)  
 [Delegados](../../../../visual-basic/programming-guide/language-features/delegates/index.md)  
 [Como passar procedimentos para outro procedimento no Visual Basic](../../../../visual-basic/programming-guide/language-features/delegates/how-to-pass-procedures-to-another-procedure.md)  
 [Instrução Delegate](../../../../visual-basic/language-reference/statements/delegate-statement.md)  
 [Introdução ao LINQ no Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
