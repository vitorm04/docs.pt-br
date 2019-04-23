---
title: 'Como: Criar uma expressão Lambda (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- lambda expressions [Visual Basic]
- expressions [Visual Basic], lambda
ms.assetid: 3279bd5c-80f7-410a-a7ba-f7085ed36aa5
ms.openlocfilehash: fc2b7ed2004b842116d051b393f00506428def61
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59344540"
---
# <a name="how-to-create-a-lambda-expression-visual-basic"></a>Como: Criar uma expressão Lambda (Visual Basic)
Um *expressão lambda* é uma função ou sub-rotina que não tem um nome. Uma expressão lambda pode ser usada sempre que um tipo de delegado é válido.  
  
### <a name="to-create-a-single-line-lambda-expression-function"></a>Para criar uma função de expressão lambda de linha única  
  
1. Em qualquer situação em que um tipo de delegado pode ser usado, digite a palavra-chave `Function`, conforme mostrado no exemplo a seguir:  
  
     `Dim add1 =`   `Function`  
  
2. Entre parênteses, diretamente após `Function`, digite os parâmetros da função. Observe que você não especificar um nome após `Function`.  
  
     `Dim add1 = Function`   `(num As Integer)`  
  
3. A seguir a lista de parâmetros, digite uma única expressão como corpo da função. O valor que avalia a expressão é o valor retornado pela função. Você não usar um `As` cláusula para especificar o tipo de retorno.  
  
     [!code-vb[VbVbalrLambdas#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#1)]  
  
     Para chamar a expressão lambda, passando um argumento de inteiro.  
  
     [!code-vb[VbVbalrLambdas#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#2)]  
  
4. Como alternativa, o mesmo resultado é realizado pelo exemplo a seguir:  
  
     [!code-vb[VbVbalrLambdas#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#3)]  
  
### <a name="to-create-a-single-line-lambda-expression-subroutine"></a>Para criar uma sub-rotina de expressão lambda de linha única  
  
1. Em qualquer situação em que um tipo de delegado pode ser usado, digite a palavra-chave `Sub`, conforme mostrado no exemplo a seguir.  
  
     `Dim add1 =`   `Sub`  
  
2. Entre parênteses, diretamente após `Sub`, digite os parâmetros da sub-rotina. Observe que você não especificar um nome após `Sub`.  
  
     `Dim add1 = Sub`   `(msg As String)`  
  
3. A seguir a lista de parâmetros, digite uma única instrução, como o corpo da sub-rotina.  
  
     [!code-vb[VbVbalrLambdas#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#17)]  
  
     Para chamar a expressão lambda, passando um argumento de cadeia de caracteres.  
  
     [!code-vb[VbVbalrLambdas#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#18)]  
  
### <a name="to-create-a-multiline-lambda-expression-function"></a>Para criar uma função de expressão lambda com várias linhas  
  
1. Em qualquer situação em que um tipo de delegado pode ser usado, digite a palavra-chave `Function`, conforme mostrado no exemplo a seguir.  
  
     `Dim add1 =`   `Function`  
  
2. Entre parênteses, diretamente após `Function`, digite os parâmetros da função. Observe que você não especificar um nome após `Function`.  
  
     `Dim add1 = Function`   `(index As Integer)`  
  
3. Pressione ENTER. O `End Function` instrução é adicionada automaticamente.  
  
4. Dentro do corpo da função, adicione o seguinte código para criar uma expressão e o valor de retorno. Você não usar um `As` cláusula para especificar o tipo de retorno.  
  
     [!code-vb[VbVbalrLambdas#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#19)]  
  
     Para chamar a expressão lambda, passando um argumento de inteiro.  
  
     [!code-vb[VbVbalrLambdas#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#20)]  
  
### <a name="to-create-a-multiline-lambda-expression-subroutine"></a>Para criar uma sub-rotina de expressão lambda com várias linhas  
  
1. Em qualquer situação em que um tipo de delegado pode ser usado, digite a palavra-chave `Sub`, conforme mostrado no exemplo a seguir:  
  
     `Dim add1 =`   `Sub`  
  
2. Entre parênteses, diretamente após `Sub`, digite os parâmetros da sub-rotina. Observe que você não especificar um nome após `Sub`.  
  
     `Dim add1 = Sub`  `(msg As String)`  
  
3. Pressione ENTER. O `End Sub` instrução é adicionada automaticamente.  
  
4. Dentro do corpo da função, adicione o seguinte código para ser executado quando a sub-rotina é invocada.  
  
     [!code-vb[VbVbalrLambdas#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#21)]  
  
     Para chamar a expressão lambda, passando um argumento de cadeia de caracteres.  
  
     [!code-vb[VbVbalrLambdas#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#22)]  
  
## <a name="example"></a>Exemplo  
 Um uso comum de expressões lambda é definir uma função que pode ser passada como o argumento para um parâmetro cujo tipo é `Delegate`. No exemplo a seguir, o <xref:System.Diagnostics.Process.GetProcesses%2A> método retorna uma matriz de processos em execução no computador local. O <xref:System.Linq.Enumerable.Where%2A> método a partir de <xref:System.Linq.Enumerable> classe requer um `Boolean` delegar como seu argumento. A expressão lambda no exemplo é usada para essa finalidade. Ele retorna `True` para cada processo que tem apenas um thread, e eles estão selecionados em `filteredList`.  
  
 [!code-vb[VbVbalrLambdas#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class4.vb#10)]  
  
 O exemplo anterior é equivalente ao código a seguir, que é escrito em [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] sintaxe:  
  
 [!code-vb[VbVbalrLambdas#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class5.vb#11)]  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Linq.Enumerable>
- [Expressões Lambda](./lambda-expressions.md)
- [Instrução Function](../../../../visual-basic/language-reference/statements/function-statement.md)
- [Instrução Sub](../../../../visual-basic/language-reference/statements/sub-statement.md)
- [Delegados](../../../../visual-basic/programming-guide/language-features/delegates/index.md)
- [Como: Passar procedimentos para outro procedimento no Visual Basic](../../../../visual-basic/programming-guide/language-features/delegates/how-to-pass-procedures-to-another-procedure.md)
- [Instrução Delegate](../../../../visual-basic/language-reference/statements/delegate-statement.md)
- [Introdução ao LINQ no Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
