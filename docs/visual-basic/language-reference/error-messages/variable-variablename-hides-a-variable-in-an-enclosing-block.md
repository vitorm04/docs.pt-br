---
title: A variável '<variablename>' oculta uma variável em bloco delimitador
ms.date: 07/20/2015
f1_keywords:
- vbc30616
- bc30616
helpviewer_keywords:
- BC30616
ms.assetid: e7658ebc-da45-451b-a409-a0f8915f0beb
ms.openlocfilehash: 15c35cbb829bec782771b584ea25b111b81b5e1f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58827127"
---
# <a name="variable-variablename-hides-a-variable-in-an-enclosing-block"></a>Variável '\<variablename >' oculta uma variável em um bloco delimitador
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
