---
title: "Sub expressão (Visual Basic) | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- lambda expressions [Visual Basic], sub expression
- Sub Expression [Visual Basic]
- subroutines [Visual Basic], sub expressions
ms.assetid: 36b6bfd1-6539-4d8f-a5eb-6541a745ffde
caps.latest.revision: 6
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
ms.openlocfilehash: 57202c0781ee62d1ac8855f4e20277feb7edef72
ms.lasthandoff: 03/13/2017

---
# <a name="sub-expression-visual-basic"></a>Subexpressão (Visual Basic)
Declara os parâmetros e o código que define uma expressão lambda de sub-rotina.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
Sub ( [ parameterlist ] ) statement  
- or -  
Sub ( [ parameterlist ] )  
  [ statements ]  
End Sub  
  
```  
  
## <a name="parts"></a>Partes  
  
|Termo|Definição|  
|---|---|  
|`parameterlist`|Opcional. Uma lista de nomes de variáveis locais que representam os parâmetros do procedimento. Os parênteses devem estar presentes mesmo quando a lista está vazia. Para obter mais informações, consulte [lista de parâmetros](../../../visual-basic/language-reference/statements/parameter-list.md).|  
|`statement`|Necessário. Uma única instrução.|  
|`statements`|Necessário. Uma lista de instruções.|  
  
## <a name="remarks"></a>Comentários  
 A *expressão lambda* é uma sub-rotina que não tem um nome e que executa uma ou mais instruções. Você pode usar uma expressão lambda em qualquer lugar que você pode usar um tipo delegado, exceto como um argumento para `RemoveHandler`. Para obter mais informações sobre o uso de expressões lambda com delegados e delegados, consulte [instrução delegado](../../../visual-basic/language-reference/statements/delegate-statement.md) e [conversão de delegado reduzida](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).  
  
## <a name="lambda-expression-syntax"></a>Sintaxe da expressão lambda  
 A sintaxe de uma expressão lambda lembra a de uma sub-rotina padrão. As diferenças são as seguintes:  
  
-   Uma expressão lambda não tem um nome.  
  
-   Uma expressão lambda não pode ter um modificador, como `Overloads` ou `Overrides`.  
  
-   O corpo de uma expressão lambda de linha deve ser uma instrução, não é uma expressão. O corpo pode consistir de uma chamada para um procedimento sub, mas não uma chamada para um procedimento function.  
  
-   Em uma expressão lambda, ou todos os parâmetros devem especificar todos os parâmetros ou tipos de dados devem ser inferidos.  
  
-   Opcional e `ParamArray` parâmetros não são permitidos em expressões lambda.  
  
-   Parâmetros genéricos não são permitidos em expressões lambda.  
  
## <a name="example"></a>Exemplo  
 A seguir está um exemplo de uma expressão lambda que grava um valor para o console. O exemplo mostra os dois a sintaxe da expressão lambda de linha e de várias linhas de uma sub-rotina. Para obter mais exemplos, consulte [expressões Lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).  
  
 [!code-vb[VbVbalrLambdas&#15;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/sub-expression_1.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [Instrução sub](../../../visual-basic/language-reference/statements/sub-statement.md)   
 [Expressões lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)   
 [Operadores e expressões](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)   
 [Instruções](../../../visual-basic/programming-guide/language-features/statements.md)   
 [Conversão de Delegado Reduzida](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
