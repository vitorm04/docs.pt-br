---
title: Tipo de &#39; &lt;variablename&gt;&#39; não pode ser inferido porque os limites do loop e a variável step não se estendem ao mesmo tipo
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30982
- vbc30982
helpviewer_keywords:
- BC30982
ms.assetid: 741e85d9-a747-42ad-a1e1-a3f1928aaff5
caps.latest.revision: 30
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 022e29e38a93d2880bbfa250e65a8b95b39ff140
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="type-of-39ltvariablenamegt39-cannot-be-inferred-because-the-loop-bounds-and-the-step-variable-do-not-widen-to-the-same-type"></a>Tipo de &#39; &lt;variablename&gt;&#39; não pode ser inferido porque os limites do loop e a variável step não se estendem ao mesmo tipo
Você escreveu uma `For...Next` loop no qual o compilador não é possível inferir um tipo de dados para a variável de controle de loop porque as seguintes condições forem verdadeiras:  
  
-   O tipo de dados da variável de controle de loop não é especificado com um `As` cláusula.  
  
-   Os limites do loop e a variável de etapa contém pelo menos dois tipos de dados.  
  
-   Não há conversões padrão existe entre os tipos de dados.  
  
 Portanto, o compilador não pode inferir o tipo de dados da variável de controle do loop.  
  
 No exemplo a seguir, a variável de etapa é um caractere e os limites do loop são ambos inteiros. Como não há nenhuma conversão padrão entre caracteres e inteiros, este erro é relatado.  
  
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
  
-   Altere os tipos de limites do loop e a variável de etapa conforme necessário para que pelo menos um deles é um tipo que os outros ampliam. No exemplo anterior, altere o tipo de `stepVar` para `Integer`.  
  
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
 <xref:Microsoft.VisualBasic.Conversion.Val%2A>  
 [Instrução For...Next](../../../visual-basic/language-reference/statements/for-next-statement.md)  
 [Conversões Implícitas e Explícitas](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)  
 [Inferência de Tipo de Variável Local](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [Instrução Option Infer](../../../visual-basic/language-reference/statements/option-infer-statement.md)  
 [Funções de Conversão do Tipo](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [Conversões de Widening e Narrowing](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
