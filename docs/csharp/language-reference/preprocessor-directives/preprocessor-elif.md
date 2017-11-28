---
title: "#<a name=\"elif-c-reference\"></a>elif (Referência de C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: '#elif'
helpviewer_keywords: '#elif directive [C#]'
ms.assetid: 731d78df-08e0-4d51-b8c8-f193c27de13f
caps.latest.revision: "14"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 1512bbbc46ce15570507c8b51540eef607d55dc8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="elif-c-reference"></a>#elif (Referência de C#)
O `#elif` permite criar uma diretiva condicional composta. A expressão `#elif` será avaliada se nenhum dos [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) anteriores nem nenhuma diretiva `#elif`, opcional, anterior avaliar expressões para `true`. Se uma expressão `#elif` for avaliada como `true`, o compilador avalia todo o código entre o `#elif` e a próxima diretiva condicional. Por exemplo:  
  
```csharp
#define VC7  
//...  
#if debug  
    Console.Writeline("Debug build");  
#elif VC7  
    Console.Writeline("Visual Studio 7");  
#endif  
```  
  
 É possível usar os operadores `==` (igualdade), `!=` (desigualdade), `&&` (e) e `||` (ou), para avaliar vários símbolos. Também é possível agrupar os símbolos e operadores com parênteses.  
  
## <a name="remarks"></a>Comentários  
 `#elif` é equivalente a usar:  
  
```csharp
#else  
#if  
```  
  
 Usar `#elif` é mais simples, porque cada `#if` requer um [#endif](../../../csharp/language-reference/preprocessor-directives/preprocessor-endif.md), enquanto um `#elif` pode ser usado sem um `#endif` de correspondência.  
  
 Consulte [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) para obter um exemplo de como usar `#elif`.  
  
## <a name="see-also"></a>Consulte também  
 [Referência de C#](../../../csharp/language-reference/index.md)  
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)  
 [Diretivas do pré-processador do C#](../../../csharp/language-reference/preprocessor-directives/index.md)
