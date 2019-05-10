---
title: 'Como: Fazer um objeto variável não se referir a qualquer instância (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- Nothing keyword [Visual Basic], variable assignment
- object variables [Visual Basic], null reference
ms.assetid: e6d30578-bdae-4142-a3ac-a10697bf696a
ms.openlocfilehash: 820d4cb9d17bf467d257bfbba5f43f07228c0b4f
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64663554"
---
# <a name="how-to-make-an-object-variable-not-refer-to-any-instance-visual-basic"></a>Como: Fazer um objeto variável não se referir a qualquer instância (Visual Basic)
Você pode desassociar uma variável de objeto de qualquer instância do objeto definindo-a para [nada](../../../../visual-basic/language-reference/nothing.md).  
  
### <a name="to-disassociate-an-object-variable-from-any-object-instance"></a>Para desassociar uma variável de objeto de qualquer instância do objeto  
  
- Defina a variável para `Nothing` em uma instrução de atribuição.  
  
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
