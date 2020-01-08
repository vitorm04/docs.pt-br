---
title: Como converter um objeto em outro tipo
ms.date: 07/20/2015
helpviewer_keywords:
- objects [Visual Basic], converting
ms.assetid: 60cb5fc7-7ba4-4ab5-9c24-480fa12ddcdc
ms.openlocfilehash: 6d16e0eafc3fa9233037abe0c92dcb1945ca8da9
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75341583"
---
# <a name="how-to-convert-an-object-to-another-type-in-visual-basic"></a>Como converter um objeto em outro tipo no Visual Basic
Você converte uma variável `Object` para outro tipo de dados usando uma palavra-chave de conversão, como a [função CType](../../../../visual-basic/language-reference/functions/ctype-function.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir converte uma variável `Object` em um `Integer` e um `String`.  
  
```vb  
Public Sub objectConversion(ByVal anObject As Object)  
    Dim anInteger As Integer  
    Dim aString As String  
    anInteger = CType(anObject, Integer)  
    aString = CType(anObject, String)  
End Sub  
```  
  
 Se você souber que o conteúdo de uma variável de `Object` é de um tipo de dados específico, é melhor converter a variável para esse tipo de dados. Se você continuar usando a variável `Object`, você incorrerá em *Boxing* e *unboxing* (para um tipo de valor) ou *associação tardia* (para um tipo de referência). Todas essas operações têm tempo de execução extra e tornam o desempenho mais lento.  
  
## <a name="compile-the-code"></a>Compilar o código  
 Este exemplo requer:  
  
- Uma referência ao namespace <xref:System?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Veja também

- <xref:System.Object>
- [Conversões de tipo no Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [Conversões de Widening e Narrowing](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [Conversões Implícitas e Explícitas](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [Conversões entre Cadeias de Caracteres e Outros Tipos](../../../../visual-basic/programming-guide/language-features/data-types/conversions-between-strings-and-other-types.md)
- [Conversões de Matriz](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md)
- [Estruturas](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [Tipos de Dados](../../../../visual-basic/language-reference/data-types/index.md)
- [Funções de Conversão do Tipo](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)
