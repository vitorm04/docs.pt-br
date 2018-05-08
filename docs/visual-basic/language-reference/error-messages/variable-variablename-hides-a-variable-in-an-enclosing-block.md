---
title: Variável &#39; &lt;variablename&gt; &#39; oculta uma variável em um bloco delimitador
ms.date: 07/20/2015
f1_keywords:
- vbc30616
- bc30616
helpviewer_keywords:
- BC30616
ms.assetid: e7658ebc-da45-451b-a409-a0f8915f0beb
ms.openlocfilehash: 58e09caeb477d6b1df7f3be17e0a8ee05be3551e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="variable-39ltvariablenamegt39-hides-a-variable-in-an-enclosing-block"></a>Variável &#39; &lt;variablename&gt; &#39; oculta uma variável em um bloco delimitador
Uma variável incluída em um bloco tem o mesmo nome que outra variável local.  
  
 **ID do erro:** BC30616  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Renomear a variável no bloco do anexo para que não seja o mesmo que todas as outras variáveis locais. Por exemplo:  
  
    ```  
    Dim a, b, x As Integer  
    If a = b Then  
       Dim y As Integer = 20 ' Uniquely named block variable.  
    End If  
    ```  
  
-   Uma causa comum para esse erro é o uso de `Catch e As Exception` dentro de um manipulador de eventos. Se esse for o caso, o nome de `Catch` variável de bloco `ex` em vez de `e`.  
  
-   Outra origem comum desse erro é uma tentativa de acessar uma variável local declarada dentro de um `Try` bloco em um separado `Catch` bloco. Para corrigir isso, declare a variável de fora de `Try...Catch...Finally` estrutura.  
  
## <a name="see-also"></a>Consulte também  
 [Instrução Try...Catch...Finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)  
 [Declaração de Variável](../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
