---
title: "Operador == (Refer&#234;ncia de C#) | Microsoft Docs"
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
  - "==_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "Operador == [C#]"
  - "Operador de igualdade [C#]"
ms.assetid: 34c6b597-caa2-4855-a7cd-38ecdd11bd07
caps.latest.revision: 14
caps.handback.revision: 14
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Operador == (Refer&#234;ncia de C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Para tipos de valor, o operador de igualdade de predefinidos \(`==`\) retorna true se os valores dos operandos forem iguais, `false` contrário.  Para referência tipos diferentes de  [seqüência de caracteres](../../../csharp/language-reference/keywords/string.md), `==` retorna `true` se dois operandos se referir ao mesmo objeto.  Para o `string` tipo, `==` compara os valores das cadeias de caracteres.  
  
## Comentários  
 Tipos de valor definido pelo usuário podem sobrecarregar o `==` operador \(consulte  [operador](../../../csharp/language-reference/keywords/operator.md)\).  Podem então os tipos de referência definidos pelo usuário, embora por padrão `==` se comporta como descrito acima para ambos os tipos de referência predefinidas e definidas pelo usuário.  Se `==` está sobrecarregado,  [\! \=](../../../csharp/language-reference/operators/not-equal-operator.md) também deve ser sobrecarregados.  Geralmente, as operações em tipos integrais são permitidas na enumeração.  
  
## Exemplo  
 [!CODE [csRefOperators#36](../CodeSnippet/VS_Snippets_VBCSharp/csrefOperators#36)]  
  
## Consulte também  
 [Referência de C\#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Operadores em C\#](../../../csharp/language-reference/operators/index.md)