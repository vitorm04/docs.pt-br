---
title: "#elif (Refer&#234;ncia de C#) | Microsoft Docs"
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
  - "#elif"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "Diretiva #elif [C#]"
ms.assetid: 731d78df-08e0-4d51-b8c8-f193c27de13f
caps.latest.revision: 14
caps.handback.revision: 14
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# #elif (Refer&#234;ncia de C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

`#elif` permite que você crie uma diretiva condicional composta.  A expressão de `#elif` será avaliada se nem [\#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) anterior ou precedência, opcional, expressões políticas de `#elif` valor para `true`.  Se uma expressão de `#elif` avalia a `true`, o compilador avalia qualquer código entre `#elif` e a diretiva condicional seguir.  Por exemplo:  
  
```  
#define VC7  
//...  
#if debug  
    Console.Writeline("Debug build");  
#elif VC7  
    Console.Writeline("Visual Studio 7");  
#endif  
```  
  
 Você pode usar os operadores `==` \(igualdade\), `!=` \(desigualdade\), `&&` \(e\), e `||` \(ou\), para avaliar mais símbolos.  Você também pode agrupar símbolos e operadores com parênteses.  
  
## Comentários  
 `#elif` é equivalente à uso:  
  
```  
#else  
#if  
```  
  
 Usar `#elif` é mais simples, porque cada `#if` requer [\#endif](../../../csharp/language-reference/preprocessor-directives/preprocessor-endif.md), enquanto `#elif` pode ser usado sem `#endif`correspondente.  
  
 Consulte [\#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) para um exemplo de como usar `#elif`.  
  
## Consulte também  
 [Referência de C\#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Diretivas de pré\-processador em C\#](../../../visual-basic/reference/command-line-compiler/index.md)