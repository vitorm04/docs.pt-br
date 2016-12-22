---
title: "namespace (Refer&#234;ncia de C#) | Microsoft Docs"
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
  - "namespace_CSharpKeyword"
  - "namespace"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "palavra-chave namespace [C#]"
  - "escopo [C#]"
ms.assetid: 0a788423-9110-42e0-97d9-bda41ca4870f
caps.latest.revision: 28
caps.handback.revision: 28
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# namespace (Refer&#234;ncia de C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

A palavra\-chave de `namespace` é usada para declarar um escopo que contém um conjunto de objetos relacionados.  Você pode usar um namespace para organizar elementos de código e para criar globalmente tipos exclusivos.  
  
 [!code-cs[csrefKeywordsNamespace#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/namespace_1.cs)]  
  
## Comentários  
 Dentro de um namespace, você pode declarar um ou mais dos seguintes tipos:  
  
-   namespace  
  
-   [classe](../../../csharp/language-reference/keywords/class.md)  
  
-   [interface](../../../csharp/language-reference/keywords/interface.md)  
  
-   [estrutura](../../../csharp/language-reference/keywords/struct.md)  
  
-   [enum](../../../csharp/language-reference/keywords/enum.md)  
  
-   [delegado](../../../csharp/language-reference/keywords/delegate.md)  
  
 Mesmo se você declarar explicitamente um namespace em um arquivo de origem C\#, o compilador adiciona um namespace padrão.  Este namespace sem nome, às vezes conhecida como o namespace global, está presente em cada arquivo.  Qualquer identificador no namespace global está disponível para uso em um namespace chamado.  
  
 Namespaces implicitamente têm acesso público e isso é não modificável.  Para uma discussão dos modificadores de acesso que você pode atribuir a elementos em um namespace, consulte [Modificadores de acesso](../../../csharp/language-reference/keywords/access-modifiers.md).  
  
 É possível definir um namespace em dois ou mais declarações.  Por exemplo, o exemplo define duas classes como parte do namespace de `MyCompany` :  
  
 [!code-cs[csrefKeywordsNamespace#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/namespace_2.cs)]  
  
## Exemplo  
 O exemplo a seguir mostra como chamar um método estático em um namespace aninhado.  
  
 [!code-cs[csrefKeywordsNamespace#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/namespace_3.cs)]  
  
## Para obter mais informações  
 Para obter mais informações sobre como usar namespaces, consulte os seguintes tópicos:  
  
-   [Namespaces](../../../csharp/programming-guide/namespaces/index.md)  
  
-   [Usando namespaces](../../../csharp/programming-guide/namespaces/using-namespaces.md)  
  
-   [Como usar o alias de namespace global](../../../csharp/programming-guide/namespaces/how-to-use-the-global-namespace-alias.md)  
  
## Especificação da linguagem C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## Consulte também  
 [Referência de C\#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Palavras\-chave C\#](../../../csharp/language-reference/keywords/index.md)   
 [Palavras\-chave de namespace](../../../csharp/language-reference/keywords/namespace-keywords.md)   
 [using](../../../csharp/language-reference/keywords/using.md)