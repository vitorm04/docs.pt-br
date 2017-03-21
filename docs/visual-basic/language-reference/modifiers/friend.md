---
title: Friend (Visual Basic) | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Friend
dev_langs:
- VB
helpviewer_keywords:
- Friend keyword
- Friend access modifier
- Friend keyword, syntax
- Protected Friend keyword combination
- Friend keyword, and Protected
ms.assetid: b664605e-1c79-4728-b996-aa59c50846bc
caps.latest.revision: 25
author: stevehoag
ms.author: shoag
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 99ed467fc6430084f3a7d853a08e5f94be0cd530
ms.lasthandoff: 03/13/2017

---
# <a name="friend-visual-basic"></a>Friend (Visual Basic)
Especifica que um ou mais elementos de programação declarados são acessíveis somente a partir de dentro do assembly que contém sua declaração.  
  
## <a name="remarks"></a>Comentários  
 Em muitos casos, você deseja programar elementos como classes e estruturas para ser usado pelo assembly inteiro, não apenas pelo componente que declara-los. No entanto, você talvez não queira estejam acessíveis pelo código fora do assembly (por exemplo, se o aplicativo é proprietário). Se você quiser limitar o acesso a um elemento dessa maneira, você pode declará-lo usando o `Friend` modificador.  
  
 Código em outras classes, estruturas e módulos são compilados no mesmo assembly pode acessar todos os `Friend` elementos nesse assembly.  
  
 `Friend`acesso geralmente é o nível de preferência para elementos de programação do aplicativo, e `Friend` é o acesso padrão em nível de uma interface, um módulo, uma classe ou uma estrutura.  
  
 Você pode usar `Friend` somente no nível de namespace ou módulo. Portanto, o contexto da declaração para um `Friend` elemento deve ser um arquivo de origem, um namespace, uma interface, um módulo, uma classe ou uma estrutura; não pode ser um procedimento.  
  
 Você pode usar o `Friend` modificador em conjunto com o [protegido](../../../visual-basic/language-reference/modifiers/protected.md) modificador na mesma declaração. Essa combinação confere ambos `Friend` acesso e protegidos nos elementos declarados, para que sejam acessíveis a partir de qualquer lugar no mesmo assembly, de sua própria classe e de classes derivadas. Você pode especificar `Protected Friend` somente em membros de classes.  
  
 Para obter uma comparação de `Friend` e outros modificadores de acesso, consulte [níveis de acesso no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
> [!NOTE]
>  Você pode especificar outro assembly é um assembly de amigo, que permite acessar todos os tipos e membros que são marcados como `Friend`. Para obter mais informações, consulte [Assemblies amigáveis](http://msdn.microsoft.com/library/df0c70ea-2c2a-4bdc-9526-df951ad2d055).  
  
## <a name="example"></a>Exemplo  
 A classe a seguir usa o `Friend` modificador para permitir que outros elementos de programação dentro do mesmo assembly para acessar determinados membros.  
  
 [!code-vb[VbVbalrAccessModifiers n º&1;](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/friend_1.vb)]  
  
## <a name="usage"></a>Uso  
 Você pode usar o `Friend` modificador nestes contextos:  
  
 [Instrução Class](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [Instrução Const](../../../visual-basic/language-reference/statements/const-statement.md)  
  
 [Instrução Declare](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [Instrução Delegate](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [Instrução Dim](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [Instrução Enum](../../../visual-basic/language-reference/statements/enum-statement.md)  
  
 [Instrução Event](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [Instrução Function](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Instrução Interface](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [Instrução Module](../../../visual-basic/language-reference/statements/module-statement.md)  
  
 [Instrução Property](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Instrução Structure](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [Instrução Sub](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute></xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>   
 [Público](../../../visual-basic/language-reference/modifiers/public.md)   
 [Protegido](../../../visual-basic/language-reference/modifiers/protected.md)   
 [Privado](../../../visual-basic/language-reference/modifiers/private.md)   
 [Níveis de acesso no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)   
 [Procedimentos](../../../visual-basic/programming-guide/language-features/procedures/index.md)   
 [Estruturas](../../../visual-basic/programming-guide/language-features/data-types/structures.md)   
 [Objetos e Classes](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
