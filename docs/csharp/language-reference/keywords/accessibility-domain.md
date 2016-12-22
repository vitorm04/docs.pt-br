---
title: "Dom&#237;nio de acessibilidade (Refer&#234;ncia de C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "domínio de acessibilidade [C#]"
ms.assetid: 8af779c1-275b-44be-a864-9edfbca71bcc
caps.latest.revision: 17
caps.handback.revision: 17
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Dom&#237;nio de acessibilidade (Refer&#234;ncia de C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

O domínio de acessibilidade de um membro Especifica quais seções do programa membro pode ser referenciado.  Se o membro estiver aninhado em outro tipo, o seu domínio de acessibilidade é determinado por ambas as  [o nível de acessibilidade](../../../csharp/language-reference/keywords/accessibility-levels.md) o membro e o domínio de acessibilidade do tipo imediatamente contido.  
  
 O domínio de acessibilidade de um tipo de nível superior é pelo menos o texto do programa do que ele seja declarado no projeto.  Ou seja, o domínio inclui todos os arquivos de origem deste projeto.  O domínio de acessibilidade de um tipo aninhado é pelo menos o texto do programa do tipo no qual é declarada.  Ou seja, o domínio é o corpo de tipo, que inclui todos os tipos aninhados.  O domínio de acessibilidade de um tipo aninhado nunca excede do tipo recipiente.  Esses conceitos são demonstrados no exemplo a seguir.  
  
## Exemplo  
 Este exemplo contém um tipo de nível superior, `T1`e duas classes aninhadas, `M1` e `M2`.  As classes contêm campos que tenham diferentes acessibilidade declarada.  No `Main` método, um comentário acompanhar cada instrução para indicar o domínio de acessibilidade de cada membro.  Observe que as instruções que tentam referenciar membros inacessíveis são comentadas.  Se você quiser ver os erros de compilador causados pela referência de um membro inacessível, remova os comentários de um por vez.  
  
 [!code-cs[csrefKeywordsModifiers#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/accessibility-domain_1.cs)]  
  
## Especificação da linguagem C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## Consulte também  
 [Referência de C\#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Palavras\-chave C\#](../../../csharp/language-reference/keywords/index.md)   
 [Modificadores de acesso](../../../csharp/language-reference/keywords/access-modifiers.md)   
 [Níveis de acessibilidade](../../../csharp/language-reference/keywords/accessibility-levels.md)   
 [Restrições ao uso de níveis de acessibilidade](../../../csharp/language-reference/keywords/restrictions-on-using-accessibility-levels.md)   
 [Modificadores de acesso](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)   
 [public](../../../csharp/language-reference/keywords/public.md)   
 [private](../../../csharp/language-reference/keywords/private.md)   
 [protected](../../../csharp/language-reference/keywords/protected.md)   
 [internal](../../../csharp/language-reference/keywords/internal.md)