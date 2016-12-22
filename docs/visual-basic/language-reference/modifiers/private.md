---
title: "Particular (Visual Basic) | Microsoft Docs"
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
  - "vb.Private"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "palavra-chave Private"
  - "palavra-chave Private, sintaxe"
ms.assetid: aba74a2e-5824-4613-bf63-b9ec7787f4e6
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Particular (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Especifica que um ou mais elementos de programação declarados são acessíveis somente a partir de seus contextos de declaração, inclusive em todos os tipos contidos.  
  
## Comentários  
 Se um elemento de programação representa funcionalidade proprietária, ou contém dados confidenciais, você geralmente deseja limitar o acesso a ele para ser tão restrito quanto possível.  Você obtém o limite máximo, permitindo que somente o módulo, de classe ou estrutura que o define acesse\-o.  Para limitar o acesso a um elemento dessa maneira, você pode declará\-lo com `Private`.  
  
## Regras  
  
-   **Contexto da Declaração.** Você pode usar `Private` somente no nível de módulo.  Isso significa que o contexto da declaração para um elemento `Private` deve ser uma classe, módulo, ou estrutura, e não pode ser um arquivo\-fonte, namespace, interface ou procedimento.  
  
## Comportamento  
  
-   **Nível de acesso.** Todo o código dentro de um contexto de declaração pode acessar seus `Private` elementos.  Isso inclui o código dentro de um tipo contido, como um classe aninhada ou uma expressão de atribuição de uma enumeração.  Nenhum código fora do contexto da declaração pode acessar seus elementos `Private`.  
  
-   **Modificadores de acesso.** As palavras\-chave que especificam o nível de acesso são chamadas  *modificadores*  acesso.  Para uma comparação entre os modificadores de acesso, consulte [Níveis de acesso no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
 O modificador `Private` pode ser utilizado nestes contextos:  
  
 [Declaração de Classe](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [Declaração Const](../../../visual-basic/language-reference/statements/const-statement.md)  
  
 [Instrução Declare](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [Instrução Delegate](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [Esmaecer declaração](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [Declaração Enum](../../../visual-basic/language-reference/statements/enum-statement.md)  
  
 [Declaração de evento](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [Instrução função](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Interface declaração](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [Propriedade declaração](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Instrução Structure](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [Instrução Sub](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## Consulte também  
 [Público](../../../visual-basic/language-reference/modifiers/public.md)   
 [Protegido](../../../visual-basic/language-reference/modifiers/protected.md)   
 [Friend](../../../visual-basic/language-reference/modifiers/friend.md)   
 [Níveis de acesso no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)   
 [Procedimentos](../../../visual-basic/programming-guide/language-features/procedures/index.md)   
 [Estruturas](../../../visual-basic/programming-guide/language-features/data-types/structures.md)   
 [Objetos e classes](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)