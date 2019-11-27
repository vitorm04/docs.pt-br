---
title: Operador TryCast
ms.date: 07/20/2015
f1_keywords:
- vb.trycast
- trycast
helpviewer_keywords:
- TryCast keyword [Visual Basic]
ms.assetid: d1ef5d47-fef4-491e-b014-1d910628f65c
ms.openlocfilehash: 53306575cfc385039be3939fd87cf993b4509af4
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348207"
---
# <a name="trycast-operator-visual-basic"></a>Operador TryCast (Visual Basic)
Apresenta uma operação de conversão de tipo que não gera uma exceção.  
  
## <a name="remarks"></a>Comentários  
 Se uma tentativa de conversão falhar, `CType` e `DirectCast` lançar um erro <xref:System.InvalidCastException>. Isso pode afetar negativamente o desempenho do seu aplicativo. `TryCast` não retorna [nada](../../../visual-basic/language-reference/nothing.md), de modo que, em vez de ter que lidar com uma possível exceção, você só precisa testar o resultado retornado em relação a `Nothing`.  
  
 Você usa a palavra-chave `TryCast` da mesma maneira que usa a [função CType](../../../visual-basic/language-reference/functions/ctype-function.md) e a palavra-chave [DirectCast Operator](../../../visual-basic/language-reference/operators/directcast-operator.md) . Você fornece uma expressão como o primeiro argumento e um tipo para convertê-lo como o segundo argumento. `TryCast` funciona apenas em tipos de referência, como classes e interfaces. Ele requer uma relação de herança ou de implementação entre os dois tipos. Isso significa que um tipo deve herdar ou implementar o outro.  
  
## <a name="errors-and-failures"></a>Erros e falhas  
 `TryCast` gerará um erro do compilador se detectar que nenhuma relação de herança ou implementação existe. Mas a falta de um erro do compilador não garante uma conversão bem-sucedida. Se a conversão desejada for restrita, ela poderá falhar em tempo de execução. Se isso acontecer, `TryCast` não retornará [nada](../../../visual-basic/language-reference/nothing.md).  
  
## <a name="conversion-keywords"></a>Palavras-chave de conversão  
 Uma comparação das palavras-chave de conversão de tipo é a seguinte:  
  
|Palavra-chave|Tipos de dados|Relação de argumento|Falha de tempo de execução|  
|---|---|---|---|  
|[Função CType](../../../visual-basic/language-reference/functions/ctype-function.md)|Quaisquer tipos de dados|A conversão de alargamento ou de estreitamento deve ser definida entre os dois tipos de dados|Gera <xref:System.InvalidCastException>|  
|[Operador DirectCast](../../../visual-basic/language-reference/operators/directcast-operator.md)|Quaisquer tipos de dados|Um tipo deve herdar ou implementar o outro tipo|Gera <xref:System.InvalidCastException>|  
|`TryCast`|Somente tipos de referência|Um tipo deve herdar ou implementar o outro tipo|Não retorna [nada](../../../visual-basic/language-reference/nothing.md)|  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como usar `TryCast`.  
  
 [!code-vb[VbVbalrKeywords#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#6)]  
  
## <a name="see-also"></a>Consulte também

- [Conversões de Widening e Narrowing](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [Conversões Implícitas e Explícitas](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
