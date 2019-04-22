---
title: 'Como: Fazer um objeto variável não se referir a qualquer instância (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- Nothing keyword [Visual Basic], variable assignment
- object variables [Visual Basic], null reference
ms.assetid: e6d30578-bdae-4142-a3ac-a10697bf696a
ms.openlocfilehash: 373d4ae84c44b212ad02b0b4266af75921e40423
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58818679"
---
# <a name="how-to-make-an-object-variable-not-refer-to-any-instance-visual-basic"></a>Como: Fazer um objeto variável não se referir a qualquer instância (Visual Basic)
Você pode desassociar uma variável de objeto de qualquer instância do objeto definindo-a para [nada](../../../../visual-basic/language-reference/nothing.md).  
  
### <a name="to-disassociate-an-object-variable-from-any-object-instance"></a>Para desassociar uma variável de objeto de qualquer instância do objeto  
  
-   Defina a variável para `Nothing` em uma instrução de atribuição.  
  
    ```  
    ' Assume account is a defined class  
    Dim currentAccount As account  
    currentAccount = Nothing  
    ```  
  
## <a name="robust-programming"></a>Programação robusta  
 Se seu código tentar acessar um membro de uma variável de objeto que foi definido como `Nothing`, um <xref:System.NullReferenceException> ocorre. Se você definir uma variável de objeto como `Nothing` com frequência, ou se for possível, a variável não é inicializada, é uma boa ideia colocar os acessos de membro em um `Try...Catch...Finally` bloco.  
  
## <a name="net-framework-security"></a>Segurança do .NET Framework  
 Se você usar uma variável de objeto para objetos que contêm dados confidenciais, você pode definir a variável `Nothing` quando você não está ativamente lidando com um desses objetos. Isso reduz a chance de códigos mal-intencionados obtenham acesso aos dados.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.NullReferenceException>
- [Variáveis de Objeto](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [Atribuição de variável do objeto](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)
- [Nothing](../../../../visual-basic/language-reference/nothing.md)
- [Instrução Try...Catch...Finally](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
