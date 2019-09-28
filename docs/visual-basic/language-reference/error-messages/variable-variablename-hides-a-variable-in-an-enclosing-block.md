---
title: A variável '<variablename>' oculta uma variável em bloco delimitador
ms.date: 07/20/2015
f1_keywords:
- vbc30616
- bc30616
helpviewer_keywords:
- BC30616
ms.assetid: e7658ebc-da45-451b-a409-a0f8915f0beb
ms.openlocfilehash: 4312abef83728f432e2f6a492e5acad3450719b1
ms.sourcegitcommit: 35da8fb45b4cca4e59cc99a5c56262c356977159
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/28/2019
ms.locfileid: "71592058"
---
# <a name="variable-variablename-hides-a-variable-in-an-enclosing-block"></a>A variável ' \<variablename > ' oculta uma variável em um bloco delimitador
Uma variável colocada em um bloco tem o mesmo nome que outra variável local.  
  
 **ID do erro:** BC30616  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
- Renomeie a variável no bloco incluído para que ela não seja a mesma que qualquer outra variável local. Por exemplo:  
  
    ```vb  
    Dim a, b, x As Integer  
    If a = b Then  
       Dim y As Integer = 20 ' Uniquely named block variable.  
    End If  
    ```  
  
- Uma causa comum desse erro é o uso de `Catch e As Exception` dentro de um manipulador de eventos. Se esse for o caso, nomeie a variável de bloco `Catch` `ex` em vez de `e`.  
  
- Outra fonte comum desse erro é uma tentativa de acessar uma variável local declarada dentro de um bloco `Try` em um bloco separado `Catch`. Para corrigir isso, declare a variável fora da estrutura `Try...Catch...Finally`.  
  
## <a name="see-also"></a>Consulte também

- [Instrução Try...Catch...Finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
- [Declaração de Variável](../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
