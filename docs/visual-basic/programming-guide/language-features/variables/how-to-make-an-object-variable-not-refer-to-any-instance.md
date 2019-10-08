---
title: 'Como: Fazer uma variável de objeto não se referir a nenhuma instância (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- Nothing keyword [Visual Basic], variable assignment
- object variables [Visual Basic], null reference
ms.assetid: e6d30578-bdae-4142-a3ac-a10697bf696a
ms.openlocfilehash: e647f2f891b06aa1767faac49b01df98ea31ec1c
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004906"
---
# <a name="how-to-make-an-object-variable-not-refer-to-any-instance-visual-basic"></a>Como: Fazer uma variável de objeto não se referir a nenhuma instância (Visual Basic)
Você pode desassociar uma variável de objeto de qualquer instância de objeto, definindo-a como [Nothing](../../../../visual-basic/language-reference/nothing.md).  
  
### <a name="to-disassociate-an-object-variable-from-any-object-instance"></a>Para desassociar uma variável de objeto de qualquer instância de objeto  
  
- Defina a variável como `Nothing` em uma instrução de atribuição.  
  
    ```vb  
    ' Assume account is a defined class  
    Dim currentAccount As account  
    currentAccount = Nothing  
    ```  
  
## <a name="robust-programming"></a>Programação robusta  
 Se o seu código tentar acessar um membro de uma variável de objeto que foi definida como `Nothing`, ocorrerá um <xref:System.NullReferenceException>. Se você definir uma variável de objeto como `Nothing` frequentemente, ou se for possível que a variável não seja inicializada, é uma boa ideia colocar os acessos de membros em um bloco `Try...Catch...Finally`.  
  
## <a name="net-framework-security"></a>Segurança do .NET Framework  
 Se você usar uma variável de objeto para objetos que contêm dados confidenciais ou confidenciais, poderá definir a variável como `Nothing` quando não estiver lidando ativamente com um desses objetos. Isso reduz a chance de código mal-intencionado obter acesso aos dados.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.NullReferenceException>
- [Variáveis de Objeto](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [Atribuição de variável do objeto](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)
- [Nothing](../../../../visual-basic/language-reference/nothing.md)
- [Instrução Try...Catch...Finally](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
