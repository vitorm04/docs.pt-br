---
title: 'Como: Converter um objeto em outro tipo no Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- objects [Visual Basic], converting
ms.assetid: 60cb5fc7-7ba4-4ab5-9c24-480fa12ddcdc
ms.openlocfilehash: 1e515c0f4ce8e787754c61a9b53d247fa93c49f2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61906523"
---
# <a name="how-to-convert-an-object-to-another-type-in-visual-basic"></a>Como: Converter um objeto em outro tipo no Visual Basic
Converter um `Object` variável em outro tipo de dados usando uma palavra-chave de conversão, como [função CType](../../../../visual-basic/language-reference/functions/ctype-function.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir converte um `Object` variável para um `Integer` e um `String`.  
  
```  
Public Sub objectConversion(ByVal anObject As Object)  
    Dim anInteger As Integer  
    Dim aString As String  
    anInteger = CType(anObject, Integer)  
    aString = CType(anObject, String)  
End Sub  
```  
  
 Se você souber que o conteúdo de um `Object` variável são de um tipo de dados específico, é melhor converter a variável para esse tipo de dados. Se você continuar a usar o `Object` variável, você incorre em um *boxing* e *unboxing* (para um tipo de valor) ou *ligação tardia* (para um tipo de referência). Essas operações usam mais tempo de execução e diminuem o desempenho.  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este exemplo requer:  
  
- Uma referência para o <xref:System?displayProperty=nameWithType> namespace.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Object>
- [Conversões de tipo no Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [Conversões de Widening e Narrowing](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [Conversões Implícitas e Explícitas](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [Conversões entre Cadeias de Caracteres e Outros Tipos](../../../../visual-basic/programming-guide/language-features/data-types/conversions-between-strings-and-other-types.md)
- [Conversões de Matriz](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md)
- [Estruturas](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [Tipos de Dados](../../../../visual-basic/language-reference/data-types/index.md)
- [Funções de Conversão do Tipo](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)
