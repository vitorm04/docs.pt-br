---
title: "Express&#227;o de fun&#231;&#227;o (Visual Basic) | Microsoft Docs"
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
  - "Expressão de função [Visual Basic]"
  - "funções [Visual Basic], expressões de função"
  - "expressões lambda [Visual Basic], expressão de função"
ms.assetid: e8a47a45-4b8a-4f45-a623-7653625dffbc
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Express&#227;o de fun&#231;&#227;o (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Declara os parâmetros e código que definem uma expressão lambda de função.  
  
## Sintaxe  
  
```  
Function ( [ parameterlist ] ) expression  
- or -  
Function ( [ parameterlist ] )  
  [ statements ]  
End Function  
  
```  
  
## Partes  
  
|||  
|-|-|  
|Termo|Definição|  
|`parameterlist`|Opcional.  Uma lista de nomes de variáveis locais que representam os parâmetros deste procedimento.  Os parênteses devem estar presentes, mesmo quando a lista está vazia.  Consulte [Lista de parâmetros](../../../visual-basic/language-reference/statements/parameter-list.md).|  
|`expression`|Obrigatório.  Uma única expressão.  O tipo da expressão é o tipo de retorno da função.|  
|`statements`|Obrigatório.  Uma lista de declarações que retorna um valor usando o `Return` instrução.  \(See [Instrução Return](../../../visual-basic/language-reference/statements/return-statement.md).\) O tipo do valor retornado é o tipo de retorno da função.|  
  
## Comentários  
 A  *expressão lambda* é uma função sem um nome que calcula e retorna um valor.  Você pode usar uma expressão lambda em qualquer lugar você pode usar um tipo delegate, exceto como um argumento para `RemoveHandler`.  Para obter mais informações sobre o uso de expressões lambda com delegados e delegados, consulte [Instrução Delegate](../../../visual-basic/language-reference/statements/delegate-statement.md) e [Conversão de delegado reduzida](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).  
  
## Sintaxe de expressões lambda  
 A sintaxe de uma expressão lambda lembra a de uma função padrão.  As diferenças são as seguintes:  
  
-   Uma expressão lambda não tem um nome.  
  
-   Expressões lambda não podem ter modificadores, como `Overloads` ou `Overrides`.  
  
-   Expressões lambda não usam uma cláusula `As` para designar o tipo de retorno da função.  Em vez disso, o tipo é inferido do que o valor que avalia o corpo de uma expressão lambda de linha única ou o valor de retorno de uma expressão lambda de várias linhas.  Por exemplo, se o corpo de uma expressão lambda de linha única é `Where cust.City = "London"`, seu tipo de retorno é `Boolean`.  
  
-   O corpo de uma expressão lambda de linha única deve ser uma expressão, não uma instrução.  O corpo pode consistir de uma chamada para um procedimento de função, mas não uma chamada para um procedimento sub.  
  
-   Ou todos os parâmetros devem ter tipos de dados especificados ou todos devem ser inferidos.  
  
-   Parâmetros opcionais e ParamArray não são permitidos.  
  
-   Parâmetros genéricos não são permitidos.  
  
## Exemplo  
 Os exemplos a seguir mostram duas maneiras para criar expressões lambda simples.  O primeiro usa um `Dim` para fornecer um nome para a função.  Para chamar a função, você envia um valor para o parâmetro.  
  
 [!code-vb[VbVbalrLambdas#1](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/function-expression_1.vb)]  
  
 [!code-vb[VbVbalrLambdas#2](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/function-expression_2.vb)]  
  
## Exemplo  
 Como alternativa, você pode declarar e executar a função ao mesmo tempo.  
  
 [!code-vb[VbVbalrLambdas#3](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/function-expression_3.vb)]  
  
## Exemplo  
 Veja a seguir um exemplo de uma expressão lambda que incrementa seu argumento e retorna o valor.  O exemplo mostra tanto a sintaxe da expressão lambda de linha e de várias linhas para uma função.  Para obter mais exemplos, consulte [Expressões lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).  
  
 [!code-vb[VbVbalrLambdas#14](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/function-expression_4.vb)]  
  
## Exemplo  
 As expressões lambda dão suporte à muitos dos operadores de consulta em [!INCLUDE[vbteclinqext](../../../csharp/getting-started/includes/vbteclinqext_md.md)]e pode ser usado explicitamente em consultas baseadas em método.  O exemplo a seguir mostra uma típica [!INCLUDE[vbteclinq](../../../csharp/includes/vbteclinq_md.md)] a consulta, seguida pela tradução da consulta em formato de método.  
  
```vb#  
Dim londonCusts = From cust In db.Customers  
                       Where cust.City = "London"  
                       Select cust  
  
' This query is compiled to the following code:  
Dim londonCusts = db.Customers.  
                  Where(Function(cust) cust.City = "London").  
                  Select(Function(cust) cust)  
```  
  
 Para obter mais informações sobre métodos de consulta, consulte [Consultas](../../../visual-basic/language-reference/queries/queries.md).  Para obter mais informações sobre operadores de consulta padrão, consulte [Visão geral de operadores de consulta padrão](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md).  
  
## Consulte também  
 [Instrução Function](../../../visual-basic/language-reference/statements/function-statement.md)   
 [Expressões lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)   
 [Operadores e expressões](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)   
 [Instruções](../../../visual-basic/programming-guide/language-features/statements.md)   
 [Comparações de valor](../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)   
 [Expressões boolianas](../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md)   
 [Operador If](../../../visual-basic/language-reference/operators/if-operator.md)   
 [Conversão de delegado reduzida](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)