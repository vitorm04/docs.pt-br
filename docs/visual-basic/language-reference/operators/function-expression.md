---
title: "Função expressão (Visual Basic) | Documentos do Microsoft"
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
- Function expression [Visual Basic]
- functions [Visual Basic], function expressions
- lambda expressions [Visual Basic], function expression
ms.assetid: e8a47a45-4b8a-4f45-a623-7653625dffbc
caps.latest.revision: 18
author: dotnet-bot
ms.author: dotnetcontent
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 9b181b18a28a8b92a392fffdc10e08690d54f545
ms.contentlocale: pt-br
ms.lasthandoff: 03/13/2017

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
|`parameterlist`|Opcional. Uma lista de nomes de variáveis locais que representam os parâmetros deste procedimento. Os parênteses devem estar presentes mesmo quando a lista está vazia. Consulte [lista de parâmetros](../../../visual-basic/language-reference/statements/parameter-list.md).|  
|`expression`|Necessário. Uma única expressão. O tipo da expressão é o tipo de retorno da função.|  
|`statements`|Necessário. Uma lista de instruções que retorna um valor usando o `Return` instrução. (Consulte [instrução Return](../../../visual-basic/language-reference/statements/return-statement.md).) O tipo do valor retornado é o tipo de retorno da função.|  
  
## <a name="remarks"></a>Comentários  
 A *expressão lambda* é uma função sem um nome que calcula e retorna um valor. Você pode usar uma expressão lambda em qualquer lugar você pode usar um tipo delegado, exceto como um argumento para `RemoveHandler`. Para obter mais informações sobre o uso de expressões lambda com delegados e delegados, consulte [instrução delegado](../../../visual-basic/language-reference/statements/delegate-statement.md) e [conversão de delegado reduzida](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).  
  
## <a name="lambda-expression-syntax"></a>Sintaxe da expressão lambda  
 A sintaxe de uma expressão lambda lembra de uma função padrão. As diferenças são as seguintes:  
  
-   Uma expressão lambda não tem um nome.  
  
-   Expressões lambda não podem ter modificadores, como `Overloads` ou `Overrides`.  
  
-   Expressões lambda não usam uma `As` cláusula para designar o tipo de retorno da função. Em vez disso, o tipo é inferido do valor que avalia o corpo de uma expressão lambda de linha única ou o valor de retorno de uma expressão lambda de várias linhas. Por exemplo, se o corpo de uma expressão lambda de linha única é `Where cust.City = "London"`, seu tipo de retorno é `Boolean`.  
  
-   O corpo de uma expressão lambda de linha deve ser uma expressão, não uma instrução. O corpo pode consistir de uma chamada para um procedimento function, mas não é uma chamada para um procedimento de sub-rotina.  
  
-   Todos os parâmetros devem especificar todos ou tipos de dados devem ser inferidos.  
  
-   Parâmetros opcionais e Paramarray não são permitidos.  
  
-   Parâmetros genéricos não são permitidos.  
  
## <a name="example"></a>Exemplo  
 Os exemplos a seguir mostram duas maneiras de criar expressões lambda simples. O primeiro usa um `Dim` para fornecer um nome para a função. Para chamar a função, você deve enviar um valor para o parâmetro.  
  
 [!code-vb[VbVbalrLambdas n º&1;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/function-expression_1.vb)]  
  
 [!code-vb[VbVbalrLambdas n º&2;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/function-expression_2.vb)]  
  
## <a name="example"></a>Exemplo  
 Como alternativa, você pode declarar e executar a função ao mesmo tempo.  
  
 [!code-vb[VbVbalrLambdas n º&3;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/function-expression_3.vb)]  
  
## <a name="example"></a>Exemplo  
 A seguir está um exemplo de uma expressão lambda que aumenta seu argumento e retorna o valor. O exemplo mostra os dois a sintaxe da expressão lambda de linha e de várias linhas para uma função. Para obter mais exemplos, consulte [expressões Lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).  
  
 [!code-vb[VbVbalrLambdas&#14;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/function-expression_4.vb)]  
  
## <a name="example"></a>Exemplo  
 Expressões lambda são a base de muitos dos operadores de consulta em [!INCLUDE[vbteclinqext](../../../csharp/getting-started/includes/vbteclinqext_md.md)]e pode ser usado explicitamente em consultas com base em método. O exemplo a seguir mostra um típico [!INCLUDE[vbteclinq](../../../csharp/includes/vbteclinq_md.md)] consulta, seguido pela tradução da consulta em formato de método.  
  
```vb  
Dim londonCusts = From cust In db.Customers  
                       Where cust.City = "London"  
                       Select cust  
  
' This query is compiled to the following code:  
Dim londonCusts = db.Customers.  
                  Where(Function(cust) cust.City = "London").  
                  Select(Function(cust) cust)  
```  
  
 Para obter mais informações sobre métodos de consulta, consulte [consultas](../../../visual-basic/language-reference/queries/queries.md). Para obter mais informações sobre operadores de consulta padrão, consulte [visão geral de operadores de consulta padrão](http://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2).  
  
## <a name="see-also"></a>Consulte também  
 [Instrução Function](../../../visual-basic/language-reference/statements/function-statement.md)   
 [Expressões lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)   
 [Operadores e expressões](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)   
 [Instruções](../../../visual-basic/programming-guide/language-features/statements.md)   
 [Comparações de valor](../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)   
 [Expressões Boolianas](../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md)   
 [Se operador](../../../visual-basic/language-reference/operators/if-operator.md)   
 [Conversão de Delegado Reduzida](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)

