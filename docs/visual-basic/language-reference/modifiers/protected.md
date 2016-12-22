---
title: "Protegido (Visual Basic) | Microsoft Docs"
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
  - "vb.Protected"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Modificador de acesso protegido"
  - "combinação de palavra-chave Protected Friend"
  - "palavra-chave Protected"
  - "palavra-chave Protected, e Friend"
  - "palavra-chave Protected, sintaxe"
ms.assetid: 74ad3d56-309f-49d2-b60c-1d0157d010e8
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Protegido (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Especifica que um ou mais elementos de programação declarados são acessíveis somente a partir dentro sua própria classe ou de um classe derivada.  
  
## Comentários  
 Às vezes, um elemento de programação declarado em uma classe contém dados confidenciais ou código restrito, e você deseja limitar o acesso ao elemento.  No entanto, se a classe é herdável e você espera uma hierarquia de classes derivadas, talvez seja necessário para essas classes derivadas  acessar os dados ou código.  Em casos como esse, você deseja que o elemento seja acessível tanto da classe base quanto de todas as classes derivadas.  Para limitar o acesso a um elemento dessa maneira, você pode declará\-la com `Protected`.  
  
## Regras  
  
-   **Contexto da Declaração.** Você pode usar `Protected` somente no nível de classe.  Isso significa que o contexto da declaração para um elemento `Protected` deve ser uma classe ou estrutura, e não um arquivo fonte, namespace, interface, módulo, estrutura ou procedimento.  
  
-   **Modificadores Combinados.** Você pode usar o `Protected` modificador juntamente com o [Friend](../../../visual-basic/language-reference/modifiers/friend.md) modificador na mesma declaração.  Essa combinação torna os elementos declarados acessíveis em qualquer lugar no mesmo assembly, de sua própria classe e de classes derivadas.  Você pode especificar `Protected Friend` somente em membros de classes.  
  
## Comportamento  
  
-   **Nível de acesso.** Todo código em uma classe pode acessar seus elementos.  Código em qualquer classe que deriva de uma classe base pode acessar todos os elementos `Protected` da classe base.  Isso é verdadeiro para todas as gerações de derivação.  Isso significa que uma classe pode acessar elementos `Protected` de classe base da classe base e assim por diante.  
  
     Não protegido de acesso é um superconjunto ou subconjunto de acesso amigo.  
  
-   **Modificadores de acesso.** As palavras\-chave que especificam o nível de acesso são chamadas  *modificadores*  acesso.  Para uma comparação entre os modificadores de acesso, consulte [Níveis de acesso no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
 O modificador `Protected` pode ser utilizado nestes contextos:  
  
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
 [Friend](../../../visual-basic/language-reference/modifiers/friend.md)   
 [Particular](../../../visual-basic/language-reference/modifiers/private.md)   
 [Níveis de acesso no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)   
 [Procedimentos](../../../visual-basic/programming-guide/language-features/procedures/index.md)   
 [Estruturas](../../../visual-basic/programming-guide/language-features/data-types/structures.md)   
 [Objetos e classes](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)