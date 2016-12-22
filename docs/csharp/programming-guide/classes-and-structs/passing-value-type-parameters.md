---
title: "Passando par&#226;metros de tipo de valor (Guia de Programa&#231;&#227;o em C#) | Microsoft Docs"
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
  - "parâmetros de método [C#], tipos de valor"
  - "parâmetros [C#], value"
ms.assetid: 193ab86f-5f9b-4359-ac29-7cdf8afad3a6
caps.latest.revision: 17
caps.handback.revision: 17
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Passando par&#226;metros de tipo de valor (Guia de Programa&#231;&#227;o em C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

A  [tipo de valor](../../../csharp/language-reference/keywords/value-types.md) variável contém seus dados diretamente, em oposição a uma  [tipo de referência](../../../csharp/language-reference/keywords/reference-types.md) variável, que contém uma referência a seus dados.  Passar uma variável do tipo de valor para um método por valor significa passar uma cópia da variável para o método.  Quaisquer alterações que ocorrem dentro do método para o parâmetro não tem nenhum efeito nos dados originais armazenados na variável argumento.  Se desejar que o método chamado para alterar o valor do parâmetro, deve passar por referência, usando o  [ref](../../../csharp/language-reference/keywords/ref.md) ou  [check\-out](../../../csharp/language-reference/keywords/out.md) palavra\-chave.  Para simplificar, os exemplos seguintes usam `ref`.  
  
## Tipos de valor de passagem por valor  
 O exemplo a seguir demonstra o tipo de valor de passagem de parâmetros por valor.  A variável `n` é passado por valor para o método `SquareIt`.  Quaisquer alterações que ocorrem dentro do método não têm nenhum efeito no valor da variável original.  
  
 [!code-cs[csProgGuideParameters#3](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/passing-value-type-parameters_1.cs)]  
  
 A variável `n` é um tipo de valor.  Ele contém os seus dados, o valor `5`.  Quando `SquareIt` é invocado, o conteúdo de `n` são copiados para o parâmetro `x`, que é elevado ao quadrado dentro do método.  Na `Main`, no entanto, o valor de `n` é o mesmo após a chamada a `SquareIt` método como ele era antes.  A alteração que ocorre dentro do método afeta somente a variável local `x`.  
  
## Tipos de valor de passagem por referência  
 O exemplo a seguir é o mesmo do exemplo anterior, exceto que o argumento é passado como um `ref` parâmetro.  O valor do argumento subjacente, `n`, será alterada quando `x` é alterado no método.  
  
 [!code-cs[csProgGuideParameters#4](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/passing-value-type-parameters_2.cs)]  
  
 Neste exemplo, não é o valor de `n` que é passado; em vez disso, uma referência a `n` é passado.  O parâmetro `x` não é um  [int](../../../csharp/language-reference/keywords/int.md); ele é uma referência a um `int`, neste caso, uma referência a `n`.  Portanto, quando `x` é elevado ao quadrado dentro do método, o que realmente é elevado ao quadrado é o que `x` refere\-se a, `n`.  
  
## Tipos de valor de troca  
 Um exemplo comum de alteração dos valores dos argumentos é um método de troca, onde você passar duas variáveis para o método e o método de troca de seu conteúdo.  Você deve passar argumentos para o método de troca por referência.  Caso contrário, você troca cópias locais dos parâmetros dentro do método e nenhuma alteração ocorre no método de chamada.  O exemplo a seguir troca os valores inteiros.  
  
 [!code-cs[csProgGuideParameters#5](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/passing-value-type-parameters_3.cs)]  
  
 Quando você chama o `SwapByRef` método, use o `ref` palavra\-chave na chamada, conforme mostrado no exemplo a seguir.  
  
 [!code-cs[csProgGuideParameters#6](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/passing-value-type-parameters_4.cs)]  
  
## Consulte também  
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Passando parâmetros](../../../csharp/programming-guide/classes-and-structs/passing-parameters.md)   
 [Passando parâmetros de tipo de referência](../../../csharp/programming-guide/classes-and-structs/passing-reference-type-parameters.md)