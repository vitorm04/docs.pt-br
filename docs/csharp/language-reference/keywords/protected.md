---
title: "protected (Refer&#234;ncia de C#) | Microsoft Docs"
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
  - "protected"
  - "protected_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "palavra-chave protected [C#]"
ms.assetid: 05ce3794-6675-4025-bddb-eaaa0ec22892
caps.latest.revision: 20
caps.handback.revision: 20
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# protected (Refer&#234;ncia de C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

O `protected` palavra\-chave é um modificador de acesso de membro.  Um membro protegido é acessível dentro de sua classe e por instâncias da classe derivada.  Para obter uma comparação de `protected` com os outros modificadores de acesso, consulte  [Níveis de acessibilidade](../../../csharp/language-reference/keywords/accessibility-levels.md).  
  
## Exemplo  
 Um membro protegido de uma classe base está acessível em uma classe derivada, somente se o acesso ocorre através do tipo de classe derivada.  Por exemplo, considere o segmento de código a seguir:  
  
 [!code-cs[csrefKeywordsModifiers#11](../../../csharp/language-reference/keywords/codesnippet/CSharp/protected_1.cs)]  
  
 A instrução `a.x = 10` gera um erro porque ele é feito dentro do método estático principal, e não uma instância da classe b.  
  
 Membros struct não podem ser protegidos porque a estrutura não pode ser herdada.  
  
## Exemplo  
 Neste exemplo, a classe `DerivedPoint` é derivada de `Point`.  Portanto, você pode acessar os membros protegidos da classe base diretamente da classe derivada.  
  
 [!code-cs[csrefKeywordsModifiers#12](../../../csharp/language-reference/keywords/codesnippet/CSharp/protected_2.cs)]  
  
 Se você alterar os níveis de acesso de `x` e `y` para [Particular](../../../csharp/language-reference/keywords/private.md), o compilador emitirá as mensagens de erro:  
  
 `'Point.y' is inaccessible due to its protection level.`  
  
 `'Point.x' is inaccessible due to its protection level.`  
  
## Especificação da linguagem C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## Consulte também  
 [Referência de C\#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Palavras\-chave C\#](../../../csharp/language-reference/keywords/index.md)   
 [Modificadores de acesso](../../../csharp/language-reference/keywords/access-modifiers.md)   
 [Níveis de acessibilidade](../../../csharp/language-reference/keywords/accessibility-levels.md)   
 [Modificadores](../../../csharp/language-reference/keywords/modifiers.md)   
 [public](../../../csharp/language-reference/keywords/public.md)   
 [private](../../../csharp/language-reference/keywords/private.md)   
 [internal](../../../csharp/language-reference/keywords/internal.md)