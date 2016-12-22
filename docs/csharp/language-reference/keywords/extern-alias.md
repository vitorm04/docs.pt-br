---
title: "extern alias (Refer&#234;ncia de C#) | Microsoft Docs"
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
  - "alias_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "aliases [C#], palavra-chave extern"
  - "aliases, palavra-chave extern"
  - "palavra-chave de alias extern [C#]"
ms.assetid: f487bf4f-c943-4fca-851b-e540c83d9027
caps.latest.revision: 16
caps.handback.revision: 16
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# extern alias (Refer&#234;ncia de C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Você pode ter que fazer referência a duas versões de módulos \(assemblies\) têm os mesmos nomes de tipo totalmente qualificado.  Por exemplo, talvez você precise usar duas ou mais versões de um assembly no mesmo aplicativo.  Usando um alias de assembly externo, os espaços para nome de cada assembly podem ser dispostos dentro de espaços para nome de nível de raiz chamados pelo alias, que permite a ser usado no mesmo arquivo.  
  
> [!NOTE]
>  O  [extern](../../../csharp/language-reference/keywords/extern.md) palavra\-chave também é usado como um modificador do método, declarando um método escrito em código não gerenciado.  
  
 Para fazer referência a dois assemblies com os mesmos nomes de tipo totalmente qualificado, um alias deve ser especificado em um prompt de comando, da seguinte maneira:  
  
 `/r:GridV1=grid.dll`  
  
 `/r:GridV2=grid20.dll`  
  
 Isso cria os aliases externos `GridV1` e `GridV2`.  Para usar esses aliases de dentro de um programa, referenciará usando o `extern` palavra\-chave.  Por exemplo:  
  
 `extern alias GridV1;`  
  
 `extern alias GridV2;`  
  
 Cada extern alias declaração apresenta um namespace de nível de raiz adicional que se iguala \(mas não fique na\) o namespace global.  Assim, os tipos de cada assembly podem ser chamados sem ambigüidade usando seu nome totalmente qualificado, enraizada no alias de namespace apropriado.  
  
 No exemplo anterior, `GridV1::Grid` seria o controle de grade de `grid.dll`, e `GridV2::Grid` seria o controle de grade de `grid20.dll`.  
  
## Especificação da linguagem C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## Consulte também  
 [Referência de C\#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Palavras\-chave C\#](../../../csharp/language-reference/keywords/index.md)   
 [Palavras\-chave de namespace](../../../csharp/language-reference/keywords/namespace-keywords.md)   
 [Operador ::](../Topic/::%20Operator%20\(C%23%20Reference\).md)   
 [\/reference \(Import Metadata\)](../../../csharp/language-reference/compiler-options/reference-compiler-option.md)