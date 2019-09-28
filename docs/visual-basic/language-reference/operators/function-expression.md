---
title: Expressão de função (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Function expression [Visual Basic]
- functions [Visual Basic], function expressions
- lambda expressions [Visual Basic], function expression
ms.assetid: e8a47a45-4b8a-4f45-a623-7653625dffbc
ms.openlocfilehash: 0ab4a77395b478df06f34240212438f3e6e18f6e
ms.sourcegitcommit: 35da8fb45b4cca4e59cc99a5c56262c356977159
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/28/2019
ms.locfileid: "71592201"
---
# <a name="function-expression-visual-basic"></a>Expressão de função (Visual Basic)
Declara os parâmetros e o código que definem uma expressão lambda de função.  
  
## <a name="syntax"></a>Sintaxe  
  
```vb  
Function ( [ parameterlist ] ) expression  
- or -  
Function ( [ parameterlist ] )  
  [ statements ]  
End Function  
```  
  
## <a name="parts"></a>Partes  
  
|Termo|Definição|  
|---|---|  
|`parameterlist`|Opcional. Uma lista de nomes de variáveis locais que representam os parâmetros deste procedimento. Os parênteses devem estar presentes mesmo quando a lista estiver vazia. Consulte a [lista de parâmetros](../../../visual-basic/language-reference/statements/parameter-list.md).|  
|`expression`|Necessário. Uma única expressão. O tipo da expressão é o tipo de retorno da função.|  
|`statements`|Necessário. Uma lista de instruções que retorna um valor usando a instrução `Return`. (Consulte a [instrução return](../../../visual-basic/language-reference/statements/return-statement.md).) O tipo do valor retornado é o tipo de retorno da função.|  
  
## <a name="remarks"></a>Comentários  
 Uma *expressão lambda* é uma função sem um nome que calcula e retorna um valor. Você pode usar uma expressão lambda em qualquer lugar em que possa usar um tipo delegado, exceto como um argumento para `RemoveHandler`. Para obter mais informações sobre delegados e o uso de expressões lambda com delegados, consulte [instrução delegate](../../../visual-basic/language-reference/statements/delegate-statement.md) e [conversão de delegado reduzida](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).  
  
## <a name="lambda-expression-syntax"></a>Sintaxe da expressão lambda  
 A sintaxe de uma expressão lambda é semelhante à de uma função padrão. As diferenças são as seguintes:  
  
- Uma expressão lambda não tem um nome.  
  
- Expressões lambda não podem ter modificadores, como `Overloads` ou `Overrides`.  
  
- As expressões lambda não usam uma cláusula `As` para designar o tipo de retorno da função. Em vez disso, o tipo é inferido do valor que o corpo de uma expressão lambda de linha única avalia ou o valor de retorno de uma expressão lambda de várias linhas. Por exemplo, se o corpo de uma expressão lambda de linha única for `Where cust.City = "London"`, seu tipo de retorno será `Boolean`.  
  
- O corpo de uma expressão lambda de linha única deve ser uma expressão, não uma instrução. O corpo pode consistir em uma chamada para um procedimento Function, mas não uma chamada para um procedimento Sub.  
  
- Todos os parâmetros devem ter tipos de dados especificados ou todos devem ser inferidos.  
  
- Parâmetros optional e ParamArray não são permitidos.  
  
- Parâmetros genéricos não são permitidos.  
  
## <a name="example"></a>Exemplo  
 Os exemplos a seguir mostram duas maneiras de criar expressões lambda simples. O primeiro usa um `Dim` para fornecer um nome para a função. Para chamar a função, você envia em um valor para o parâmetro.  
  
 [!code-vb[VbVbalrLambdas#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#1)]  
  
 [!code-vb[VbVbalrLambdas#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#2)]  
  
## <a name="example"></a>Exemplo  
 Como alternativa, você pode declarar e executar a função ao mesmo tempo.  
  
 [!code-vb[VbVbalrLambdas#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#3)]  
  
## <a name="example"></a>Exemplo  
 Veja a seguir um exemplo de uma expressão lambda que incrementa seu argumento e retorna o valor. O exemplo mostra a sintaxe da expressão lambda de linha única e de várias linhas para uma função. Para obter mais exemplos, consulte [expressões lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).  
  
 [!code-vb[VbVbalrLambdas#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#14)]  
  
## <a name="example"></a>Exemplo  
 As expressões lambda baseiam-se em muitos dos operadores de consulta no [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] e podem ser usadas explicitamente em consultas baseadas em método. O exemplo a seguir mostra uma consulta [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] típica, seguida pela conversão da consulta em formato de método.  
  
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

- [Instrução Function](../../../visual-basic/language-reference/statements/function-statement.md)
- [Expressões Lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
- [Operadores e Expressões](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
- [Instruções](../../../visual-basic/programming-guide/language-features/statements.md)
- [Comparações de Valor](../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)
- [Expressões Boolianas](../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md)
- [Operador If](../../../visual-basic/language-reference/operators/if-operator.md)
- [Conversão de Delegado Reduzida](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
