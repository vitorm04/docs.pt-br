---
title: Variável de &#39; &lt;variablename&gt; &#39; oculta uma variável em um bloco delimitador
ms.date: 07/20/2015
f1_keywords:
- vbc30616
- bc30616
helpviewer_keywords:
- BC30616
ms.assetid: e7658ebc-da45-451b-a409-a0f8915f0beb
ms.openlocfilehash: 23ec659535b71ee9af189f5c4fec0dec2bb1cd8f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54719424"
---
# <a name="variable-39ltvariablenamegt39-hides-a-variable-in-an-enclosing-block"></a>Variável de &#39; &lt;variablename&gt; &#39; oculta uma variável em um bloco delimitador
Uma variável incluída em um bloco tem o mesmo nome que outra variável local.  
  
 **ID do erro:** BC30616  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Renomear a variável no bloco incluído para que não seja o mesmo que qualquer outra variável local. Por exemplo:  
  
    ```  
    Dim a, b, x As Integer  
    If a = b Then  
       Dim y As Integer = 20 ' Uniquely named block variable.  
    End If  
    ```  
  
-   Uma causa comum desse erro é o uso de `Catch e As Exception` dentro de um manipulador de eventos. Se esse for o caso, o nome do `Catch` variável de bloco `ex` em vez de `e`.  
  
-   Outra origem comum desse erro é uma tentativa de acessar uma variável local declarada dentro de um `Try` bloco em um separado `Catch` bloco. Para corrigir isso, declare a variável de fora a `Try...Catch...Finally` estrutura.  
  
## <a name="see-also"></a>Consulte também
- [Instrução Try...Catch...Finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
- [Declaração de Variável](../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
