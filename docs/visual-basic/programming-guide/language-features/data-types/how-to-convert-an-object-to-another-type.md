---
title: "Como converter um objeto em outro tipo no Visual Basic | Microsoft Docs"
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
  - "objetos [Visual Basic], convertendo"
ms.assetid: 60cb5fc7-7ba4-4ab5-9c24-480fa12ddcdc
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como converter um objeto em outro tipo no Visual Basic
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Você converte uma variável `Object` para outro tipo de dados usando uma palavra\-chave de conversão, como [Função CType](../../../../visual-basic/language-reference/functions/ctype-function.md).  
  
## Exemplo  
 O exemplo seguinte converte uma variável `Object` para um `Integer` e uma `String`.  
  
```  
Public Sub objectConversion(ByVal anObject As Object)  
    Dim anInteger As Integer  
    Dim aString As String  
    anInteger = CType(anObject, Integer)  
    aString = CType(anObject, String)  
End Sub  
```  
  
 Se você souber que o conteúdo de uma variável `Object` é de um determinado tipo de dados, é melhor converter a variável para esse mesmo tipo de dados.  Se você continuar a usar a variável `Object`,você provoca o *boxing* ou  *unboxing* \(para um tipo de valor\) ou  *ligação tardia*  \(para uma tipo de referência\).  Essas operações todas levam mais tempo de execução e diminuem o desempenho.  
  
## Compilando o código  
 Este exemplo requer:  
  
-   Uma referência ao namespace <xref:System?displayProperty=fullName>.  
  
## Consulte também  
 <xref:System.Object>   
 [Conversões de tipo no Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)   
 [Conversões de Widening e Narrowing](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)   
 [Conversões implícitas e explícitas](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)   
 [Conversões entre cadeias de caracteres e outros tipos](../../../../visual-basic/programming-guide/language-features/data-types/conversions-between-strings-and-other-types.md)   
 [Conversões de matriz](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md)   
 [Estruturas](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)   
 [Tipos de dados](../../../../visual-basic/language-reference/data-types/data-type-summary.md)   
 [Funções de conversão do tipo](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)