---
title: Protegido (Visual Basic) | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Protected
dev_langs:
- VB
helpviewer_keywords:
- Protected Friend keyword combination
- Protected keyword, and Friend
- Protected keyword, syntax
- Protected access modifier
- Protected keyword
ms.assetid: 74ad3d56-309f-49d2-b60c-1d0157d010e8
caps.latest.revision: 16
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: a063845f7135e993f635d36df1bf460811d04846
ms.lasthandoff: 03/13/2017

---
# <a name="protected-visual-basic"></a>Protegido (Visual Basic)
Especifica que um ou mais elementos de programação declarados são acessíveis somente de dentro da sua própria classe ou de uma classe derivada.  
  
## <a name="remarks"></a>Comentários  
 Às vezes, um elemento de programação declarado em uma classe contém dados confidenciais ou código restrito, e você deseja limitar o acesso ao elemento. No entanto, se a classe é herdável e você espera uma hierarquia de classes derivadas, pode ser necessário para essas classes derivadas acessar os dados ou código. Nesse caso, você deseja que o elemento seja acessível tanto da classe base de todas as classes derivadas. Para limitar o acesso a um elemento dessa maneira, você pode declará-lo com `Protected`.  
  
## <a name="rules"></a>Regras  
  
-   **Contexto de declaração.** Você pode usar `Protected` somente no nível de classe. Isso significa que o contexto da declaração para um `Protected` elemento deve ser uma classe e não pode ser um arquivo fonte, namespace, interface, módulo, estrutura ou procedimento.  
  
-   **Modificadores combinados.** Você pode usar o `Protected` modificador junto com o [amigo](../../../visual-basic/language-reference/modifiers/friend.md) modificador na mesma declaração. Essa combinação torna os elementos declarados acessíveis a partir de qualquer lugar no mesmo assembly, de sua própria classe e de classes derivadas. Você pode especificar `Protected Friend` somente em membros de classes.  
  
## <a name="behavior"></a>Comportamento  
  
-   **Nível de acesso.** Todo o código em uma classe pode acessar seus elementos. Código em qualquer classe que deriva de uma classe base pode acessar todos os `Protected` elementos da classe base. Isso é verdadeiro para todas as gerações de derivação. Isso significa que uma classe pode acessar `Protected` elementos da classe base da classe base e assim por diante.  
  
     Acesso protegido não é um superconjunto ou subconjunto de acesso amigo.  
  
-   **Modificadores de acesso.** As palavras-chave que especificam o nível de acesso são chamadas *modificadores de acesso*. Para uma comparação entre os modificadores de acesso, consulte [níveis de acesso no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
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
