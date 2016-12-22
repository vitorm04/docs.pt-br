---
title: "Namespaces (Guia de Programa&#231;&#227;o em C#) | Microsoft Docs"
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
  - "Linguagem C#, namespaces"
  - "namespaces [C#]"
ms.assetid: b1c4ab46-3fad-4ffa-9deb-dd50a2d8c65a
caps.latest.revision: 27
caps.handback.revision: 27
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Namespaces (Guia de Programa&#231;&#227;o em C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Os namespaces são fortemente usados na programação em C\# de duas formas.  Primeiro, o .NET framework usa os namespaces para organizar suas muitas classes, como a seguir:  
  
 [!code-cs[csProgGuide#22](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/index_1.cs)]  
  
 `System`é um espaço para nome e `Console` é uma classe no namespace.  O `using` palavra\-chave pode ser usada para que o nome completo não é necessário, como no exemplo a seguir:  
  
 [!code-cs[csProgGuide#1](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/index_2.cs)]  
  
 [!code-cs[csProgGuide#25](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/index_3.cs)]  
  
 Para obter mais informações, consulte [Diretiva de uso](../../../csharp/language-reference/keywords/using-directive.md).  
  
 Segundo, declarando seus próprios namespaces pode ajudar no controle do escopo da classe e nomes de métodos em grandes projetos de programação.  Use o  [espaço para nome](../../../csharp/language-reference/keywords/namespace.md) palavra\-chave para declarar um espaço para nome, como no exemplo a seguir:  
  
 [!code-cs[csProgGuideNamespaces#6](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/index_4.cs)]  
  
## Visão geral de namespaces  
 Namespaces possuem as seguintes propriedades:  
  
-   Eles organizam o código de grandes projetos.  
  
-   Eles são delimitados por meio do `.` operador.  
  
-   O `using directive` elimina a necessidade de especificar o nome do namespace para cada classe.  
  
-   O `global` namespace é o namespace "raiz": `global::System` sempre fará referência a.NET Framework namespace `System`.  
  
## Seções relacionadas  
 Veja os tópicos a seguir para mais informações sobre namespaces:  
  
-   [Usando namespaces](../../../csharp/programming-guide/namespaces/using-namespaces.md)  
  
-   [Como usar o alias de namespace global](../../../csharp/programming-guide/namespaces/how-to-use-the-global-namespace-alias.md)  
  
-   [Como usar o My Namespace](../../../csharp/programming-guide/namespaces/how-to-use-the-my-namespace.md)  
  
## Especificação da linguagem C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## Consulte também  
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Palavras\-chave de namespace](../../../csharp/language-reference/keywords/namespace-keywords.md)   
 [Diretiva de uso](../../../csharp/language-reference/keywords/using-directive.md)   
 [Operador ::](../Topic/::%20Operator%20\(C%23%20Reference\).md)   
 [Operador .](../../../csharp/language-reference/operators/member-access-operator.md)