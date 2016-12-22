---
title: "partial (m&#233;todo) (Refer&#234;ncia de C#) | Microsoft Docs"
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
  - "partialmethod_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "métodos parciais [C#]"
ms.assetid: 43f40242-17e0-4452-8573-090503ad3137
caps.latest.revision: 26
caps.handback.revision: 26
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# partial (m&#233;todo) (Refer&#234;ncia de C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Um método parcial tem sua assinatura definido em uma parte de um tipo parcial, e sua implementação definida em outra parte do tipo.  Métodos parciais permitem designer de classe para fornecer ganchos de método, semelhantes aos manipuladores de eventos, que os desenvolvedores podem decidir implementar ou não.  Se o desenvolvedor não fornece uma implementação, o compilador remove a assinatura em tempo de compilação.  As seguintes condições se aplicam aos métodos parciais:  
  
-   As assinaturas em ambas as partes do tipo parcial devem coincidir.  
  
-   O método deve retornar o vácuo.  
  
-   É permitido a nenhum modificador de acesso.  Métodos parciais são implicitamente particulares.  
  
 O exemplo a seguir mostra um método parcial definido em duas partes de uma classe parcial:  
  
 [!code-cs[csrefKeywordsContextual#9](../../../csharp/language-reference/keywords/codesnippet/CSharp/partial-method_1.cs)]  
  
 Para obter mais informações, consulte [Classes e métodos partial](../../../csharp/programming-guide/classes-and-structs/partial-classes-and-methods.md).  
  
## Consulte também  
 [Referência de C\#](../../../csharp/language-reference/index.md)   
 [partial \(tipo\)](../../../csharp/language-reference/keywords/partial-type.md)