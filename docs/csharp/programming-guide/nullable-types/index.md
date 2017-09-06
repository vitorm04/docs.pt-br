---
title: "Tipos anuláveis (Guia de Programação em C#)"
ms.date: 2017-05-15
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- nullable types [C#]
- C# language, nullable types
- types [C#], nullable
ms.assetid: e473cb01-28ca-42be-9cea-f717055d72c6
caps.latest.revision: 44
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
ms.translationtype: HT
ms.sourcegitcommit: 9bb64ea7199f5699ff166d1affb7f8126dcc6612
ms.openlocfilehash: 56e22638457017688ff380f6683b463b47c53a17
ms.contentlocale: pt-br
ms.lasthandoff: 09/02/2017

---
# <a name="nullable-types-c-programming-guide"></a>Tipos anuláveis (Guia de Programação em C#)
Os tipos que permitem valor nulo são instâncias do struct <xref:System.Nullable%601?displayProperty=fullName>. Um tipo que permite valor nulo pode representar o intervalo de valores para seu tipo de valor subjacente, além de um valor `null` adicional. Por exemplo, `Nullable<Int32>`, também indicado como “Nullable de Int32”, pode receber qualquer valor de –2147483648 a 2147483647 ou receber um valor `null`. Um `Nullable<bool>` pode ser atribuído aos valores [true](../../../csharp/language-reference/keywords/true.md), [false](../../../csharp/language-reference/keywords/false.md) ou [nulo](../../../csharp/language-reference/keywords/null.md). A capacidade de atribuir `null` para tipos numéricos e boolianos é especialmente útil quando você está lidando com bancos de dados e outros tipos de dados que contêm elementos que não podem ser atribuídos a um valor. Por exemplo, um campo booliano em um banco de dados pode armazenar os valores `true` ou `false` ou pode ser indefinido. 
  
[!code-cs[tipos que permitem valor nulo](../../../../samples/snippets/csharp/programming-guide/nullable-types/nullable-ex1.cs)]  
  
Para obter mais informações, consulte [Usando tipos que permitem valor nulo](../../../csharp/programming-guide/nullable-types/using-nullable-types.md)  
  
## <a name="nullable-types-overview"></a>Visão geral dos tipos que permitem valor nulo  
 Os tipos que permitem valor nulo têm as seguintes características:  
  
-   Os tipos que permitem valor nulo representam variáveis de tipo de valor que podem ser atribuídas ao valor de `null`. Você não pode criar um tipo que permite valor nulo com base em um tipo de referência. (Os tipos de referência já dão suporte ao valor `null`.)  
  
-   A sintaxe `T?` é a abreviação de <xref:System.Nullable%601>, em que `T` é um tipo de valor. As duas formas são intercambiáveis.  
  
-   Atribuir um valor a um tipo que permite valor nulo exatamente como faria para um tipo de valor comum, por exemplo `int? x = 10;` ou `double? d = 4.108`. Um tipo que permite valor nulo também pode ser atribuído ao valor `null`:`int? x = null.`  
  
-   Use o método <xref:System.Nullable%601.GetValueOrDefault%2A?displayProperty=fullName> para retornar o valor atribuído ou o valor padrão do tipo subjacente se o valor for `null`, por exemplo `int j = x.GetValueOrDefault();`  
  
-   Use as propriedades somente leitura <xref:System.Nullable%601.HasValue%2A> e <xref:System.Nullable%601.Value%2A> para testar em relação ao valor nulo e recupere o valor, conforme mostrado no exemplo a seguir: `if(x.HasValue) j = x.Value;`  
  
    -   A propriedade `HasValue` retornará `true` se a variável contiver um valor ou `false` se for `null`.  
  
    -   A propriedade `Value` retorna um valor se atribuído. Caso contrário, uma <xref:System.InvalidOperationException?displayProperty=fullName> será gerada.  
  
    -   O valor padrão para `HasValue` é `false`. A propriedade `Value` não tem valor padrão.  
  
    -   Você também pode usar os operadores `==` e `!=` com um tipo que permite valor nulo, conforme mostrado no exemplo a seguir: `if (x != null) y = x;`  
  
-   Use o operador `??` para atribuir um valor padrão que será aplicado quando um tipo que permite valor nulo cujo valor atual é `null` for atribuído a um tipo não anulável, por exemplo, `int? x = null; int y = x ?? -1;`  
  
-   Os tipos que permitem valor nulo aninhados não são permitidos. A linha a seguir não será compilada: `Nullable<Nullable<int>> n;`  
  
## <a name="related-sections"></a>Seções relacionadas  
 Para saber mais:  
  
-   [Usando tipos que permitem valor nulo](../../../csharp/programming-guide/nullable-types/using-nullable-types.md)  
  
-   [Conversão boxing de tipos que permitem valor nulo](../../../csharp/programming-guide/nullable-types/boxing-nullable-types.md)  
  
-   [Operador ??](../../../csharp/language-reference/operators/null-conditional-operator.md)  
  
## <a name="c-language-specification"></a>Especificação da Linguagem C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Nullable>   
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)   
 [C#](../../../csharp/index.md)   
 [Referência de C#](../../../csharp/language-reference/index.md)   
 [O que exatamente "levantado" significa?](http://go.microsoft.com/fwlink/?LinkId=112382)

