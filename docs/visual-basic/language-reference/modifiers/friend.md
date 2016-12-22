---
title: "Friend (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.Friend"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "palavra-chave Friend"
  - "modificador de acesso Friend"
  - "Palavra-chave Friend, sintaxe"
  - "combinação de palavra-chave Protected Friend"
  - "Palavra-chave Friend e protegido"
ms.assetid: b664605e-1c79-4728-b996-aa59c50846bc
caps.latest.revision: 25
caps.handback.revision: 25
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Friend (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Especifica que um ou mais elementos de programação declarados só podem ser acessados no assembly que contém sua declaração.  
  
## Comentários  
 Em muitos casos, você deseja que os elementos de programação como classes e estruturas para ser usadas pelo conjunto inteiro, não apenas pelo componente que a declara.  No entanto, você não pode desejar\-los para ser acessível pelo código fora do assembly \(por exemplo, se o aplicativo é proprietário\).  Se você desejar limitar essa maneira o acesso a um elemento, você pode declará\-lo usando o modificador de `Friend` .  
  
 O código em outras classes, estruturas, módulos e que são compilados no mesmo assembly pode acessar todos os elementos de `Friend` naquele assembly.  
  
 acesso de`Friend` o nível é geralmente preferido para elementos de programação de aplicativo, e `Friend` é o nível de acesso padrão de uma interface, módulo, de classe, ou de uma estrutura.  
  
 Você pode usar `Friend` somente a interface, módulo, ou nível de namespace.  Como consequência, o contexto da declaração para um elemento de `Friend` deve ser um arquivo fonte, namespace, interface, módulo, de classe ou estrutura;, não um procedimento.  
  
 Você pode usar o modificador de `Friend` em conjunto com o modificador de [Protegido](../../../visual-basic/language-reference/modifiers/protected.md) na declaração.  Essa combinação confere ambos acesso de `Friend` e acesso protegido em elementos declarados, o que são acessíveis em qualquer lugar no mesmo assembly, de sua própria classe, e classes derivadas.  Você pode especificar `Protected Friend` somente em membros de classes.  
  
 Para uma comparação de `Friend` e outros modificadores de acesso, consulte o [Níveis de acesso no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
> [!NOTE]
>  Você pode especificar que outro assembly é um assembly autorizado, que permite que acessa todos os tipos e membros que estejam marcadas como `Friend`.  Para obter mais informações, consulte [Assemblies amigáveis](../Topic/Friend%20Assemblies%20\(C%23%20and%20Visual%20Basic\).md).  
  
## Exemplo  
 A seguinte classe usa o modificador de `Friend` para permitir que outros elementos de programação no mesmo assembly para alguns membros de acesso.  
  
 [!CODE [VbVbalrAccessModifiers#1](../CodeSnippet/VS_Snippets_VBCSharp/vbvbalraccessmodifiers#1)]  
  
## Uso  
 Você pode usar o modificador de `Friend` nestes contextos:  
  
 [Declaração de Classe](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [Declaração Const](../../../visual-basic/language-reference/statements/const-statement.md)  
  
 [Instrução Declare](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [Instrução Delegate](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [Esmaecer declaração](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [Declaração Enum](../../../visual-basic/language-reference/statements/enum-statement.md)  
  
 [Declaração de evento](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [Instrução função](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Interface declaração](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [Declaração de Módulo](../../../visual-basic/language-reference/statements/module-statement.md)  
  
 [Propriedade declaração](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Instrução Structure](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [Declaração Sub](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## Consulte também  
 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>   
 [Público](../../../visual-basic/language-reference/modifiers/public.md)   
 [Protegido](../../../visual-basic/language-reference/modifiers/protected.md)   
 [Particular](../../../visual-basic/language-reference/modifiers/private.md)   
 [Níveis de acesso no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)   
 [Procedimentos](../../../visual-basic/programming-guide/language-features/procedures/index.md)   
 [Estruturas](../../../visual-basic/programming-guide/language-features/data-types/structures.md)   
 [Objetos e classes](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)