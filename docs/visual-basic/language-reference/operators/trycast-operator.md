---
title: Operador TryCast (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.trycast
- trycast
helpviewer_keywords:
- TryCast keyword [Visual Basic]
ms.assetid: d1ef5d47-fef4-491e-b014-1d910628f65c
ms.openlocfilehash: 1bd92428927927a84c1de8f88d176a8f0aba4af2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54524930"
---
# <a name="trycast-operator-visual-basic"></a>Operador TryCast (Visual Basic)
Apresenta uma operação de conversão de tipo que não gera uma exceção.  
  
## <a name="remarks"></a>Comentários  
 Se uma tentativa de conversão falhar, `CType` e `DirectCast` ambos lançar um <xref:System.InvalidCastException> erro. Isso pode afetar negativamente o desempenho do seu aplicativo. `TryCast` Retorna [nada](../../../visual-basic/language-reference/nothing.md), de modo que, em vez de ter que lidar com uma possível exceção, você só precisa testar o resultado retornado contra `Nothing`.  
  
 Você usa o `TryCast` palavra-chave da mesma maneira que você usar o [função CType](../../../visual-basic/language-reference/functions/ctype-function.md) e o [operador DirectCast](../../../visual-basic/language-reference/operators/directcast-operator.md) palavra-chave. Você fornece uma expressão como o primeiro argumento e um tipo para convertê-lo para como o segundo argumento. `TryCast` funciona somente em tipos de referência, como classes e interfaces. Ele requer uma relação de herança ou implementação entre os dois tipos. Isso significa que um tipo deve herdar ou implementar o outro.  
  
## <a name="errors-and-failures"></a>Erros e falhas  
 `TryCast` gera um erro do compilador se detectar que não existir nenhuma relação de herança ou implementação. Mas a falta de um erro do compilador não garante uma conversão bem-sucedida. Se a conversão desejada é de restrição, ele poderá falhar em tempo de execução. Se isso acontecer, `TryCast` retorna [nada](../../../visual-basic/language-reference/nothing.md).  
  
## <a name="conversion-keywords"></a>Palavras-chave de conversão  
 Uma comparação entre as palavras-chave de conversão de tipo é da seguinte maneira.  
  
|Palavra-chave|Tipos de dados|Relacionamento de argumento|Falha de tempo de execução|  
|---|---|---|---|  
|[Função CType](../../../visual-basic/language-reference/functions/ctype-function.md)|Quaisquer tipos de dados|Ampliação ou conversão de estreitamento deve ser definido entre os dois tipos de dados|Gera <xref:System.InvalidCastException>|  
|[Operador DirectCast](../../../visual-basic/language-reference/operators/directcast-operator.md)|Quaisquer tipos de dados|Um tipo deve herdar ou implementar o outro tipo|Gera <xref:System.InvalidCastException>|  
|`TryCast`|Somente tipos de referência|Um tipo deve herdar ou implementar o outro tipo|Retorna [nada](../../../visual-basic/language-reference/nothing.md)|  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como usar `TryCast`.  
  
 [!code-vb[VbVbalrKeywords#6](../../../visual-basic/language-reference/codesnippet/VisualBasic/trycast-operator_1.vb)]  
  
## <a name="see-also"></a>Consulte também
- [Conversões de Widening e Narrowing](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [Conversões Implícitas e Explícitas](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
