---
title: "Indexadores em interfaces (Guia de Programa&#231;&#227;o em C#) | Microsoft Docs"
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
  - "acessadores [C#], indexadores"
  - "indexadores [C#], em interfaces"
ms.assetid: e16b54bd-4a83-4f52-bd75-65819fca79e8
caps.latest.revision: 18
caps.handback.revision: 18
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Indexadores em interfaces (Guia de Programa&#231;&#227;o em C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Os indexadores podem ser declarados em um [interface](../../../csharp/language-reference/keywords/interface.md).  Acessadores de indexadores interface diferem os acessadores de  [classe](../../../csharp/language-reference/keywords/class.md) indexadores das seguintes maneiras:  
  
-   Acessadores de interface não usam modificadores.  
  
-   Um acessador de interface não tem um corpo.  
  
 Portanto, é o objetivo do acessador indicar se o indexador é leitura\-gravação, somente leitura ou somente para gravação.  
  
 Este é um exemplo de um acessador do indexador de interface:  
  
 [!code-cs[csProgGuideIndexers#3](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/indexers-in-interfaces_1.cs)]  
  
 A assinatura de um indexador deve diferir de assinaturas de todos os outros indexadores declaradas na interface do mesma.  
  
## Exemplo  
 O exemplo a seguir mostra como implementar os indexadores de interface.  
  
 [!code-cs[csProgGuideIndexers#4](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/indexers-in-interfaces_2.cs)]  
  
 No exemplo anterior, você poderia usar a implementação de um membro de interface explícita usando o nome totalmente qualificado do membro de interface.  Por exemplo:  
  
```  
public string ISomeInterface.this   
{   
}   
```  
  
 No entanto, o nome totalmente qualificado só é necessário para evitar ambigüidade quando a classe está implementando a mais de uma interface com a mesma assinatura do indexador.  Por exemplo, se um `Employee` classe está implementando duas interfaces, `ICitizen` e `IEmployee`, e ambas as interfaces têm a mesma assinatura do indexador, a implementação de um membro de interface explícita é necessária.  Ou seja, a seguinte declaração do indexador:  
  
```  
public string IEmployee.this   
{   
}   
```  
  
 implementa o indexador sobre o `IEmployee` interface, enquanto a declaração a seguir:  
  
```  
public string ICitizen.this   
{   
}   
```  
  
 implementa o indexador sobre o `ICitizen` interface.  
  
## Consulte também  
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Indexadores](../../../csharp/programming-guide/indexers/index.md)   
 [Propriedades](../../../csharp/programming-guide/classes-and-structs/properties.md)   
 [Interfaces](../../../visual-basic/reference/command-line-compiler/index.md)