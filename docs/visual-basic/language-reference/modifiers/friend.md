---
title: Friend (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.Friend
helpviewer_keywords:
- Friend keyword [Visual Basic]
- Friend access modifier
- Friend keyword [Visual Basic], syntax
- Protected Friend keyword combination
- Friend keyword [Visual Basic], and Protected
ms.assetid: b664605e-1c79-4728-b996-aa59c50846bc
caps.latest.revision: "25"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: df0e8ad1990fe7a1aa495e1794c942813cffb5bc
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/21/2017
---
# <a name="friend-visual-basic"></a>Friend (Visual Basic)
Especifica que um ou mais elementos de programação declarados são acessíveis somente de dentro do assembly que contém sua declaração.  
  
## <a name="remarks"></a>Comentários  
 Em muitos casos, você deseja a programação de elementos, como classes e estruturas para ser usado pelo conjunto inteiro, não apenas pelo componente que declara. No entanto, talvez não seja a ser acessado pelo código fora do assembly (por exemplo, se o aplicativo é proprietário). Se você quiser limitar o acesso a um elemento dessa maneira, você pode declará-lo usando o `Friend` modificador.  
  
 Código de outras classes, estruturas e módulos que são compilados para o mesmo assembly pode acessar todos os `Friend` elementos nesse assembly.  
  
 `Friend`acesso geralmente é o nível preferido para elementos de programação do aplicativo, e `Friend` é o acesso padrão em nível de uma interface, um módulo, uma classe ou uma estrutura.  
  
 Você pode usar `Friend` somente no nível de namespace ou módulo. Portanto, o contexto da declaração para um `Friend` elemento deve ser um arquivo de origem, um namespace, uma interface, um módulo, uma classe ou uma estrutura; ele não pode ser um procedimento.  
  
 Você pode usar o `Friend` modificador em conjunto com o [protegidos](../../../visual-basic/language-reference/modifiers/protected.md) modificador na mesma declaração. Essa combinação confere ambos `Friend` acesso e protegidos nos elementos declarados, para que eles são acessíveis de qualquer lugar no mesmo assembly, de sua própria classe e de classes derivadas. Você pode especificar `Protected Friend` somente em membros de classes.  
  
 Para obter uma comparação de `Friend` e outros modificadores de acesso, consulte [acessar níveis no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
> [!NOTE]
>  Você pode especificar outro assembly é um assembly friend, que permite acessar todos os tipos e membros que são marcados como `Friend`. Para obter mais informações, consulte [Assemblies amigáveis](../../programming-guide/concepts/assemblies-gac/friend-assemblies.md).  
  
## <a name="example"></a>Exemplo  
 A seguinte classe usa a `Friend` modificador para permitir que outros elementos de programação dentro do mesmo assembly para acessar determinados membros.  
  
 [!code-vb[VbVbalrAccessModifiers#1](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/friend_1.vb)]  
  
## <a name="usage"></a>Uso  
 Você pode usar o `Friend` modificador nesses contextos:  
  
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
 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>  
 [Público](../../../visual-basic/language-reference/modifiers/public.md)  
 [Protegido](../../../visual-basic/language-reference/modifiers/protected.md)  
 [Privado](../../../visual-basic/language-reference/modifiers/private.md)  
 [Níveis de acesso no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)  
 [Procedimentos](../../../visual-basic/programming-guide/language-features/procedures/index.md)  
 [Estruturas](../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [Objetos e Classes](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
