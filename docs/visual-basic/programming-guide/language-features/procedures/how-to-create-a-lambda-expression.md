---
title: "Como: criar uma expressão Lambda (Visual Basic) | Documentos do Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- lambda expressions [Visual Basic]
- expressions [Visual Basic], lambda
ms.assetid: 3279bd5c-80f7-410a-a7ba-f7085ed36aa5
caps.latest.revision: 27
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
ms.openlocfilehash: 5e105e87b1e63218f2c3c2204350257c139b5837
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-create-a-lambda-expression-visual-basic"></a>Como criar uma expressão lambda (Visual Basic)
A *expressão lambda* é uma função ou sub-rotina que não tem um nome. Uma expressão lambda pode ser usada sempre que um tipo delegate é válido.  
  
### <a name="to-create-a-single-line-lambda-expression-function"></a>Para criar uma função de expressão lambda de linha única  
  
1.  Em qualquer situação em que um tipo delegate pode ser usado, digite a palavra-chave `Function`, como no exemplo a seguir:  
  
     `Dim add1 =`   `Function`  
  
2.  Entre parênteses, diretamente após `Function`, digite os parâmetros da função. Observe que você não especifica um nome após `Function`.  
  
     `Dim add1 = Function`   `(num As Integer)`  
  
3.  Após a lista de parâmetros, digite uma única expressão como corpo da função. O valor que a expressão é avaliada como é o valor retornado pela função. Você não usar um `As` cláusula para especificar o tipo de retorno.  
  
     [!code-vb[VbVbalrLambdas n º&1;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_1.vb)]  
  
     Você chama a expressão lambda passando um argumento integer.  
  
     [!code-vb[VbVbalrLambdas n º&2;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_2.vb)]  
  
4.  Como alternativa, o mesmo resultado é realizado pelo exemplo a seguir:  
  
     [!code-vb[VbVbalrLambdas n º&3;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_3.vb)]  
  
### <a name="to-create-a-single-line-lambda-expression-subroutine"></a>Para criar uma sub-rotina de expressão lambda de linha única  
  
1.  Em qualquer situação em que um tipo delegate pode ser usado, digite a palavra-chave `Sub`, conforme mostrado no exemplo a seguir.  
  
     `Dim add1 =`   `Sub`  
  
2.  Entre parênteses, diretamente após `Sub`, digite os parâmetros da sub-rotina. Observe que você não especifica um nome após `Sub`.  
  
     `Dim add1 = Sub`   `(msg As String)`  
  
3.  Após a lista de parâmetros, digite uma única instrução no corpo da sub-rotina.  
  
     [!code-vb[17 VbVbalrLambdas](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_4.vb)]  
  
     Você chama a expressão lambda passando um argumento de cadeia de caracteres.  
  
     [!code-vb[VbVbalrLambdas n º&18;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_5.vb)]  
  
### <a name="to-create-a-multiline-lambda-expression-function"></a>Para criar uma função de expressão lambda com várias linhas  
  
1.  Em qualquer situação em que um tipo delegate pode ser usado, digite a palavra-chave `Function`, conforme mostrado no exemplo a seguir.  
  
     `Dim add1 =`   `Function`  
  
2.  Entre parênteses, diretamente após `Function`, digite os parâmetros da função. Observe que você não especifica um nome após `Function`.  
  
     `Dim add1 = Function`   `(index As Integer)`  
  
3.  Pressione ENTER. O `End Function` instrução é adicionada automaticamente.  
  
4.  Dentro do corpo da função, adicione o seguinte código para criar uma expressão e o valor de retorno. Você não usar um `As` cláusula para especificar o tipo de retorno.  
  
     [!code-vb[19 VbVbalrLambdas](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_6.vb)]  
  
     Você chama a expressão lambda passando um argumento integer.  
  
     [!code-vb[20 VbVbalrLambdas](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_7.vb)]  
  
### <a name="to-create-a-multiline-lambda-expression-subroutine"></a>Para criar uma sub-rotina de expressão lambda com várias linhas  
  
1.  Em qualquer situação em que um tipo delegate pode ser usado, digite a palavra-chave `Sub`, conforme mostrado no exemplo a seguir:  
  
     `Dim add1 =`   `Sub`  
  
2.  Entre parênteses, diretamente após `Sub`, digite os parâmetros da sub-rotina. Observe que você não especifica um nome após `Sub`.  
  
     `Dim add1 = Sub`  `(msg As String)`  
  
3.  Pressione ENTER. O `End Sub` instrução é adicionada automaticamente.  
  
4.  Dentro do corpo da função, adicione o seguinte código para executar quando a sub-rotina é invocada.  
  
     [!code-vb[VbVbalrLambdas&#21;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_8.vb)]  
  
     Você chama a expressão lambda passando um argumento de cadeia de caracteres.  
  
     [!code-vb[VbVbalrLambdas&#22;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_9.vb)]  
  
## <a name="example"></a>Exemplo  
 Um uso comum de expressões lambda é para definir uma função que pode ser passada como argumento para um parâmetro cujo tipo é `Delegate`. No exemplo a seguir, o <xref:System.Diagnostics.Process.GetProcesses%2A>método retorna uma matriz dos processos em execução no computador local.</xref:System.Diagnostics.Process.GetProcesses%2A> O <xref:System.Linq.Enumerable.Where%2A>método a partir de <xref:System.Linq.Enumerable>classe requer um `Boolean` delegar como seu argumento.</xref:System.Linq.Enumerable> </xref:System.Linq.Enumerable.Where%2A> A expressão lambda no exemplo é usada para essa finalidade. Ele retorna `True` para cada processo que tem apenas um segmento, e aqueles selecionados na `filteredList`.  
  
 [!code-vb[VbVbalrLambdas n º&10;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_10.vb)]  
  
 O exemplo anterior é equivalente ao código a seguir, que é escrito em [!INCLUDE[vbteclinqext](../../../../csharp/getting-started/includes/vbteclinqext_md.md)] sintaxe:  
  
 [!code-vb[VbVbalrLambdas n º&11;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_11.vb)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Linq.Enumerable></xref:System.Linq.Enumerable>   
 [Expressões lambda](./lambda-expressions.md)   
 [Instrução Function](../../../../visual-basic/language-reference/statements/function-statement.md)   
 [Instrução sub](../../../../visual-basic/language-reference/statements/sub-statement.md)   
 [Delegados](../../../../visual-basic/programming-guide/language-features/delegates/index.md)   
 [Como: passar procedimentos para outro procedimento no Visual Basic](../../../../visual-basic/programming-guide/language-features/delegates/how-to-pass-procedures-to-another-procedure.md)   
 [Instrução delegate](../../../../visual-basic/language-reference/statements/delegate-statement.md)   
 [Introdução ao LINQ no Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
