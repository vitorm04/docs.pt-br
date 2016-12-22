---
title: "public (Refer&#234;ncia de C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "public"
  - "public_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "palavra-chave public [C#]"
ms.assetid: 0ae45d16-a551-4b74-9845-57208de1328e
caps.latest.revision: 21
caps.handback.revision: 21
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# public (Refer&#234;ncia de C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

O `public` palavra\-chave é um modificador de acesso para tipos e membros de tipo.  Acesso público é o nível de acesso mais permissivo.  Existem há restrições para acessar membros públicos, como, neste exemplo:  
  
```  
class SampleClass  
{  
    public int x; // No access restrictions.  
}  
```  
  
 Consulte [Modificadores de acesso](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md) e [Níveis de acessibilidade](../../../csharp/language-reference/keywords/accessibility-levels.md) para mais informações.  
  
## Exemplo  
 No exemplo a seguir, duas classes são declaradas, `PointTest` e `MainClass`.  Membros públicos `x` e `y` de `PointTest` são acessados diretamente pelo `MainClass`.  
  
 [!code-cs[csrefKeywordsModifiers#13](../../../csharp/language-reference/keywords/codesnippet/CSharp/public_1.cs)]  
  
 Se você alterar o `public` nível de acesso para  [particular](../../../csharp/language-reference/keywords/private.md) ou  [protegido](../../../csharp/language-reference/keywords/protected.md), você receberá a mensagem de erro:  
  
 'PointTest.y' está inacessível devido ao seu nível de proteção.  
  
## Especificação da linguagem C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## Consulte também  
 [Referência de C\#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Modificadores de acesso](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)   
 [Palavras\-chave C\#](../../../csharp/language-reference/keywords/index.md)   
 [Modificadores de acesso](../../../csharp/language-reference/keywords/access-modifiers.md)   
 [Níveis de acessibilidade](../../../csharp/language-reference/keywords/accessibility-levels.md)   
 [Modificadores](../../../csharp/language-reference/keywords/modifiers.md)   
 [private](../../../csharp/language-reference/keywords/private.md)   
 [protected](../../../csharp/language-reference/keywords/protected.md)   
 [internal](../../../csharp/language-reference/keywords/internal.md)