---
title: Operador DirectCast (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.directCast
- directCast
helpviewer_keywords:
- DirectCast keyword [Visual Basic]
ms.assetid: 63e5a1d0-4d9e-4732-bf8f-e90c0c8784b8
ms.openlocfilehash: 628ce4f06b91d0f514f71dea3aad8ea0fee6dccf
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58821498"
---
# <a name="directcast-operator-visual-basic"></a>Operador DirectCast (Visual Basic)
Apresenta uma operação de conversão de tipo com base em herança ou implementação.  
  
## <a name="remarks"></a>Comentários  
 `DirectCast` não usa rotinas auxiliares de tempo de execução para a conversão, para que possa fornecer um pouco melhor desempenho do que o Visual Basic `CType` ao converter para e do tipo de dados `Object`.  
  
 Você usa o `DirectCast` palavra-chave semelhante à forma como você usar o [função CType](../../../visual-basic/language-reference/functions/ctype-function.md) e o [operador TryCast](../../../visual-basic/language-reference/operators/trycast-operator.md) palavra-chave. Você fornece uma expressão como o primeiro argumento e um tipo para convertê-lo para como o segundo argumento. `DirectCast` requer uma relação de herança ou implementação entre os tipos de dados dos dois argumentos. Isso significa que um tipo deve herdar ou implementar o outro.  
  
## <a name="errors-and-failures"></a>Erros e falhas  
 `DirectCast` gera um erro do compilador se detectar que não existir nenhuma relação de herança ou implementação. Mas a falta de um erro do compilador não garante uma conversão bem-sucedida. Se a conversão desejada é de restrição, ele poderá falhar em tempo de execução. Se isso acontecer, o tempo de execução gera uma <xref:System.InvalidCastException> erro.  
  
## <a name="conversion-keywords"></a>Palavras-chave de conversão  
 Uma comparação entre as palavras-chave de conversão de tipo é da seguinte maneira.  
  
|Palavra-chave|Tipos de dados|Relacionamento de argumento|Falha de tempo de execução|  
|---|---|---|---|  
|[Função CType](../../../visual-basic/language-reference/functions/ctype-function.md)|Quaisquer tipos de dados|Ampliação ou conversão de estreitamento deve ser definido entre os dois tipos de dados|Gera <xref:System.InvalidCastException>|  
|`DirectCast`|Quaisquer tipos de dados|Um tipo deve herdar ou implementar o outro tipo|Gera <xref:System.InvalidCastException>|  
|[Operador TryCast](../../../visual-basic/language-reference/operators/trycast-operator.md)|Somente tipos de referência|Um tipo deve herdar ou implementar o outro tipo|Retorna [nada](../../../visual-basic/language-reference/nothing.md)|  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir demonstra dois usos do `DirectCast`, que falha em tempo de execução e outra que obter êxito.  
  
 [!code-vb[VbVbalrKeywords#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#1)]  
  
 No exemplo anterior, o tempo de execução do tipo de `q` é `Double`. `CType` é bem-sucedida pois `Double` pode ser convertido em `Integer`. No entanto, a primeira `DirectCast` falhar no tempo de execução porque o tempo de execução do tipo de `Double` não tem nenhuma relação de herança com `Integer`, mesmo que exista uma conversão. A segunda `DirectCast` é bem-sucedida pois ele converte do tipo <xref:System.Windows.Forms.Form> digitar <xref:System.Windows.Forms.Control>, do qual <xref:System.Windows.Forms.Form> herda.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Convert.ChangeType%2A?displayProperty=nameWithType>
- [Conversões de Widening e Narrowing](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [Conversões Implícitas e Explícitas](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
