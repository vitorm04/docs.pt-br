---
title: Operador DirectCast
ms.date: 07/20/2015
f1_keywords:
- vb.directCast
- directCast
helpviewer_keywords:
- DirectCast keyword [Visual Basic]
ms.assetid: 63e5a1d0-4d9e-4732-bf8f-e90c0c8784b8
ms.openlocfilehash: 8ea29b80cf27bbb2c21a8cebbfaa0a294e05f11d
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74331316"
---
# <a name="directcast-operator-visual-basic"></a>Operador DirectCast (Visual Basic)
Apresenta uma operação de conversão de tipo baseada na herança ou implementação.  
  
## <a name="remarks"></a>Comentários  
 `DirectCast` não usa as rotinas auxiliares de tempo de execução Visual Basic para conversão, para que possa fornecer um desempenho um pouco melhor do que `CType` ao converter de e para o tipo de dados `Object`.  
  
 Use a palavra-chave `DirectCast` semelhante à maneira como você usa a [função CType](../../../visual-basic/language-reference/functions/ctype-function.md) e a palavra-chave do [Operador TryCast](../../../visual-basic/language-reference/operators/trycast-operator.md) . Você fornece uma expressão como o primeiro argumento e um tipo para convertê-lo como o segundo argumento. `DirectCast` requer uma relação de herança ou implementação entre os tipos de dados dos dois argumentos. Isso significa que um tipo deve herdar ou implementar o outro.  
  
## <a name="errors-and-failures"></a>Erros e falhas  
 `DirectCast` gerará um erro do compilador se detectar que nenhuma relação de herança ou implementação existe. Mas a falta de um erro do compilador não garante uma conversão bem-sucedida. Se a conversão desejada for restrita, ela poderá falhar em tempo de execução. Se isso acontecer, o tempo de execução gera um erro de <xref:System.InvalidCastException>.  
  
## <a name="conversion-keywords"></a>Palavras-chave de conversão  
 Uma comparação das palavras-chave de conversão de tipo é a seguinte:  
  
|Palavra-chave|Tipos de dados|Relação de argumento|Falha de tempo de execução|  
|---|---|---|---|  
|[Função CType](../../../visual-basic/language-reference/functions/ctype-function.md)|Quaisquer tipos de dados|A conversão de alargamento ou de estreitamento deve ser definida entre os dois tipos de dados|Gera <xref:System.InvalidCastException>|  
|`DirectCast`|Quaisquer tipos de dados|Um tipo deve herdar ou implementar o outro tipo|Gera <xref:System.InvalidCastException>|  
|[Operador TryCast](../../../visual-basic/language-reference/operators/trycast-operator.md)|Somente tipos de referência|Um tipo deve herdar ou implementar o outro tipo|Não retorna [nada](../../../visual-basic/language-reference/nothing.md)|  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir demonstra dois usos de `DirectCast`, um que falha em tempo de execução e um que é bem sucedido.  
  
 [!code-vb[VbVbalrKeywords#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#1)]  
  
 No exemplo anterior, o tipo de tempo de execução de `q` é `Double`. `CType` sucede porque `Double` pode ser convertido em `Integer`. No entanto, a primeira `DirectCast` falha em tempo de execução porque o tipo de tempo de execução de `Double` não tem nenhuma relação de herança com `Integer`, embora exista uma conversão. O segundo `DirectCast` é executado com sucesso porque converte do tipo <xref:System.Windows.Forms.Form> para o tipo <xref:System.Windows.Forms.Control>, do qual <xref:System.Windows.Forms.Form> herda.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Convert.ChangeType%2A?displayProperty=nameWithType>
- [Conversões de Widening e Narrowing](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [Conversões Implícitas e Explícitas](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
