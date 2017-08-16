---
title: "Função CType (Visual Basic) | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.CType
dev_langs:
- VB
helpviewer_keywords:
- expression conversion results
- explicit data type conversions
- CType function
- conversions, expression
ms.assetid: dd4b29e7-6fa1-428c-877e-69955420bb72
caps.latest.revision: 22
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: fc119d730ccd2ed9b33183d281ceeebefb1e7569
ms.lasthandoff: 03/13/2017

---
# <a name="ctype-function-visual-basic"></a>Função CType (Visual Basic)
Retorna o resultado da conversão explícita de uma expressão para um tipo de dados especificado, objeto, estrutura, classe ou interface.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
CType(expression, typename)  
```  
  
## <a name="parts"></a>Partes  
 `expression`  
 Qualquer expressão válida. Se o valor de `expression` está fora do intervalo permitido por `typename`, Visual Basic gera uma exceção.  
  
 `typename`  
 Qualquer expressão que seja legal em um `As` cláusula em uma `Dim` instrução, ou seja, o nome de qualquer tipo de dados, objeto, estrutura, classe ou interface.  
  
## <a name="remarks"></a>Comentários  
  
> [!TIP]
>  Você também pode usar as funções a seguir para executar uma conversão de tipo:  
>   
>  -   Funções de conversão de tipo como `CByte`, `CDbl`, e `CInt` que executar uma conversão para um tipo de dados específico. Para obter mais informações, consulte [funções de conversão de tipo](../../../visual-basic/language-reference/functions/type-conversion-functions.md).  
> -   [Operador DirectCast](../../../visual-basic/language-reference/operators/directcast-operator.md) ou [operador TryCast](../../../visual-basic/language-reference/operators/trycast-operator.md). Esses operadores exigem que um tipo de herdar de ou implementar o outro tipo. Podem fornecer desempenho um pouco melhor do que `CType` durante a conversão de e para o `Object` tipo de dados.  
  
 `CType`é embutido compilado, o que significa que o código de conversão faz parte do código que avalia a expressão. Em alguns casos, o código é executado mais rápido porque não há procedimentos são chamados para executar a conversão.  
  
 Se nenhuma conversão é definida de `expression` para `typename` (por exemplo, de `Integer` para `Date`), do Visual Basic exibe uma mensagem de erro de tempo de compilação.  
  
 Se uma conversão falhar em tempo de execução, a exceção apropriada é gerada. Se uma conversão de redução falhar, um <xref:System.OverflowException>é o resultado mais comum.</xref:System.OverflowException> Se a conversão for indefinida, uma <xref:System.InvalidCastException>em gerada.</xref:System.InvalidCastException> Por exemplo, isso pode acontecer se `expression` é do tipo `Object` e seu tipo de tempo de execução não tem nenhuma conversão em `typename`.  
  
 Se o tipo de dados `expression` ou `typename` é uma classe ou estrutura que você definiu, você pode definir `CType` na classe ou estrutura como um operador de conversão. Isso torna `CType` atuar como um *sobrecarregado operador*. Se você fizer isso, você pode controlar o comportamento de conversões para e de sua classe ou estrutura, incluindo as exceções que podem ser geradas.  
  
## <a name="overloading"></a>Sobrecarga  
 O `CType` também pode ser sobrecarregado operador em uma classe ou estrutura definida fora de seu código. Se o código a seguir converte para ou de uma classe ou estrutura, certifique-se de entender o comportamento do seu `CType` operador. Para obter mais informações, consulte [procedimentos de operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="converting-dynamic-objects"></a>Convertendo objetos dinâmicos  
 Conversões de tipo de objetos dinâmicos são executadas por conversões dinâmicas definido pelo usuário que usam o <xref:System.Dynamic.DynamicObject.TryConvert%2A>ou <xref:System.Dynamic.DynamicMetaObject.BindConvert%2A>métodos.</xref:System.Dynamic.DynamicMetaObject.BindConvert%2A> </xref:System.Dynamic.DynamicObject.TryConvert%2A> Se você estiver trabalhando com objetos dinâmicos, use o <xref:Microsoft.VisualBasic.Conversion.CTypeDynamic%2A>método para converter o objeto dinâmico.</xref:Microsoft.VisualBasic.Conversion.CTypeDynamic%2A>  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa o `CType` função para converter uma expressão para o `Single` tipo de dados.  
  
 [!code-vb[VbVbalrFunctions&#24;](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/ctype-function_1.vb)]  
  
 Para obter exemplos adicionais, consulte [conversões explícitas e implícitas](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.OverflowException></xref:System.OverflowException>   
 <xref:System.InvalidCastException></xref:System.InvalidCastException>   
 [Funções de conversão de tipo](../../../visual-basic/language-reference/functions/type-conversion-functions.md)   
 [Funções de conversão](../../../visual-basic/language-reference/functions/conversion-functions.md)   
 [Instrução Operator](../../../visual-basic/language-reference/statements/operator-statement.md)   
 [Como: definir um operador de conversão](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)   
 [Conversão de tipo no .NET Framework](http://msdn.microsoft.com/library/ba36154f-064c-47d3-9f05-72f93a7ca96d)
