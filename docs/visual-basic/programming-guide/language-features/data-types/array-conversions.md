---
title: Conversões de matriz (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [Visual Basic], converting type
- type conversion [Visual Basic], arrays
- conversions [Visual Basic], type
- arrays [Visual Basic], data types
- conversions [Visual Basic], data type
- object arrays [Visual Basic], converting type
- data type conversion [Visual Basic], array conversions
- conversions [Visual Basic], array types
- object arrays
ms.assetid: fceff7d2-a1b7-44c7-b9aa-8bd831d8a444
ms.openlocfilehash: 93e6365a70f52f730b016cd4d4ac9382baeeba55
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43734298"
---
# <a name="array-conversions-visual-basic"></a>Conversões de matriz (Visual Basic)
Você pode converter um tipo de matriz a um tipo de matriz diferente, desde que atendem às seguintes condições:  
  
-   **Classificação igual.** As classificações de duas matrizes devem ser as mesmas, ou seja, eles devem ter o mesmo número de dimensões. No entanto, os comprimentos das dimensões respectivos não precisa ser o mesmo.  
  
-   **Tipo de dados do elemento.** Os tipos de dados dos elementos de ambas as matrizes devem ser tipos de referência. Não é possível converter um `Integer` de matriz para uma `Long` array ou até mesmo em um `Object` de matriz, pois o tipo de pelo menos um valor está envolvido. Para obter mais informações, consulte [tipos de valor e tipos de referência](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md).  
  
-   **Convertibilidade.** Uma conversão de ampliação ou redução, deve ser possível entre os tipos de elementos de duas matrizes. Um exemplo que falha esse requisito é uma tentativa de conversão entre uma `String` matriz e uma matriz de uma classe derivam de <xref:System.Attribute?displayProperty=nameWithType>. Esses dois tipos não têm nada em comum, e nenhuma conversão de qualquer tipo existe entre eles.  
  
 Uma conversão de tipo de uma matriz para outra é de ampliação ou redução dependendo se a conversão dos respectivos elementos é de ampliação ou redução. Para obter mais informações, consulte [Ampliando e restringindo conversões](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).  
  
## <a name="conversion-to-an-object-array"></a>Conversão em uma matriz de objetos  
 Quando você declara uma `Object` matriz sem inicializá-la, o tipo de elemento é `Object` , desde que ele permaneça não inicializado. Quando você defini-lo para uma matriz de uma classe específica, ele usa o tipo de classe. No entanto, seu tipo subjacente ainda é `Object`, e, posteriormente, você pode defini-lo para outra matriz de uma classe não relacionada. Uma vez que todas as classes derivam `Object`, você pode alterar o tipo de elemento da matriz de qualquer classe para qualquer outra classe.  
  
 No exemplo a seguir, não existe conversão entre tipos `student` e `String`, mas ambos derivam `Object`, portanto, todas as atribuições são válidas.  
  
```  
' Assume student has already been defined as a class.  
Dim testArray() As Object  
' testArray is still an Object array at this point.  
Dim names() As String = New String(3) {"Name0", "Name1", "Name2", "Name3"}  
testArray = New student(3) {}  
' testArray is now of type student().  
testArray = names  
' testArray is now a String array.  
```  
  
### <a name="underlying-type-of-an-array"></a>Tipo subjacente de uma matriz  
 Se você originalmente declarar uma matriz com uma classe específica, seu tipo de elemento subjacente é dessa classe. Se, posteriormente, defini-lo para uma matriz de outra classe, deve haver uma conversão entre as duas classes.  
  
 No exemplo a seguir `students` é um `student` matriz. Uma vez que não existe conversão entre `String` e `student`, a última instrução falha.  
  
```  
Dim students() As student  
Dim names() As String = New String(3) {"Name0", "Name1", "Name2", "Name3"}  
students = New Student(3) {}  
' The following statement fails at compile time.  
students = names  
```  
  
## <a name="see-also"></a>Consulte também  
 [Tipos de Dados](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 [Conversões de tipo no Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [Conversões Implícitas e Explícitas](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)  
 [Conversões entre Cadeias de Caracteres e Outros Tipos](../../../../visual-basic/programming-guide/language-features/data-types/conversions-between-strings-and-other-types.md)  
 [Como: converter um objeto em outro tipo no Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/how-to-convert-an-object-to-another-type.md)  
 [Tipos de Dados](../../../../visual-basic/language-reference/data-types/index.md)  
 [Funções de Conversão do Tipo](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [Matrizes](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
