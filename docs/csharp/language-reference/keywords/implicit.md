---
title: "implicit (Refer&#234;ncia de C#) | Microsoft Docs"
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
  - "implicit"
  - "implicit_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "palavra-chave implicit [C#]"
ms.assetid: 34db590e-eb3a-4f11-88d0-ffb3cd753dab
caps.latest.revision: 19
caps.handback.revision: 19
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# implicit (Refer&#234;ncia de C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

O `implicit` palavra\-chave é usada para declarar um operador de conversão implícita de tipo definido pelo usuário.  Usá\-lo para permitir conversões implícitas entre um tipo definido pelo usuário e outro tipo, a conversão é garantida que não causa perda de dados.  
  
## Exemplo  
 [!CODE [csrefKeywordsConversion#5](../CodeSnippet/VS_Snippets_VBCSharp/csrefKeywordsConversion#5)]  
  
 Eliminando conversões desnecessárias, conversões implícitas podem melhorar a legibilidade do código de origem.  No entanto, como conversões implícitas não exigem aos programadores explicitamente convertido de um tipo para outro, é preciso cuidado para evitar resultados inesperados.  Em geral, os operadores de conversão implícita devem nunca lançar exceções e nunca perder informações, para que possa ser usados com segurança sem o reconhecimento do programador.  Se um operador de conversão não pode atender a esses critérios, ele deve ser marcado `explicit`.  Para obter mais informações, consulte  [Usando os operadores de conversão](../../../csharp/programming-guide/statements-expressions-operators/using-conversion-operators.md).  
  
## Especificação da linguagem C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## Consulte também  
 [Referência de C\#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Palavras\-chave C\#](../../../csharp/language-reference/keywords/index.md)   
 [explicit](../../../csharp/language-reference/keywords/explicit.md)   
 [operator](../../../csharp/language-reference/keywords/operator.md)   
 [Como implementar conversões definidas pelo usuário entre structs](../../../csharp/programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)