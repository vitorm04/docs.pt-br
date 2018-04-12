---
title: Variável &#39; &lt;variablename&gt;&#39; oculta uma variável em um bloco delimitador
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30616
- bc30616
helpviewer_keywords:
- BC30616
ms.assetid: e7658ebc-da45-451b-a409-a0f8915f0beb
caps.latest.revision: 8
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2af570cd002b4be4e15a7c03b0ffc2ff84ba3982
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="variable-39ltvariablenamegt39-hides-a-variable-in-an-enclosing-block"></a>Variável &#39; &lt;variablename&gt;&#39; oculta uma variável em um bloco delimitador
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
