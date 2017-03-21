---
title: 'Como: converter um objeto em outro tipo no Visual Basic | Documentos do Microsoft'
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
- objects [Visual Basic], converting
ms.assetid: 60cb5fc7-7ba4-4ab5-9c24-480fa12ddcdc
caps.latest.revision: 15
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
ms.openlocfilehash: aa8a7fe9263364c49babfa4ca9810991807ba7d5
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-convert-an-object-to-another-type-in-visual-basic"></a>Como converter um objeto em outro tipo no Visual Basic
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
  
 Se você souber que o conteúdo de um `Object` variável são de um tipo de dados específico, é melhor converter a variável para esse tipo de dados. Se você continuar a usar o `Object` variável, você provoca uma *conversão boxing* e *unboxing* (para um tipo de valor) ou *ligação tardia* (para um tipo de referência). Essas operações usam mais tempo de execução e diminuem o desempenho.  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este exemplo requer:  
  
-   Uma referência para o <xref:System?displayProperty=fullName>namespace.</xref:System?displayProperty=fullName>  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Object></xref:System.Object>   
 [Conversões de tipo no Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)   
 [Conversões entre](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)   
 [Conversões implícitas e explícitas](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)   
 [Conversões entre cadeias de caracteres e outros tipos](../../../../visual-basic/programming-guide/language-features/data-types/conversions-between-strings-and-other-types.md)   
 [Conversões de matriz](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md)   
 [Estruturas](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)   
 [Tipos de dados](../../../../visual-basic/language-reference/data-types/data-type-summary.md)   
 [Funções de Conversão do Tipo](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)
