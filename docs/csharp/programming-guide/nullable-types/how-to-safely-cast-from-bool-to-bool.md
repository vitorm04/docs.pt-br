---
title: "Como converter bool? em bool com seguran&#231;a (Guia de Programa&#231;&#227;o em C#) | Microsoft Docs"
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
  - "conversão [C#], tipos anuláveis"
  - "tipos anuláveis [C#], convertendo bool? em bool"
ms.assetid: e06e4274-a443-422d-8ef1-9dbf9df55237
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Como converter bool? em bool com seguran&#231;a (Guia de Programa&#231;&#227;o em C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

O tipo anulável `bool?` pode conter três valores diferentes: `true`, `false` e `null`.  Portanto, o tipo `bool?` não pode ser usado em condicionais como `if`, `for` ou `while`.  Por exemplo, o código a seguir causa um erro do compilador.  
  
```  
bool? b = null;  
if (b) // Error CS0266.  
{  
}  
```  
  
 Isso não é permitido porque não fica claro o que `null` significa no contexto de um condicional.  Para usar `bool?` em uma instrução condicional, verifique primeiro sua propriedade de <xref:System.Nullable%601.HasValue%2A> para garantir que o valor não é `null`, e para convertê\-lo para `bool`.  Para obter mais informações, consulte [bool](../../../csharp/language-reference/keywords/bool.md).  Se você realizar a conversão em um `bool?` com um valor de `null`, <xref:System.InvalidOperationException> será lançado no teste condicional.  O exemplo a seguir mostra uma maneira de converter com segurança de `bool?` para `bool`:  
  
## Exemplo  
  
```c#  
bool? test = null;  
// Other code that may or may not  
// give a value to test.  
if(!test.HasValue) //check for a value  
{  
    // Assume that IsInitialized  
    // returns either true or false.  
    test = IsInitialized();  
}  
if((bool)test) //now this cast is safe  
{  
   // Do something.  
}  
```  
  
## Consulte também  
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Palavras\-chave literais](../../../csharp/language-reference/keywords/literal-keywords.md)   
 [Tipos anuláveis](../../../csharp/programming-guide/nullable-types/index.md)   
 [Operador ??](../../../csharp/language-reference/operators/null-conditional-operator.md)