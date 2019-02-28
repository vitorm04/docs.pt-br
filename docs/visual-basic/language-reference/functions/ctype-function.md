---
title: Função CType (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.CType
helpviewer_keywords:
- expression conversion results
- explicit data type conversions [Visual Basic]
- CType function
- conversions [Visual Basic], expression
ms.assetid: dd4b29e7-6fa1-428c-877e-69955420bb72
ms.openlocfilehash: 8f60edb2b5e2dba15526169ef10bc05c1f50a7f1
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56970006"
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
 Qualquer expressão que é legal em um `As` cláusula em uma `Dim` instrução, ou seja, o nome de qualquer tipo de dados, objeto, estrutura, classe ou interface.  
  
## <a name="remarks"></a>Comentários  
  
> [!TIP]
>  Você também pode usar as funções a seguir para executar uma conversão de tipo:  
>   
>  -   Funções de conversão de tipo, como `CByte`, `CDbl`, e `CInt` que executa uma conversão para um tipo de dados específico. Para obter mais informações, consulte [funções de conversão de tipo](../../../visual-basic/language-reference/functions/type-conversion-functions.md).  
> -   [Operador DirectCast](../../../visual-basic/language-reference/operators/directcast-operator.md) ou [operador TryCast](../../../visual-basic/language-reference/operators/trycast-operator.md). Esses operadores exigem que um tipo herda de ou implementa o outro tipo. Eles podem fornecer desempenho um pouco melhor do que `CType` durante a conversão de e para o `Object` tipo de dados.  
  
 `CType` é compilado embutido, o que significa que o código de conversão é parte do código que avalia a expressão. Em alguns casos, o código é executado mais rapidamente porque nenhum procedimento é chamado para executar a conversão.  
  
 Se nenhuma conversão é definida de `expression` à `typename` (por exemplo, do `Integer` para `Date`), Visual Basic exibe uma mensagem de erro de tempo de compilação.  
  
 Se uma conversão falhar em tempo de execução, a exceção apropriada é lançada. Se uma conversão de redução falhar, um <xref:System.OverflowException> é o resultado mais comum. Se a conversão é indefinida, um <xref:System.InvalidCastException> gerada. Por exemplo, isso pode acontecer se `expression` é do tipo `Object` e seu tipo de tempo de execução não tiver nenhuma conversão para `typename`.  
  
 Se o tipo de dados `expression` ou `typename` é uma classe ou estrutura que você definiu, você pode definir `CType` nessa classe ou estrutura como um operador de conversão. Isso torna `CType` atuar como um *operador sobrecarregado*. Se você fizer isso, você pode controlar o comportamento de conversões para e de sua classe ou estrutura, incluindo as exceções que podem ser lançadas.  
  
## <a name="overloading"></a>Sobrecarga  
 O `CType` operador também pode ser sobrecarregado em uma classe ou estrutura definida fora de seu código. Se seu código converte para ou de uma classe ou estrutura, certifique-se de entender o comportamento do seu `CType` operador. Para obter mais informações, consulte [procedimentos de operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="converting-dynamic-objects"></a>Convertendo objetos dinâmicos  
 Conversões de tipos de objetos dinâmicos são executadas pela conversões dinâmicas definidas pelo usuário que usam o <xref:System.Dynamic.DynamicObject.TryConvert%2A> ou <xref:System.Dynamic.DynamicMetaObject.BindConvert%2A> métodos. Se você estiver trabalhando com objetos dinâmicos, use o <xref:Microsoft.VisualBasic.Conversion.CTypeDynamic%2A> método para converter o objeto dinâmico.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa o `CType` função para converter uma expressão para o `Single` tipo de dados.  
  
 [!code-vb[VbVbalrFunctions#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#24)]  
  
 Para obter exemplos adicionais, consulte [conversões implícitas e explícitas](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md).  
  
## <a name="see-also"></a>Consulte também
- <xref:System.OverflowException>
- <xref:System.InvalidCastException>
- [Funções de Conversão do Tipo](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Funções de Conversão](../../../visual-basic/language-reference/functions/conversion-functions.md)
- [Instrução Operator](../../../visual-basic/language-reference/statements/operator-statement.md)
- [Como: Definir um operador de conversão](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
- [Conversão de tipos no .NET Framework](../../../standard/base-types/type-conversion.md)
