---
title: 'Como: Controlar o escopo de uma variável (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], scope
- declared elements [Visual Basic], scope
- visibility [Visual Basic], declared elements
- variables [Visual Basic], visibility
- scope [Visual Basic], declared elements
- scope [Visual Basic], variables
- scope [Visual Basic], Visual Basic
- declared elements [Visual Basic], visibility
- visibility [Visual Basic], variables
ms.assetid: 44b7f62a-cb5c-4d50-bce9-60ae68f87072
ms.openlocfilehash: ef7957a991718112fe01c4fa3a85f29b9226abd3
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58818717"
---
# <a name="how-to-control-the-scope-of-a-variable-visual-basic"></a>Como: Controlar o escopo de uma variável (Visual Basic)
Normalmente, uma variável está no *escopo*, ou visível para referência, em toda a região na qual você declará-la. Em alguns casos, a variável *nível de acesso* podem influenciar seu escopo.  
  
 Para obter mais informações, consulte [escopo no Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md).  
  
## <a name="scope-at-block-or-procedure-level"></a>Escopo no nível de procedimento ou bloco  
  
#### <a name="to-make-a-variable-visible-only-within-a-block"></a>Para fazer uma variável visível somente dentro de um bloco  
  
-   Coloque o [instrução Dim](../../../../visual-basic/language-reference/statements/dim-statement.md) para a variável entre o Iniciando e encerrando instruções de declaração desse bloco, por exemplo, entre a `For` e `Next` instruções de um `For` loop.  
  
     Você pode fazer referência à variável apenas de dentro do bloco.  
  
#### <a name="to-make-a-variable-visible-only-within-a-procedure"></a>Para fazer uma variável visível somente dentro de um procedimento  
  
-   Coloque o `Dim` instrução para a variável dentro do procedimento, mas fora de qualquer bloco (como um `With`... `End With` bloco).  
  
     Você pode fazer referência à variável apenas de dentro do procedimento, inclusive dentro de qualquer bloco contido no procedimento.  
  
## <a name="scope-at-module-or-namespace-level"></a>Escopo no nível de Namespace ou módulo  
 Para sua conveniência, o termo simples *nível de módulo* se aplica igualmente a módulos, classes e estruturas. O nível de acesso de uma variável de nível de módulo determina seu escopo. O namespace que contém o módulo, classe ou estrutura também influencia o escopo.  
  
#### <a name="to-make-a-variable-visible-throughout-a-module-class-or-structure"></a>Para tornar uma variável visível em um módulo, classe ou estrutura  
  
1.  Coloque o `Dim` instrução para a variável dentro do módulo, classe ou estrutura, mas fora de qualquer procedimento.  
  
2.  Incluir o [privados](../../../../visual-basic/language-reference/modifiers/private.md) palavra-chave no `Dim` instrução.  
  
3.  Você pode fazer referência à variável de qualquer lugar dentro do módulo, classe ou estrutura, mas não de fora dela.  
  
#### <a name="to-make-a-variable-visible-throughout-a-namespace"></a>Para tornar uma variável visível em um namespace  
  
1.  Coloque o `Dim` instrução para a variável dentro do módulo, classe ou estrutura, mas fora de qualquer procedimento.  
  
2.  Incluir o [amigo](../../../../visual-basic/language-reference/modifiers/friend.md) ou [pública](../../../../visual-basic/language-reference/modifiers/public.md) palavra-chave no `Dim` instrução.  
  
3.  Você pode fazer referência à variável de qualquer lugar dentro do namespace que contém o módulo, classe ou estrutura.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir declara uma variável no nível de módulo e limita sua visibilidade ao código dentro do módulo.  
  
```  
Module demonstrateScope  
    Private strMsg As String  
    Sub initializePrivateVariable()  
        strMsg = "This variable cannot be used outside this module."  
    End Sub  
    Sub usePrivateVariable()  
        MsgBox(strMsg)  
    End Sub  
End Module  
```  
  
 No exemplo anterior, todos os procedimentos definidos no módulo `demonstrateScope` pode se referir a `String` variável `strMsg`. Quando o `usePrivateVariable` procedimento é chamado, ele exibe o conteúdo da variável de cadeia de caracteres `strMsg` em uma caixa de diálogo.  
  
 Com a seguinte alteração ao exemplo anterior, a variável de cadeia de caracteres `strMsg` pode ser chamada pelo código em qualquer lugar no namespace da sua declaração.  
  
```  
Public strMsg As String  
```  
  
## <a name="robust-programming"></a>Programação robusta  
 Quanto mais estreito o escopo de uma variável, e menos oportunidades que você tem para se referir acidentalmente a ele no lugar de outra variável com o mesmo nome. Você também pode minimizar problemas de referência correspondente.  
  
## <a name="net-framework-security"></a>Segurança do .NET Framework  
 Quanto mais estreito o escopo de uma variável, menores as chances de que um código mal-intencionado pode fazer inadequado usá-lo.  
  
## <a name="see-also"></a>Consulte também

- [Escopo no Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
- [Tempo de vida no Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)
- [Níveis de acesso no Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [Variáveis](../../../../visual-basic/programming-guide/language-features/variables/index.md)
- [Declaração de Variável](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [Instrução Dim](../../../../visual-basic/language-reference/statements/dim-statement.md)
