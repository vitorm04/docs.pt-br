---
title: "Usando tipos anul&#225;veis (Guia de Programa&#231;&#227;o em C#) | Microsoft Docs"
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
  - "tipos anuláveis [C#], sobre tipos anuláveis"
ms.assetid: 0bacbe72-ce15-4b14-83e1-9c14e6380c28
caps.latest.revision: 31
caps.handback.revision: 31
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Usando tipos anul&#225;veis (Guia de Programa&#231;&#227;o em C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Tipos anuláveis podem representar todos os valores de um tipo subjacente e adicional  [Nulo](../../../csharp/language-reference/keywords/null.md) valor.  Tipos anuláveis são declarados em uma das seguintes maneiras:  
  
 `System.Nullable<T> variable`  
  
 \- ou \-  
  
 `T?  variable`  
  
 `T`é o tipo subjacente do tipo anulável.  `T`pode ser qualquer tipo de valor incluindo `struct`; ele não pode ser um tipo de referência.  
  
 Para obter um exemplo de quando você pode usar um tipo anulável, considere como uma variável booleana comum pode ter dois valores: true e false.  Não há nenhum valor para o que significa "indefinidos".  Em muitos aplicativos de programação, principalmente database interações, variáveis que podem ocorrer em um estado indefinido.  Por exemplo, um campo em um banco de dados pode conter os valores true ou falsos, mas não pode também conter nenhum valor.  Da mesma forma, os tipos de referência podem ser definidos como `null` para indicar que eles não são inicializados.  
  
 Esta disparidade pode criar o trabalho extra de programação, com variáveis adicionais usadas para armazenar informações de estado, o uso de valores especiais e assim por diante.  O modificador do tipo anulável permite C\# criar variáveis de tipo de valor que indicam um valor indefinido.  
  
## Exemplos de tipos anuláveis  
 Qualquer tipo de valor pode ser usado como base para um tipo anulável.  Por exemplo:  
  
 [!code-cs[csProgGuideTypes#4](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_1.cs)]  
  
## Os membros de tipos anuláveis  
 Cada instância de um tipo anulável tem duas propriedades públicas de somente leitura:  
  
-   `HasValue`  
  
     `HasValue`é do tipo `bool`.  Ela é definida como `true` quando a variável contém um valor não nulo.  
  
-   `Value`  
  
     `Value`é do mesmo tipo que o tipo subjacente.  Se `HasValue` é `true`, `Value` contém um valor significativo.  If `HasValue` is `false`, accessing `Value` will throw a <xref:System.InvalidOperationException>.  
  
 Neste exemplo, o `HasValue` membro é usado para testar se a variável contém um valor antes de tentar exibi\-la.  
  
 [!code-cs[csProgGuideTypes#5](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_2.cs)]  
  
 Teste para um valor também pode ser feito como no exemplo a seguir:  
  
 [!code-cs[csProgGuideTypes#6](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_3.cs)]  
  
## Conversões explícitas  
 Um tipo anulável pode ser convertido em um tipo regular, explicitamente, com uma projeção ou usando o `Value` propriedade.  Por exemplo:  
  
 [!code-cs[csProgGuideTypes#7](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_4.cs)]  
  
 Se uma conversão definida pelo usuário é definida entre os dois tipos de dados, a mesma conversão também pode ser usada com as versões anuláveis desses tipos de dados.  
  
## Conversões implícitas  
 Uma variável do tipo anulável pode ser definida como null com o `null` palavra\-chave, como mostrado no exemplo a seguir:  
  
 [!code-cs[csProgGuideTypes#8](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_5.cs)]  
  
 A conversão de um tipo comum para um tipo anulável, está implícito.  
  
 [!code-cs[csProgGuideTypes#9](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_6.cs)]  
  
## Operadores  
 O unário predefinido e operadores binários e os operadores definidos pelo usuário que existem para tipos de valor também podem ser usados por tipos anuláveis.  Esses operadores para produzir um valor nulo se os operandos forem nulos. Caso contrário, o operador usa o valor contido calcular o resultado.  Por exemplo:  
  
 [!code-cs[csProgGuideTypes#10](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_7.cs)]  
  
 Ao realizar comparações com tipos anuláveis, se o valor de um dos tipos anuláveis é nulo e o outro não, todas as comparações de avaliar a `false` , exceto para `!=` \(não igual\).  É importante não assumir que, como uma comparação particular retorna `false`, o caso oposto retorna `true`.  No exemplo a seguir, 10 não é maior que, menor que nem igual a nulo.  Somente `num1 != num2` for avaliada como `true`.  
  
 [!code-cs[csProgGuideTypes#11](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_8.cs)]  
  
 Uma comparação de igualdade de dois tipos anuláveis ambos nulo é avaliada como `true`.  
  
## O??Operador  
 O `??` operador define um valor padrão que é retornado quando um tipo anulável é atribuído a um tipo não anulável.  
  
 [!code-cs[csProgGuideTypes#12](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_9.cs)]  
  
 Este operador também pode ser usado com vários tipos anuláveis.  Por exemplo:  
  
 [!code-cs[csProgGuideTypes#13](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_10.cs)]  
  
## O bool?tipo  
 O `bool?` tipo anulável pode conter três valores diferentes:  [true](../../../csharp/language-reference/keywords/true.md),  [false](../../../csharp/language-reference/keywords/false.md) e  [Nulo](../../../csharp/language-reference/keywords/null.md).  Para obter informações sobre como lançar um um bool?  para um bool, consulte [Como converter bool? em bool com segurança](../../../csharp/programming-guide/nullable-types/how-to-safely-cast-from-bool-to-bool.md).  
  
 Booleanos anuláveis são como o tipo de variável booleano que é usado em SQL.  Para garantir que os resultados produzidos pela `&` e  `|` os operadores são consistentes com o tipo booleano três valores no SQL, os seguintes operadores predefinidos são fornecidos:  
  
 `bool?  operator &(bool?  x, bool?  y)`  
  
 `bool?  operator |(bool?  x, bool?  y)`  
  
 Os resultados desses operadores estão listados na tabela a seguir:  
  
|X|y|x e y|x&#124;y|  
|-------|-------|-----------|--------------|  
|verdadeiro|verdadeiro|verdadeiro|verdadeiro|  
|verdadeiro|FALSO|FALSO|verdadeiro|  
|verdadeiro|Nulo|Nulo|verdadeiro|  
|FALSO|verdadeiro|FALSO|verdadeiro|  
|FALSO|FALSO|FALSO|FALSO|  
|FALSO|Nulo|FALSO|Nulo|  
|Nulo|verdadeiro|Nulo|verdadeiro|  
|Nulo|FALSO|FALSO|Nulo|  
|Nulo|Nulo|Nulo|Nulo|  
  
## Consulte também  
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Tipos anuláveis](../../../csharp/programming-guide/nullable-types/index.md)   
 [Executando a conversão boxing de tipos anuláveis](../../../csharp/programming-guide/nullable-types/boxing-nullable-types.md)   
 [Tipos de valor que permitem valor nulo](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)