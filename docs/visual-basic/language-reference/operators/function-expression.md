---
title: Expressão de função (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Function expression [Visual Basic]
- functions [Visual Basic], function expressions
- lambda expressions [Visual Basic], function expression
ms.assetid: e8a47a45-4b8a-4f45-a623-7653625dffbc
ms.openlocfilehash: cfdd17f6f4ee6c4ddb3fa73ab3ec9c5ce46a162f
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/14/2018
ms.locfileid: "45609906"
---
# <a name="function-expression-visual-basic"></a>Expressão de função (Visual Basic)
Declara os parâmetros e o código que define uma expressão lambda de função.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
Function ( [ parameterlist ] ) expression  
- or -  
Function ( [ parameterlist ] )  
  [ statements ]  
End Function  
```  
  
## <a name="parts"></a>Partes  
  
|Termo|Definição|  
|---|---|  
|`parameterlist`|Opcional. Uma lista de nomes de variáveis locais que representam os parâmetros deste procedimento. Os parênteses devem estar presentes mesmo quando a lista está vazia. Ver [lista de parâmetros](../../../visual-basic/language-reference/statements/parameter-list.md).|  
|`expression`|Necessário. Uma única expressão. O tipo da expressão é o tipo de retorno da função.|  
|`statements`|Necessário. Uma lista de instruções que retorna um valor usando o `Return` instrução. (Consulte [instrução Return](../../../visual-basic/language-reference/statements/return-statement.md).) O tipo do valor retornado é o tipo de retorno da função.|  
  
## <a name="remarks"></a>Comentários  
 Um *expressão lambda* é uma função sem um nome que calcula e retorna um valor. Você pode usar uma expressão lambda em qualquer lugar você pode usar um tipo de delegado, exceto como um argumento para `RemoveHandler`. Para obter mais informações sobre delegados e o uso de expressões lambda com delegados, consulte [declaração de delegado](../../../visual-basic/language-reference/statements/delegate-statement.md) e [conversão de delegado reduzida](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).  
  
## <a name="lambda-expression-syntax"></a>Sintaxe da expressão lambda  
 A sintaxe de uma expressão lambda lembra a de uma função padrão. As diferenças são da seguinte maneira:  
  
-   Uma expressão lambda não tem um nome.  
  
-   Expressões lambda não podem ter modificadores, como `Overloads` ou `Overrides`.  
  
-   Expressões lambda não usam um `As` cláusula para designar o tipo de retorno da função. Em vez disso, o tipo é inferido do valor que avalia o corpo de uma expressão lambda de linha única, ou o valor retornado de uma expressão lambda de várias linhas. Por exemplo, se o corpo de uma expressão lambda de linha única estiver `Where cust.City = "London"`, seu tipo de retorno é `Boolean`.  
  
-   O corpo de uma expressão lambda de linha única deve ser uma expressão, não uma instrução. O corpo pode consistir de uma chamada para um procedimento function, mas não uma chamada para um procedimento sub.  
  
-   Ou todos os parâmetros devem ter especificado devem ser deduzidos a tipos de dados ou todos.  
  
-   Parâmetros opcionais e Paramarray não são permitidos.  
  
-   Parâmetros genéricos não são permitidos.  
  
## <a name="example"></a>Exemplo  
 Os exemplos a seguir mostram duas maneiras de criar expressões lambda simples. O primeiro usa um `Dim` para fornecer um nome para a função. Para chamar a função, você envia um valor para o parâmetro.  
  
 [!code-vb[VbVbalrLambdas#1](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/function-expression_1.vb)]  
  
 [!code-vb[VbVbalrLambdas#2](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/function-expression_2.vb)]  
  
## <a name="example"></a>Exemplo  
 Como alternativa, você pode declarar e executar a função ao mesmo tempo.  
  
 [!code-vb[VbVbalrLambdas#3](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/function-expression_3.vb)]  
  
## <a name="example"></a>Exemplo  
 A seguir está um exemplo de uma expressão lambda que aumenta seu argumento e retorna o valor. O exemplo mostra os dois a sintaxe da expressão lambda de linha única e várias linhas para uma função. Para obter mais exemplos, consulte [expressões Lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).  
  
 [!code-vb[VbVbalrLambdas#14](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/function-expression_4.vb)]  
  
## <a name="example"></a>Exemplo  
 Expressões lambda são a base de muitos dos operadores de consulta em [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)]e pode ser usada explicitamente em consultas com base em método. O exemplo a seguir mostra um típico [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] consulta, seguido pela tradução da consulta em formato de método.  
  
```vb  
Dim londonCusts = From cust In db.Customers  
                       Where cust.City = "London"  
                       Select cust  
  
' This query is compiled to the following code:  
Dim londonCusts = db.Customers.  
                  Where(Function(cust) cust.City = "London").  
                  Select(Function(cust) cust)  
```  
  
 Para obter mais informações sobre métodos de consulta, consulte [consultas](../../../visual-basic/language-reference/queries/index.md). Para obter mais informações sobre operadores de consulta padrão, consulte [visão geral de operadores de consulta padrão](../../programming-guide/concepts/linq/standard-query-operators-overview.md).  
  
## <a name="see-also"></a>Consulte também  
 [Instrução Function](../../../visual-basic/language-reference/statements/function-statement.md)  
 [Expressões Lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)  
 [Operadores e Expressões](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)  
 [Instruções](../../../visual-basic/programming-guide/language-features/statements.md)  
 [Comparações de Valor](../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)  
 [Expressões Boolianas](../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md)  
 [Operador If](../../../visual-basic/language-reference/operators/if-operator.md)  
 [Conversão de Delegado Reduzida](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
