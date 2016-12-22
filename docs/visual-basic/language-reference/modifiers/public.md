---
title: "P&#250;blico (Visual Basic) | Microsoft Docs"
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
  - "vb.Public"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Modificador de acesso público"
  - "palavra-chave Public"
  - "palavra-chave Public, sintaxe"
ms.assetid: 284c9e1b-ed23-499b-9bc9-ad87c11485a5
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# P&#250;blico (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Especifica que um ou mais elementos de programação declarados não têm nenhuma restrição de acesso.  
  
## Comentários  
 Se você estiver publicando um componente ou conjunto de componentes, como uma biblioteca de classes, geralmente é desejado que os elementos de programação sejam acessível a qualquer código que interopera com o conjunto de módulos \(assembly\).  Para concede tal acesso ilimitado em um elemento, você pode declará\-lo com `Public`.  
  
 Acesso público é o nível normal para um elemento de programação quando não é necessário limitar o acesso a ele.  Observe que o nível de acesso de um elemento declarado em uma interface, módulo, de classe ou estrutura padrão é `Public` se você não declarar o contrário.  
  
## Regras  
  
-   **Contexto da Declaração.** Você pode usar `Public` somente em nível de namespace ou módulo.  Isso significa que o contexto da declaração para um elemento `Public` deve ser uma classe, módulo, arquivo fonte, namespace, interface ou estrutura, e não um procedimento.  
  
## Comportamento  
  
-   **Nível de acesso.** Todo o código que pode acessar um módulo, classe ou estrutura pode acessar seu `Public` elementos.  
  
-   **Acesso padrão.** Variáveis locais dentro de um procedimento são de acesso público por padrão, e você não pode usar nenhum modifciador de acesso neles.  
  
-   **Modificadores de acesso.** As palavras\-chave que especificam o nível de acesso são chamadas  *modificadores*  acesso.  Para uma comparação entre os modificadores de acesso, consulte [Níveis de acesso no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
 O modificador `Public` pode ser utilizado nestes contextos:  
  
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
  
 [Declaração Operator](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
 [Propriedade declaração](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Instrução Structure](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [Instrução Sub](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## Consulte também  
 [Protegido](../../../visual-basic/language-reference/modifiers/protected.md)   
 [Friend](../../../visual-basic/language-reference/modifiers/friend.md)   
 [Particular](../../../visual-basic/language-reference/modifiers/private.md)   
 [Níveis de acesso no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)   
 [Procedimentos](../../../visual-basic/programming-guide/language-features/procedures/index.md)   
 [Estruturas](../../../visual-basic/programming-guide/language-features/data-types/structures.md)   
 [Objetos e classes](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)