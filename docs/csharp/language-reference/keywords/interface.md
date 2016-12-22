---
title: "interface (Refer&#234;ncia de C#) | Microsoft Docs"
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
  - "interface_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "palavra-chave interface [C#]"
ms.assetid: 7da38e81-4f99-4bc5-b07d-c986b687eeba
caps.latest.revision: 29
caps.handback.revision: 29
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# interface (Refer&#234;ncia de C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Uma interface contém apenas assinaturas de [métodos](../../../fsharp/language-reference/members/methods.md), de [propriedades](../../../csharp/programming-guide/classes-and-structs/properties.md), de [eventos](../../../csharp/programming-guide/events/index.md) ou de [indexadores](../../../csharp/programming-guide/indexers/index.md).  Uma classe ou estrutura que implementa a interface devem implementar membros de interface que são especificados na definição de interface.  No exemplo a seguir, a classe `ImplementationClass` deve implementar um método chamado `SampleMethod` que não tem nenhum parâmetro e retorna `void`.  
  
 Para mais informações e exemplos, consulte [Interfaces](../../../visual-basic/reference/command-line-compiler/index.md).  
  
## Exemplo  
 [!CODE [csrefKeywordsTypes#14](../CodeSnippet/VS_Snippets_VBCSharp/csrefKeywordsTypes#14)]  
  
 Uma interface pode ser um membro de namespace ou uma classe e pode conter assinaturas dos seguintes membros:  
  
-   [Métodos](../../../fsharp/language-reference/members/methods.md)  
  
-   [Propriedades](../../../csharp/programming-guide/classes-and-structs/using-properties.md)  
  
-   [Indexadores](../../../csharp/programming-guide/indexers/using-indexers.md)  
  
-   [Eventos](../../../csharp/language-reference/keywords/event.md)  
  
 Uma interface pode herdar de uma ou mais interfaces base.  
  
 Quando uma lista de tipo base contém uma classe base e interfaces, a classe base deve vir primeiro na lista.  
  
 Uma classe que implementa uma interface pode explicitamente implementar membros da interface.  Um membro implementado explicitamente não pode ser acessado através de uma instância da classe, mas somente através de uma instância da interface.  
  
 Para obter detalhes e exemplos de código explícita na implementação da interface, consulte [Implementação de interface explícita](../../../csharp/programming-guide/interfaces/explicit-interface-implementation.md).  
  
## Exemplo  
 O exemplo a seguir demonstra a implementação da interface.  Nesse exemplo, a interface contém a declaração de propriedade e a classe contém a implementação.  Qualquer instância de uma classe que implementa `IPoint` tem propriedades `x` e `y`inteiro.  
  
 [!CODE [csrefKeywordsTypes#15](../CodeSnippet/VS_Snippets_VBCSharp/csrefKeywordsTypes#15)]  
  
## Especificação da Linguagem C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## Consulte também  
 [Referência de C\#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Palavras\-chave C\#](../../../csharp/language-reference/keywords/index.md)   
 [Tipos de referência](../../../csharp/language-reference/keywords/reference-types.md)   
 [Interfaces](../../../visual-basic/reference/command-line-compiler/index.md)   
 [Usando propriedades](../../../csharp/programming-guide/classes-and-structs/using-properties.md)   
 [Usando indexadores](../../../csharp/programming-guide/indexers/using-indexers.md)   
 [classe](../../../csharp/language-reference/keywords/class.md)   
 [struct](../../../csharp/language-reference/keywords/struct.md)   
 [Interfaces](../../../visual-basic/reference/command-line-compiler/index.md)