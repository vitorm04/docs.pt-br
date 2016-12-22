---
title: "Convers&#245;es de matriz (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "matrizes [Visual Basic], tipo de conversão"
  - "matrizes [Visual Basic], tipos de dados"
  - "conversões, tipos de matriz"
  - "conversões,   (tipo de dados)"
  - "conversões, Tipo "
  - "conversão de tipo de dados, conversões de matriz"
  - "matrizes de objetos"
  - "matrizes de objetos, tipo de conversão"
  - "conversão de tipo, matrizes"
ms.assetid: fceff7d2-a1b7-44c7-b9aa-8bd831d8a444
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Convers&#245;es de matriz (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Você pode converter um tipo de matriz para um tipo de matriz diferentes, desde que você atender as seguintes condições:  
  
-   **Classificação igual.** As classificações das duas matrizes devem ser iguais, ou seja, eles devem ter o mesmo número de dimensões.  No entanto, os comprimentos das respectivas dimensões não precisará ser o mesmo.  
  
-   **Tipo de dados do elemento.** Os tipos dos elementos de ambos os conjuntos de dados devem ser de tipos de referência.  Não é possível converter um `Integer` array, para um `Long` de array ou mesmo um `Object` de array, porque o tipo de pelo menos um valor é envolvido.  Para obter mais informações, consulte [Tipos de valor e referência](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md).  
  
-   **Convertibility.** Uma conversão, o alargamento ou restringir, deve ser possível entre os tipos de elementos das duas matrizes.  Um exemplo que falha esse requisito é uma tentativa de conversão entre um `String` matriz e uma matriz de uma classe derivada de <xref:System.Attribute?displayProperty=fullName>.  Esses dois tipos nada têm em comum, e nenhuma conversão de qualquer tipo existe entre eles.  
  
 Uma conversão de tipo de um array para outro é ampliando ou estreitando dependendo se a conversão dos respectivos elementos está ampliando ou estreitando.  Para obter mais informações, consulte [Conversões de Widening e Narrowing](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).  
  
## Conversão em uma matriz de objeto  
 Quando você declara uma `Object` matriz sem inicializá\-lo, seu tipo de elemento é `Object` , contanto que ele permaneça não inicializado.  Quando você defini\-la para uma matriz de uma classe específica, ele assume o tipo de classe.  No entanto, seu tipo subjacente ainda é `Object`, e, posteriormente, você pode defini\-la a outra matriz de uma classe não relacionada.  Uma vez que todas as classes derivar `Object`, você pode alterar o tipo de elemento da matriz de qualquer classe para qualquer outra classe.  
  
 No exemplo a seguir, não existe nenhuma conversão entre tipos de `student` e `String`, mas ambos derivam da `Object`, portanto, todas as atribuições são válidas.  
  
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
  
### Tipo subjacente de uma matriz  
 Se você originalmente declarar uma matriz com uma classe específica, o seu tipo de elemento subjacente é aquela classe.  Se você subseqüentemente defini\-la para uma matriz de outra classe, deve haver uma conversão entre as duas classes.  
  
 No exemplo a seguir, `students` é um `student` array.  Desde que nenhuma conversão existe entre `String` e `student`, a última instrução falha.  
  
```  
Dim students() As student  
Dim names() As String = New String(3) {"Name0", "Name1", "Name2", "Name3"}  
students = New Student(3) {}  
' The following statement fails at compile time.  
students = names  
```  
  
## Consulte também  
 [Tipos de dados](../../../../visual-basic/programming-guide/language-features/data-types/index.md)   
 [Conversões de tipo no Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)   
 [Conversões implícitas e explícitas](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)   
 [Conversões entre cadeias de caracteres e outros tipos](../../../../visual-basic/programming-guide/language-features/data-types/conversions-between-strings-and-other-types.md)   
 [Como converter um objeto em outro tipo no Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/how-to-convert-an-object-to-another-type.md)   
 [Tipos de dados](../../../../visual-basic/language-reference/data-types/data-type-summary.md)   
 [Funções de conversão do tipo](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)   
 [Matrizes](../../../../visual-basic/programming-guide/language-features/arrays/index.md)