---
title: "Como usar o alias de namespace global (Guia de Programa&#231;&#227;o em C#) | Microsoft Docs"
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
  - "aliases [C#]"
  - "namespace global [C#]"
  - "namespaces [C#], qualificador de namespace global"
ms.assetid: 98a1d89b-3c5a-44f7-8400-c4a3c0ec22a9
caps.latest.revision: 23
caps.handback.revision: 23
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Como usar o alias de namespace global (Guia de Programa&#231;&#227;o em C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

A capacidade de acessar um membro no global  [espaço para nome](../../../csharp/language-reference/keywords/namespace.md) é útil quando o membro pode estar oculto por outra entidade de mesmo nome.  
  
 Por exemplo, no código a seguir, `Console` resolve para `TestApp.Console` ao invés da `Console` digite o <xref:System> espaço para nome.  
  
 [!code-cs[csProgGuide#1](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/how-to-use-the-global-namespace-alias_1.cs)]  
  
 [!code-cs[csProgGuideNamespaces#1](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/how-to-use-the-global-namespace-alias_2.cs)]  
  
 Usando `System.Console` ainda resulta em erro, porque o `System` namespace está oculta pela classe `TestApp.System`:  
  
 [!code-cs[csProgGuideNamespaces#2](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/how-to-use-the-global-namespace-alias_3.cs)]  
  
 No entanto, você pode contornar esse erro, usando `global::System.Console`, como este:  
  
 [!code-cs[csProgGuideNamespaces#3](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/how-to-use-the-global-namespace-alias_4.cs)]  
  
 Quando o identificador esquerdo está `global`, a pesquisa para o identificador direito começa no namespace global.  Por exemplo, a declaração a seguir faz referência ao `TestApp` como um membro do espaço global.  
  
 [!code-cs[csProgGuideNamespaces#4](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/how-to-use-the-global-namespace-alias_5.cs)]  
  
 Obviamente, a criação de seus próprios espaços para nome chamado `System` não é recomendada, e é improvável que você encontre qualquer código em que isso aconteceu.  No entanto, em projetos maiores, é uma possibilidade bastante real que o namespace duplicação pode ocorrer em um formato ou outro.  Nessas situações, o qualificador de namespace global é a sua garantia de que você pode especificar o namespace raiz.  
  
## Exemplo  
 Neste exemplo, o namespace `System` é usada para incluir a classe `TestClass` , portanto, `global::System.Console` deve ser usado para referência a `System.Console` classe, que está oculta pela `System` namespace.  Além disso, o alias `colAlias` é usado para fazer referência ao namespace `System.Collections`; Portanto, a instância de um <xref:System.Collections.Hashtable?displayProperty=fullName> foi criado com o uso desse alias em vez do namespace.  
  
 [!code-cs[csProgGuideNamespaces#5](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/how-to-use-the-global-namespace-alias_6.cs)]  
  
  **UM 1**  
**B 2**  
**C 3**   
## Consulte também  
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Namespaces](../../../csharp/programming-guide/namespaces/index.md)   
 [Operador .](../../../csharp/language-reference/operators/member-access-operator.md)   
 [Operador ::](../Topic/::%20Operator%20\(C%23%20Reference\).md)   
 [extern](../../../csharp/language-reference/keywords/extern.md)