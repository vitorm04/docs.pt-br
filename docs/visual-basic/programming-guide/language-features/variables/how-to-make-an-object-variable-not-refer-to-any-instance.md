---
title: Como fazer uma variável de objeto não se referir a nenhuma instância
ms.date: 07/20/2015
helpviewer_keywords:
- Nothing keyword [Visual Basic], variable assignment
- object variables [Visual Basic], null reference
ms.assetid: e6d30578-bdae-4142-a3ac-a10697bf696a
ms.openlocfilehash: 320dadb61c12f3339c5328dcef31c41503892c56
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352889"
---
# <a name="how-to-make-an-object-variable-not-refer-to-any-instance-visual-basic"></a>Como fazer uma variável de objeto não se referir a nenhuma instância (Visual Basic)
Você pode desassociar uma variável de objeto de qualquer instância de objeto, definindo-a como [Nothing](../../../../visual-basic/language-reference/nothing.md).  
  
### <a name="to-disassociate-an-object-variable-from-any-object-instance"></a>Para desassociar uma variável de objeto de qualquer instância de objeto  
  
- Defina a variável como `Nothing` em uma instrução de atribuição.  
  
    ```vb  
    ' Assume account is a defined class  
    Dim currentAccount As account  
    currentAccount = Nothing  
    ```  
  
## <a name="robust-programming"></a>Programação robusta  
 Se o seu código tentar acessar um membro de uma variável de objeto que foi definida como `Nothing`, ocorrerá uma <xref:System.NullReferenceException>. Se você definir uma variável de objeto como `Nothing` frequentemente, ou se for possível que a variável não seja inicializada, é uma boa ideia colocar os acessos de membros em um bloco de `Try...Catch...Finally`.  
  
## <a name="net-framework-security"></a>Segurança do .NET Framework  
 Se você usar uma variável de objeto para objetos que contêm dados confidenciais ou confidenciais, poderá definir a variável como `Nothing` quando não estiver lidando ativamente com um desses objetos. Isso reduz a chance de código mal-intencionado obter acesso aos dados.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.NullReferenceException>
- [Variáveis de Objeto](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [Atribuição de variável do objeto](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)
- [Nothing](../../../../visual-basic/language-reference/nothing.md)
- [Instrução Try...Catch...Finally](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
