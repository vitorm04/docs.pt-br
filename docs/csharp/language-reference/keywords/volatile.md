---
title: "volatile (Refer&#234;ncia de C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "volatile_CSharpKeyword"
  - "volatile"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "palavra-chave volatile [C#]"
ms.assetid: 78089bc7-7b38-4cfd-9e49-87ac036af009
caps.latest.revision: 29
caps.handback.revision: 29
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# volatile (Refer&#234;ncia de C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

O `volatile` palavra\-chave indica que um campo pode ser modificado por vários segmentos que estão em execução ao mesmo tempo.  Os campos que são declarados `volatile` são não sujeitas a otimizações do compilador que assumem o acesso por um único thread.  Isso garante que o valor mais atualizado está presente no campo em todos os momentos.  
  
 O `volatile` modificador geralmente é usado para um campo que é acessado por vários threads sem usar o  [lock](../../../csharp/language-reference/keywords/lock-statement.md) instrução para serializar o acesso.  
  
 O `volatile` palavra\-chave pode ser aplicado a campos desses tipos:  
  
-   Tipos de referência.  
  
-   Tipos de ponteiro \(em um contexto sem segurança\).  Observe que embora o ponteiro em si pode ser volátil, o objeto ao qual ele aponta não pode.  Em outras palavras, você não pode declarar um "ponteiro para volátil".  
  
-   Tipos como, por exemplo, sbyte, byte, short, ushort, int, uint, char, float e bool.  
  
-   Um tipo enum com um dos seguintes tipos de base: byte, sbyte, short, ushort, int ou uint.  
  
-   Parâmetros de tipo genérico conhecidos como tipos de referência.  
  
-   <xref:System.IntPtr> e <xref:System.UIntPtr>.  
  
 A palavra\-chave volátil só pode ser aplicada aos campos de uma classe ou struct.  Variáveis locais não podem ser declaradas `volatile`.  
  
## Exemplo  
 O exemplo a seguir mostra como declarar uma variavel como um campo público `volatile`.  
  
 [!code-cs[csrefKeywordsModifiers#24](../../../csharp/language-reference/keywords/codesnippet/CSharp/volatile_1.cs)]  
  
## Exemplo  
 O exemplo a seguir demonstra como um segmento auxiliar ou de trabalho pode ser criado e usado para executar o processamento em paralelo com o do segmento primário.  Para obter informações detalhadas sobre consulte multithreading, [Threading](../Topic/Managed%20Threading.md) e [Threading](../Topic/Threading%20\(C%23%20and%20Visual%20Basic\).md).  
  
 [!CODE [csProgGuideThreading#1](../CodeSnippet/VS_Snippets_VBCSharp/csProgGuideThreading#1)]  
  
## Especificação da linguagem C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## Consulte também  
 [Referência de C\#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Palavras\-chave C\#](../../../csharp/language-reference/keywords/index.md)   
 [Modificadores](../../../csharp/language-reference/keywords/modifiers.md)