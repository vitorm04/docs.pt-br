---
title: "Matriz conversões (Visual Basic) | Documentos do Microsoft"
ms.custom: 
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
- arrays [Visual Basic], converting type
- type conversion, arrays
- conversions, type
- arrays [Visual Basic], data types
- conversions, data type
- object arrays, converting type
- data type conversion, array conversions
- conversions, array types
- object arrays
ms.assetid: fceff7d2-a1b7-44c7-b9aa-8bd831d8a444
caps.latest.revision: 14
author: stevehoag
ms.author: shoag
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
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 74c9f6d721f2810edc4dd24a482664d384670208
ms.lasthandoff: 03/13/2017

---
# <a name="array-conversions-visual-basic"></a>Conversões de matriz (Visual Basic)
Você pode converter um tipo de matriz a um tipo de matriz diferente, desde que atendem às seguintes condições:  
  
-   **Classificação igual.** As classificações de duas matrizes devem ser as mesmas, ou seja, eles devem ter o mesmo número de dimensões. No entanto, os comprimentos das respectivas dimensões não precisa ser o mesmo.  
  
-   **Tipo de dados do elemento.** Os tipos de dados dos elementos de ambas as matrizes devem ser tipos de referência. Não é possível converter um `Integer` de matriz para uma `Long` de matriz, ou mesmo um `Object` de matriz, pois o tipo de pelo menos um valor está envolvido. Para obter mais informações, consulte [tipos de valor e tipos de referência](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md).  
  
-   **Convertibilidade.** Uma conversão de ampliação ou redução, deve ser possível entre os tipos de elemento das duas matrizes. Um exemplo que falha esse requisito é uma tentativa de conversão entre uma `String` matriz e uma matriz de uma classe derivam de <xref:System.Attribute?displayProperty=fullName>.</xref:System.Attribute?displayProperty=fullName> Esses dois tipos não têm nada em comum e nenhuma conversão de qualquer tipo existe entre eles.  
  
 Uma conversão de tipo de uma matriz para outro é ampliação ou redução dependendo se a conversão dos respectivos elementos é de ampliação ou redução. Para obter mais informações, consulte [Widening e conversões de estreitamento](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).  
  
## <a name="conversion-to-an-object-array"></a>Conversão em uma matriz de objetos  
 Ao declarar uma `Object` matriz sem inicializá-la, seu tipo de elemento é `Object` enquanto ele permanece não inicializado. Quando você defini-la para uma matriz de uma classe específica, ele usa o tipo de classe. No entanto, seu tipo subjacente ainda é `Object`, e você pode defini-lo posteriormente a outra matriz de uma classe não relacionada. Como todas as classes derivam `Object`, você pode alterar o tipo de elemento da matriz de qualquer classe a qualquer outra classe.  
  
 No exemplo a seguir, não existe nenhuma conversão entre tipos `student` e `String`, mas ambos derivam `Object`, portanto, todas as atribuições são válidas.  
  
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
 Se você originalmente declarar uma matriz com uma classe específica, seu tipo subjacente do elemento é dessa classe. Se você subsequentemente configurá-lo para uma matriz de outra classe, deve haver uma conversão entre as duas classes.  
  
 No exemplo a seguir, `students` é um `student` matriz. Como nenhuma conversão existe entre `String` e `student`, a última instrução falha.  
  
```  
Dim students() As student  
Dim names() As String = New String(3) {"Name0", "Name1", "Name2", "Name3"}  
students = New Student(3) {}  
' The following statement fails at compile time.  
students = names  
```  
  
## <a name="see-also"></a>Consulte também  
 [Tipos de dados](../../../../visual-basic/programming-guide/language-features/data-types/index.md)   
 [Conversões de tipo no Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)   
 [Conversões implícitas e explícitas](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)   
 [Conversões entre cadeias de caracteres e outros tipos](../../../../visual-basic/programming-guide/language-features/data-types/conversions-between-strings-and-other-types.md)   
 [Como: converter um objeto em outro tipo no Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/how-to-convert-an-object-to-another-type.md)   
 [Tipos de dados](../../../../visual-basic/language-reference/data-types/data-type-summary.md)   
 [Funções de conversão de tipo](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)   
 [Matrizes](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
