---
title: Protegido (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.Protected
helpviewer_keywords:
- Protected Friend keyword combination
- Protected keyword [Visual Basic], and Friend
- Protected keyword [Visual Basic], syntax
- Protected access modifier
- Protected keyword [Visual Basic]
ms.assetid: 74ad3d56-309f-49d2-b60c-1d0157d010e8
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2d0cc7a0cb626a9ec8e2a0e47abc02e5268aed56
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="protected-visual-basic"></a>Protegido (Visual Basic)
Especifica que um ou mais elementos de programação declarados são acessíveis somente de dentro de sua própria classe ou de uma classe derivada.  
  
## <a name="remarks"></a>Comentários  
 Às vezes, um elemento de programação declarado em uma classe contém dados confidenciais ou código restrito, e você deseja limitar o acesso ao elemento. No entanto, se a classe é herdável e você espera uma hierarquia de classes derivadas, pode ser necessário para essas classes derivadas acessar os dados ou código. Nesse caso, você deseja que o elemento para ser acessível da classe base e de todas as classes derivadas. Para limitar o acesso a um elemento dessa maneira, você pode declará-la com `Protected`.  
  
## <a name="rules"></a>Regras  
  
-   **Contexto de declaração.** Você pode usar `Protected` somente no nível de classe. Isso significa que o contexto da declaração para um `Protected` elemento deve ser uma classe e não pode ser um arquivo de origem, namespace, interface, módulo, estrutura ou procedimento.  
  
-   **Modificadores combinados.** Você pode usar o `Protected` modificador junto com o [Friend](../../../visual-basic/language-reference/modifiers/friend.md) modificador na mesma declaração. Essa combinação torna os elementos declarados acessíveis de qualquer lugar no mesmo assembly, de sua própria classe e de classes derivadas. Você pode especificar `Protected Friend` somente em membros de classes.  
  
## <a name="behavior"></a>Comportamento  
  
-   **Nível de acesso.** Todo o código em uma classe pode acessar seus elementos. O código em qualquer classe que deriva de uma classe base pode acessar todos os `Protected` elementos da classe base. Isso é verdadeiro para todas as gerações de derivação. Isso significa que uma classe pode acessar `Protected` elementos da classe base da classe base e assim por diante.  
  
     Acesso protegido não é um superconjunto ou subconjunto de acesso friend.  
  
-   **Modificadores de acesso.** As palavras-chave que especificam o nível de acesso são chamadas *modificadores de acesso*. Para uma comparação entre os modificadores de acesso, consulte [acessar níveis no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
 O `Protected` modificador pode ser usado nesses contextos:  
  
 [Instrução Class](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [Instrução Const](../../../visual-basic/language-reference/statements/const-statement.md)  
  
 [Instrução Declare](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [Instrução Delegate](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [Instrução Dim](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [Instrução Enum](../../../visual-basic/language-reference/statements/enum-statement.md)  
  
 [Instrução Event](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [Instrução Function](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Instrução Interface](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [Instrução Property](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Instrução Structure](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [Instrução Sub](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>Consulte também  
 [Público](../../../visual-basic/language-reference/modifiers/public.md)  
 [Friend](../../../visual-basic/language-reference/modifiers/friend.md)  
 [Privado](../../../visual-basic/language-reference/modifiers/private.md)  
 [Níveis de acesso no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)  
 [Procedimentos](../../../visual-basic/programming-guide/language-features/procedures/index.md)  
 [Estruturas](../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [Objetos e Classes](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
