---
title: "Tipos de refer&#234;ncia (Refer&#234;ncia de C#) | Microsoft Docs"
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
  - "cs.referencetypes"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "Linguagem C#, tipos de referência"
  - "tipos de referência [C#]"
  - "tipos [C#], tipos de referência"
ms.assetid: 801cf030-6e2d-4a0d-9daf-1431b0c31f47
caps.latest.revision: 15
caps.handback.revision: 15
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Tipos de refer&#234;ncia (Refer&#234;ncia de C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Há dois tipos em C\#: tipos de referência e valor.  Variáveis de tipos de referência armazenam referências em seus dados \(objetos\) enquanto que variáveis de tipos de valor contém diretamente seus dados.  Com tipos de referência, duas variáveis podem fazer referência ao mesmo objeto; portanto, operações em uma variável podem afetar o objeto referenciado pela outra variável.  Com tipos de valor, cada variável possui sua própria cópia dos dados e não é possível que operações em uma variável afetem a outra \(exceto no caso de variáveis de parâmetros ref e out, consulte [ref](../../../csharp/language-reference/keywords/ref.md) e [Modificador de parâmetro out](../../../csharp/language-reference/keywords/out-parameter-modifier.md)\).  
  
 As seguintes palavras\-chaves são usadas para declarar tipos de referência:  
  
-   [classe](../../../csharp/language-reference/keywords/class.md)  
  
-   [interface](../../../csharp/language-reference/keywords/interface.md)  
  
-   [delegado](../../../csharp/language-reference/keywords/delegate.md)  
  
 O C\# também oferece os seguintes tipos de referência internos:  
  
-   [dinâmica](../../../csharp/language-reference/keywords/dynamic.md)  
  
-   [object](../../../csharp/language-reference/keywords/object.md)  
  
-   [cadeia de caracteres](../../../csharp/language-reference/keywords/string.md)  
  
## Consulte também  
 [Referência de C\#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Palavras\-chave C\#](../../../csharp/language-reference/keywords/index.md)   
 [Tipos](../../../csharp/language-reference/keywords/types.md)   
 [Tipos de valor](../../../csharp/language-reference/keywords/value-types.md)