---
title: "Delegados com m&#233;todos nomeados versus an&#244;nimos (Guia de Programa&#231;&#227;o em C#) | Microsoft Docs"
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
  - "delegados [C#], com métodos nomeados vs. anônimos"
  - "métodos [C#], em delegados"
ms.assetid: 98fa8c61-66b6-4146-986c-3236c4045733
caps.latest.revision: 18
caps.handback.revision: 18
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Delegados com m&#233;todos nomeados versus an&#244;nimos (Guia de Programa&#231;&#227;o em C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

A  [delegar](../../../csharp/language-reference/keywords/delegate.md) pode ser associado um método nomeado.  Quando você instancia um delegado usando um método nomeado, o método é passado como um parâmetro, por exemplo:  
  
 [!code-cs[csProgGuideDelegates#1](../../../csharp/programming-guide/delegates/codesnippet/CSharp/delegates-with-named-vs-anonymous-methods_1.cs)]  
  
 Ele é chamado usando um método nomeado.  Os delegados construídos com um método nomeado podem encapsular um um  [estático](../../../csharp/language-reference/keywords/static.md) método ou um método de instância.  Métodos nomeados são a única maneira de instanciar um delegado em versões anteriores do C\#.  No entanto, em uma situação onde a criação de um novo método é indesejado sobrecarga, C\# permite instanciar um delegado e imediatamente, especificar um bloco de código que processará o delegado quando for chamado.  O bloco pode conter uma expressão lambda ou um método anônimo.  Para obter mais informações, consulte [Funções anônimas](../../../csharp/programming-guide/statements-expressions-operators/anonymous-functions.md).  
  
## Comentários  
 O método que você passa como um parâmetro de delegate deve ter a mesma assinatura da declaração do Delegate.  
  
 Uma instância de Delegate pode encapsular o  método Estático ou Instânciado.  
  
 Embora o delegado pode usar um  [check\-out](../../../csharp/language-reference/keywords/out.md) parâmetro, não recomendamos seu uso com representantes de evento de difusão seletiva porque você não sabe qual representante será chamado.  
  
## Exemplo 1  
 O seguinte é um exemplo simples de como declarar e usar um delegate.  Observe que ambos delegates, `Del`, e o método associado, `MultiplyNumbers`,  possuem a mesma assinatura  
  
 [!code-cs[csProgGuideDelegates#2](../../../csharp/programming-guide/delegates/codesnippet/CSharp/delegates-with-named-vs-anonymous-methods_2.cs)]  
  
## Exemplo 2  
 No exemplo a seguir, um delegate é mapeado para ambos os métodos, estático e instaciado, e retorna informações específicas de cada um.  
  
 [!code-cs[csProgGuideDelegates#3](../../../csharp/programming-guide/delegates/codesnippet/CSharp/delegates-with-named-vs-anonymous-methods_3.cs)]  
  
## Consulte também  
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Delegados](../../../csharp/programming-guide/delegates/index.md)   
 [Métodos anônimos](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)   
 [Como combinar delegados \(delegados multicast\)](../../../csharp/programming-guide/delegates/how-to-combine-delegates-multicast-delegates.md)   
 [Eventos](../../../csharp/programming-guide/events/index.md)