---
title: O tipo de '<variablename>' não pode ser inferido porque os limites de loop e a variável step não são ampliados com o mesmo tipo
ms.date: 07/20/2015
f1_keywords:
- bc30982
- vbc30982
helpviewer_keywords:
- BC30982
ms.assetid: 741e85d9-a747-42ad-a1e1-a3f1928aaff5
ms.openlocfilehash: 1f1df0c7391c027994caabadc4b857bec55f5938
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57367174"
---
# <a name="type-of-variablename-cannot-be-inferred-because-the-loop-bounds-and-the-step-variable-do-not-widen-to-the-same-type"></a>Tipo de '\<variablename >' não pode ser inferido porque os limites do loop e a variável step não são ampliados para o mesmo tipo
Você escreveu uma `For...Next` loop em que o compilador não é possível inferir um tipo de dados para a variável de controle de loop porque as seguintes condições forem verdadeiras:  
  
-   O tipo de dados da variável de controle de loop não é especificado com um `As` cláusula.  
  
-   Os limites do loop e a variável step contêm pelo menos dois tipos de dados.  
  
-   Não há nenhuma conversão padrão entre os tipos de dados.  
  
 Portanto, o compilador não pode inferir o tipo de dados da variável de controle de um loop.  
  
 No exemplo a seguir, a variável step é um caractere e os limites do loop são ambos inteiros. Como não há nenhuma conversão padrão entre caracteres e inteiros, esse erro é relatado.  
  
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
  
-   Altere os tipos de limites do loop e a variável step conforme necessário para que pelo menos um deles é um tipo que os outros ampliam. No exemplo anterior, altere o tipo de `stepVar` para `Integer`.  
  
    ```  
    Dim stepVar = 1  
    ```  
  
     —ou—  
  
    ```  
    Dim stepVar As Integer = 1  
    ```  
  
-   Use funções de conversão explícitas para converter os limites do loop e a variável de etapa para os tipos apropriados. No exemplo anterior, se aplicam a `Val` função `stepVar`.  
  
    ```  
    For i = 1 To 10 Step Val(stepVar)  
        ' Loop processing  
    Next  
    ```  
  
## <a name="see-also"></a>Consulte também
- <xref:Microsoft.VisualBasic.Conversion.Val%2A>
- [Instrução For...Next](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [Conversões Implícitas e Explícitas](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [Inferência de Tipo de Variável Local](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [Instrução Option Infer](../../../visual-basic/language-reference/statements/option-infer-statement.md)
- [Funções de Conversão do Tipo](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Conversões de Widening e Narrowing](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
