---
title: "Como criar uma express&#227;o lambda (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "expressões [Visual Basic], lambda"
  - "expressões lambda [Visual Basic]"
ms.assetid: 3279bd5c-80f7-410a-a7ba-f7085ed36aa5
caps.latest.revision: 27
caps.handback.revision: 27
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como criar uma express&#227;o lambda (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

A  *expressão lambda* é uma função ou sub\-rotina que não tem um nome.  Uma expressão lambda pode ser usada sempre que um tipo delegate é válido.  
  
### Para criar uma função de expressão lambda de linha única  
  
1.  Em qualquer situação onde um tipo delegado pode ser usado, digite a palavra\-chave `Function`, como no exemplo a seguir:  
  
     `Dim add1 =`   `Function`  
  
2.  Entre parênteses, diretamente após `Function`, digite os parâmetros da função.  Observe que você não especifica um nome após `Function`.  
  
     `Dim add1 = Function`   `(num As Integer)`  
  
3.  Após a lista de parâmetros, digite uma única expressão como corpo da função.  O valor que a expressão processará é o valor retornado pela função.  Você não usa uma cláusula `As` para especificar o tipo de retorno.  
  
     [!code-vb[VbVbalrLambdas#1](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_1.vb)]  
  
     Você chama a expressão lambda passando um argumento Integer.  
  
     [!code-vb[VbVbalrLambdas#2](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_2.vb)]  
  
4.  Como alternativa, o mesmo resultado é conseguido no exemplo a seguir:  
  
     [!code-vb[VbVbalrLambdas#3](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_3.vb)]  
  
### Para criar uma sub\-rotina de expressão lambda de linha única  
  
1.  Em qualquer situação onde um tipo delegado pode ser usado, digite a palavra\-chave `Sub`, conforme mostrado no exemplo a seguir.  
  
     `Dim add1 =`   `Sub`  
  
2.  Entre parênteses, logo após `Sub`, digite os parâmetros da sub\-rotina.  Observe que você não especifica um nome após `Sub`.  
  
     `Dim add1 = Sub`   `(msg As String)`  
  
3.  Após a lista de parâmetros, digite uma única instrução, como o corpo da sub\-rotina.  
  
     [!code-vb[VbVbalrLambdas#17](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_4.vb)]  
  
     Chamar a expressão lambda, passando um argumento de seqüência de caracteres.  
  
     [!code-vb[VbVbalrLambdas#18](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_5.vb)]  
  
### Para criar uma função de expressão lambda multilinha  
  
1.  Em qualquer situação onde um tipo delegado pode ser usado, digite a palavra\-chave `Function`, conforme mostrado no exemplo a seguir.  
  
     `Dim add1 =`   `Function`  
  
2.  Entre parênteses, diretamente após `Function`, digite os parâmetros da função.  Observe que você não especifica um nome após `Function`.  
  
     `Dim add1 = Function`   `(index As Integer)`  
  
3.  Pressione ENTER.  O `End Function` declaração é adicionada automaticamente.  
  
4.  Dentro do corpo da função, adicione o seguinte código para criar uma expressão e retornar o valor.  Você não usa uma cláusula `As` para especificar o tipo de retorno.  
  
     [!code-vb[VbVbalrLambdas#19](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_6.vb)]  
  
     Você chama a expressão lambda passando um argumento Integer.  
  
     [!code-vb[VbVbalrLambdas#20](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_7.vb)]  
  
### Para criar uma sub\-rotina de expressão lambda multilinha  
  
1.  Em qualquer situação onde um tipo delegado pode ser usado, digite a palavra\-chave `Sub`, conforme mostrado no exemplo a seguir:  
  
     `Dim add1 =`   `Sub`  
  
2.  Entre parênteses, logo após `Sub`, digite os parâmetros da sub\-rotina.  Observe que você não especifica um nome após `Sub`.  
  
     `Dim add1 = Sub`  `(msg As String)`  
  
3.  Pressione ENTER.  O `End Sub` declaração é adicionada automaticamente.  
  
4.  Dentro do corpo da função, adicione o seguinte código para executar quando a sub\-rotina é invocada.  
  
     [!code-vb[VbVbalrLambdas#21](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_8.vb)]  
  
     Chamar a expressão lambda, passando um argumento de seqüência de caracteres.  
  
     [!code-vb[VbVbalrLambdas#22](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_9.vb)]  
  
## Exemplo  
 Um uso comum de expressões lambda é para definir uma função que pode ser passada como argumento para um parâmetro cujo tipo é `Delegate`.  No exemplo a seguir, o método <xref:System.Diagnostics.Process.GetProcesses%2A> retorna uma matriz dos processos em execução no computador local.  O método <xref:System.Linq.Enumerable.Where%2A> da classe <xref:System.Linq.Enumerable> requer que um delegado `Boolean` como seu argumento.  A expressão lambda no exemplo é usada para essa finalidade.  Ela retorna `True` para cada processo que tem apenas um segmento, e aqueles selecionados na `filteredList`.  
  
 [!code-vb[VbVbalrLambdas#10](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_10.vb)]  
  
 O exemplo anterior é equivalente ao código a seguir, que está escrito na sintaxe [!INCLUDE[vbteclinqext](../../../../csharp/getting-started/includes/vbteclinqext_md.md)]:  
  
 [!code-vb[VbVbalrLambdas#11](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_11.vb)]  
  
## Consulte também  
 <xref:System.Linq.Enumerable>   
 [Expressões lambda](../../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)   
 [Instrução Function](../../../../visual-basic/language-reference/statements/function-statement.md)   
 [Instrução Sub](../../../../visual-basic/language-reference/statements/sub-statement.md)   
 [Delegados](../../../../visual-basic/programming-guide/language-features/delegates/delegates.md)   
 [Como passar procedimentos para outro procedimento no Visual Basic](../../../../visual-basic/programming-guide/language-features/delegates/how-to-pass-procedures-to-another-procedure.md)   
 [Instrução Delegate](../../../../visual-basic/language-reference/statements/delegate-statement.md)   
 [Introdução a LINQ no Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)