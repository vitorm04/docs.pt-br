---
title: "Subexpress&#227;o (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "expressões lambda [Visual Basic], subexpressão"
  - "Subexpressão [Visual Basic]"
  - "sub-rotinas [Visual Basic], subexpressões"
ms.assetid: 36b6bfd1-6539-4d8f-a5eb-6541a745ffde
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Subexpress&#227;o (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Declara os parâmetros e código que definem uma expressão lambda de sub\-rotina.  
  
## Sintaxe  
  
```  
Sub ( [ parameterlist ] ) statement  
- or -  
Sub ( [ parameterlist ] )  
  [ statements ]  
End Sub  
  
```  
  
## Partes  
  
|||  
|-|-|  
|Termo|Definição|  
|`parameterlist`|Opcional.  Uma lista de nomes de variáveis locais que representam os parâmetros do procedimento.  Os parênteses devem estar presentes, mesmo quando a lista está vazia.  Para obter mais informações, consulte [Lista de parâmetros](../../../visual-basic/language-reference/statements/parameter-list.md).|  
|`statement`|Obrigatório.  Uma única instrução.|  
|`statements`|Obrigatório.  Uma lista de instruções.|  
  
## Comentários  
 A  *expressão lambda* é uma sub\-rotina que não tem um nome e que executa uma ou mais instruções.  Você pode usar uma expressão lambda em qualquer lugar que você pode usar um tipo delegate, exceto como um argumento para `RemoveHandler`.  Para obter mais informações sobre o uso de expressões lambda com delegados e delegados, consulte [Instrução Delegate](../../../visual-basic/language-reference/statements/delegate-statement.md) e [Conversão de delegado reduzida](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).  
  
## Sintaxe de expressões lambda  
 A sintaxe de uma expressão lambda é semelhante a de uma sub\-rotina padrão.  As diferenças são as seguintes:  
  
-   Uma expressão lambda não tem um nome.  
  
-   Uma expressão lambda não pode ter um modificador, como `Overloads` ou `Overrides`.  
  
-   O corpo de uma expressão lambda de linha única deve ser uma instrução, não é uma expressão.  O corpo pode consistir de uma chamada para um procedimento sub, mas não uma chamada para um procedimento function.  
  
-   Em uma expressão lambda, todos os parâmetros devem especificar os tipos de dados ou de todos os parâmetros devem ser inferidos.  
  
-   Opcional e `ParamArray` parâmetros não são permitidos em expressões lambda.  
  
-   Parâmetros genéricos não são permitidos em expressões lambda.  
  
## Exemplo  
 Veja a seguir um exemplo de uma expressão lambda que grava um valor no console.  O exemplo mostra tanto a sintaxe da expressão lambda de linha e de várias linhas de uma sub\-rotina.  Para obter mais exemplos, consulte [Expressões lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).  
  
 [!code-vb[VbVbalrLambdas#15](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/sub-expression_1.vb)]  
  
## Consulte também  
 [Instrução Sub](../../../visual-basic/language-reference/statements/sub-statement.md)   
 [Expressões lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)   
 [Operadores e expressões](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)   
 [Instruções](../../../visual-basic/programming-guide/language-features/statements.md)   
 [Conversão de delegado reduzida](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)