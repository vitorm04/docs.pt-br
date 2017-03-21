---
title: "Tipo de &quot;&lt;variablename&gt;&quot; não pode ser inferido porque os limites do loop e a variável step não se estendem ao mesmo tipo | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30982
- vbc30982
dev_langs:
- VB
helpviewer_keywords:
- BC30982
ms.assetid: 741e85d9-a747-42ad-a1e1-a3f1928aaff5
caps.latest.revision: 30
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
ms.openlocfilehash: 126b34937364caa960ce8d7aed50d922af381529
ms.lasthandoff: 03/13/2017

---
# <a name="type-of-39ltvariablenamegt39-cannot-be-inferred-because-the-loop-bounds-and-the-step-variable-do-not-widen-to-the-same-type"></a>Tipo de '&lt;variablename&gt;' não pode ser inferido porque os limites do loop e a variável step não se estendem ao mesmo tipo
Você escreveu um `For...Next` loop em que o compilador não pode inferir um tipo de dados para a variável de controle de loop porque as seguintes condições forem verdadeiras:  
  
-   O tipo de dados da variável de controle de loop não é especificado com um `As` cláusula.  
  
-   Os limites do loop e a variável step contêm pelo menos dois tipos de dados.  
  
-   Não há nenhuma conversão padrão entre os tipos de dados.  
  
 Portanto, o compilador não pode inferir o tipo de dados da variável de controle do loop.  
  
 No exemplo a seguir, a variável step é um caractere e os limites do loop são ambos inteiros. Como não há nenhuma conversão padrão entre caracteres e inteiros, este erro é relatado.  
  
```vb  
Dim stepVar = "1"c  
Dim m = 0  
Dim n = 20  
  
' Not valid.  
' For i = 1 To 10 Step stepVar  
    ' Loop processing  
' Next  
```  
  
 **ID do erro:** BC30982  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Altere os tipos dos limites do loop e a variável step conforme necessário para que pelo menos um deles é um tipo que os outros ampliam. No exemplo anterior, altere o tipo de `stepVar` para `Integer`.  
  
    ```  
    Dim stepVar = 1  
    ```  
  
     —ou—  
  
    ```  
    Dim stepVar As Integer = 1  
    ```  
  
-   Use funções de conversão explícitas para converter os limites do loop e a variável de etapa para os tipos apropriados. No exemplo anterior, aplique a `Val` função `stepVar`.  
  
    ```  
    For i = 1 To 10 Step Val(stepVar)  
        ' Loop processing  
    Next  
    ```  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualBasic.Conversion.Val%2A></xref:Microsoft.VisualBasic.Conversion.Val%2A>   
 [Para... Próxima instrução](../../../visual-basic/language-reference/statements/for-next-statement.md)   
 [Conversões implícitas e explícitas](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)   
 [Inferência de tipo local](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)   
 [Instrução Option Infer](../../../visual-basic/language-reference/statements/option-infer-statement.md)   
 [Funções de conversão de tipo](../../../visual-basic/language-reference/functions/type-conversion-functions.md)   
 [Conversões de Widening e Narrowing](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
