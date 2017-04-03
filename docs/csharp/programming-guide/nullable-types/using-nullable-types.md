---
title: "Usando tipos que permitem valor nulo (Guia de programação em C#) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- nullable types [C#], about nullable types
ms.assetid: 0bacbe72-ce15-4b14-83e1-9c14e6380c28
caps.latest.revision: 31
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 88397167b12a00bf5e99a0537148a2957b9f0bd8
ms.lasthandoff: 03/13/2017

---
# <a name="using-nullable-types-c-programming-guide"></a>Usando tipos anuláveis (Guia de Programação em C#)
Os tipos que permitem valor nulo podem representar todos os valores de um tipo subjacente e um valor adicional [null](../../../csharp/language-reference/keywords/null.md) . Os tipos que permitem valor nulo são declarados em uma das duas maneiras:  
  
 `System.Nullable<T> variable`  
  
 -ou-  
  
 `T? variable`  
  
 `T` é o tipo subjacente do tipo que permite valor nulo. `T` pode ser qualquer tipo de valor incluindo `struct`. Ele não pode ser um tipo de referência.  
  
 Para um exemplo de quando é possível usar um tipo que permite valor nulo, considere como uma variável booliana comum pode ter dois valores: true e false. Não há nenhum valor que significa "indefinido". Em muitas aplicações em programação, principalmente nas interações de banco de dados, as variáveis podem ocorrer em um estado indefinido. Por exemplo, um campo em um banco de dados pode conter os valores true ou false, mas também pode não conter nenhum valor. Da mesma forma, os tipos de referência podem ser definidos como `null` para indicar que eles não estão inicializados.  
  
 Esta disparidade pode criar trabalho extra de programação, com variáveis adicionais usadas para armazenar informações de estado, o uso de valores especiais e assim por diante. O modificador de tipo que permite valor nulo habilita o C# a criar variáveis de tipo de valor que indicam um valor indefinido.  
  
## <a name="examples-of-nullable-types"></a>Exemplos de tipos que permitem valor nulo  
 Qualquer tipo de valor pode ser usado como base para um tipo que permite valor nulo. Por exemplo:  
  
 [!code-cs[csProgGuideTypes#4](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_1.cs)]  
  
## <a name="the-members-of-nullable-types"></a>Os membros de tipos que permitem valor nulo  
 Cada instância de um tipo que permite valor nulo tem duas propriedades públicas somente leitura:  
  
-   `HasValue`  
  
     `HasValue` é do tipo `bool`. Ele é definido como `true` quando a variável contém um valor não nulo.  
  
-   `Value`  
  
     `Value` é do mesmo tipo que o tipo subjacente. Se `HasValue` for `true`, `Value` conterá um valor significativo. Se `HasValue` for `false`, acessar `Value` lançará uma <xref:System.InvalidOperationException>.  
  
 Neste exemplo, o membro `HasValue` é usado para testar se a variável contém um valor antes de tentar exibi-la.  
  
 [!code-cs[csProgGuideTypes#5](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_2.cs)]  
  
 O teste de um valor também pode ser feito como no exemplo a seguir:  
  
 [!code-cs[csProgGuideTypes#6](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_3.cs)]  
  
## <a name="explicit-conversions"></a>Conversões explícitas  
 Um tipo que permite valor nulo pode ser convertido em um tipo regular, explicitamente com uma conversão ou usando a propriedade `Value`. Por exemplo:  
  
 [!code-cs[csProgGuideTypes#7](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_4.cs)]  
  
 Se uma conversão definida pelo usuário for definida entre dois tipos de dados, a mesma conversão também poderá ser usada com as versões que permitem valor nulo desses tipos de dados.  
  
## <a name="implicit-conversions"></a>Conversões implícitas  
 Uma variável do tipo que permite valor nulo pode ser definida como null com a palavra-chave `null`, conforme mostrado no exemplo a seguir:  
  
 [!code-cs[csProgGuideTypes#8](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_5.cs)]  
  
 A conversão de um tipo comum para um tipo que permite valor nulo, é implícita.  
  
 [!code-cs[csProgGuideTypes#9](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_6.cs)]  
  
## <a name="operators"></a>Operadores  
 Os operadores unários e binários predefinidos e os operadores definidos pelo usuário que existem para tipos de valor também podem ser usados por tipos que permitem valor nulo. Esses operadores produzem um valor nulo se os operandos são nulos. Caso contrário, o operador usa o valor contido para calcular o resultado. Por exemplo:  
  
 [!code-cs[csProgGuideTypes#10](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_7.cs)]  
  
 Quando você realiza comparações com tipos que permitem valor nulo, se o valor de um dos tipos que permitem valor nulo for nulo e o outro não, todas as comparações serão avaliadas como `false`, exceto `!=` (não igual). É importante não presumir que porque uma comparação retorna `false`, o caso oposto retornará `true`. No exemplo a seguir, 10 não é maior que, menor que nem igual a null. Somente `num1 != num2` é avaliado como `true`.  
  
 [!code-cs[csProgGuideTypes#11](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_8.cs)]  
  
 Uma comparação de igualdade de dois tipos que permitem valor nulo, em que ambos são null, é avaliada como `true`.  
  
## <a name="the--operator"></a>O operador ?? Operador  
 O operador `??` define um valor padrão que é retornado quando um tipo que permite valor nulo é atribuído a um tipo que não permite valor nulo.  
  
 [!code-cs[csProgGuideTypes#12](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_9.cs)]  
  
 Este operador também pode ser usado com vários tipos que permitem valor nulo. Por exemplo:  
  
 [!code-cs[csProgGuideTypes#13](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_10.cs)]  
  
## <a name="the-bool-type"></a>O tipo bool?  
 O tipo que permite valor nulo `bool?` pode conter três valores diferentes: [true](../../../csharp/language-reference/keywords/true.md), [false](../../../csharp/language-reference/keywords/false.md) e [null](../../../csharp/language-reference/keywords/null.md). Para obter informações sobre como converter de um bool? para um bool, consulte [Como converter bool? em bool com segurança](../../../csharp/programming-guide/nullable-types/how-to-safely-cast-from-bool-to-bool.md).  
  
 Os boolianos que permitem valor nulo são como o tipo de variável booliana que é usada no SQL. Para garantir que os resultados produzidos pelos operadores `&` e `|` são consistentes com o tipo booliano de três valores no SQL, os seguintes operadores predefinidos são fornecidos:  
  
 `bool? operator &(bool? x, bool? y)`  
  
 `bool? operator |(bool? x, bool? y)`  
  
 Os resultados desses operadores estão listados na tabela a seguir:  
  
|X|y|x&y|x&#124;y|  
|-------|-------|---------|--------------|  
|true|true|true|true|  
|true|false|false|true|  
|true|nulo|nulo|true|  
|false|true|false|true|  
|false|false|false|false|  
|false|nulo|false|nulo|  
|nulo|true|nulo|true|  
|nulo|false|false|nulo|  
|nulo|nulo|nulo|nulo|  
  
## <a name="see-also"></a>Consulte também  
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)   
 [Tipos que permitem valor nulo](../../../csharp/programming-guide/nullable-types/index.md)   
 [Conversão boxing de tipos que permitem valor nulo](../../../csharp/programming-guide/nullable-types/boxing-nullable-types.md)   
 [Tipos de Valor Anulável](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
