---
title: "Contexto verificado e não verificado (Referência de C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- operators [C#], checked and unchecked
- exceptions [C#], overflow checking
- checked statement [C#]
- overflow checking [C#]
- unchecked statement [C#]
- statements [C#], checked and unchecked
ms.assetid: a84bc877-2c7f-4396-8735-1ce97c42f35e
caps.latest.revision: "17"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 4b7b18b39dbfa7ed0818d9ea6e9e62ef79a9f5b7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="checked-and-unchecked-c-reference"></a>Contexto verificado e não verificado (Referência de C#)
Instruções C# podem ser executadas em contexto marcado ou desmarcado. Em um contexto marcado, o estouro aritmético gera uma exceção. Em um contexto desmarcado, o estouro aritmético é ignorado e o resultado é truncado.  
  
-   [verificado](../../../csharp/language-reference/keywords/checked.md) Especificar o contexto verificado.  
  
-   [não verificado](../../../csharp/language-reference/keywords/unchecked.md) Especificar o contexto não verificado.  
  
 Se nem `checked` nem `unchecked` forem especificados, o contexto padrão dependerá de fatores externos, tais como as opções do compilador.  
  
 As seguintes operações são afetadas pela verificação de estouro:  
  
-   Expressões que usam os seguintes operadores predefinidos em tipos integrais:  
  
     `++` `--` – (unário)   `+` -   `*` `/`  
  
-   Conversões numéricas explícitas entre tipos integrais.  
  
 A opção do compilador [/checked](../../../csharp/language-reference/compiler-options/checked-compiler-option.md) permite especificar contexto verificado ou não verificado para todas as instruções aritméticas de inteiros que não estão explicitamente no escopo de uma palavra-chave `checked` ou `unchecked`.  
  
## <a name="see-also"></a>Consulte também  
 [Referência de C#](../../../csharp/language-reference/index.md)  
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)  
 [Palavras-chave do C#](../../../csharp/language-reference/keywords/index.md)  
 [Palavras-chave de instrução](../../../csharp/language-reference/keywords/statement-keywords.md)
