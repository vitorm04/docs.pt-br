---
title: "Tipos de enumeração (Guia de Programação em C#) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- enumerations [C#]
- enums [C#]
- C# Language, enums
- bit flags [C#]
ms.assetid: 64a9b731-9e3c-4336-8a09-018db2aa10b7
caps.latest.revision: 17
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
ms.openlocfilehash: 8c23c17967474af0f91c0dda6d071073234736c6
ms.lasthandoff: 03/13/2017

---
# <a name="enumeration-types-c-programming-guide"></a>Tipos de enumeração (Guia de Programação em C#)
Um tipo de enumeração (também chamado de uma enumeração ou enum) fornece uma maneira eficiente para definir um conjunto de constantes integrais nomeadas que podem ser atribuídas a um valor. Por exemplo, suponha que você precisa definir uma variável cujo valor representará um dia da semana. Há apenas sete valores significativos que essa variável armazenará. Para definir esses valores, você pode usar um tipo de enumeração, que é declarado usando a palavra-chave [enum](../../csharp/language-reference/keywords/enum.md).  
  
 [!code-cs[csProgGuideEnums#1](../../csharp/programming-guide/codesnippet/CSharp/enumeration-types_1.cs)]  
  
 Por padrão o tipo subjacente de cada elemento na enumeração é [int](../../csharp/language-reference/keywords/int.md). Você pode especificar outro tipo numérico integral usando dois-pontos, como mostrado no exemplo anterior. Para obter uma lista completa dos tipos possíveis, consulte [enum (Referência de C#)](../../csharp/language-reference/keywords/enum.md).  
  
 Você pode verificar os valores numéricos subjacentes com a conversão em tipo subjacente, como mostra o exemplo a seguir.  
  
```csharp  
Days today = Days.Monday;  
int dayNumber =(int)today;  
Console.WriteLine("{0} is day number #{1}.", today, dayNumber);  
  
Months thisMonth = Months.Dec;  
byte monthNumber = (byte)thisMonth;  
Console.WriteLine("{0} is month number #{1}.", thisMonth, monthNumber);  
  
// Output:  
// Monday is day number #1.  
// Dec is month number #11.  
```  
  
 A seguir estão as vantagens de usar uma enumeração, em vez de um tipo numérico:  
  
-   Você especifica claramente para o código do cliente quais valores são válidos para a variável.  
  
-   Em [!INCLUDE[vsprvs](../../csharp/includes/vsprvs_md.md)], o IntelliSense lista os valores definidos.  
  
 Quando você não especifica valores para os elementos na lista de enumerador, os valores são automaticamente incrementados em 1. No exemplo anterior, `Days.Sunday` tem um valor de 0, `Days.Monday` tem um valor de 1 e assim por diante. Ao criar um novo objeto `Days`, ele terá um valor padrão de `Days.Sunday` (0) se você não atribuir explicitamente um valor a ele. Quando você criar uma enumeração, selecione o valor padrão mais lógico e forneça a ele um valor igual a zero. Isso fará com que todos os enumeradores tenham esse valor padrão se eles não tiverem um valor explicitamente atribuído quando forem criados.  
  
 Se a variável `meetingDay` for do tipo `Days`, (sem uma conversão explícita) você pode apenas atribuir a ele um dos valores definidos por `Days`. E se o dia da reunião for alterado, você poderá atribuir um novo valor de `Days` para `meetingDay`:  
  
 [!code-cs[csProgGuideEnums#4](../../csharp/programming-guide/codesnippet/CSharp/enumeration-types_2.cs)]  
  
> [!NOTE]
>  É possível atribuir qualquer valor inteiro arbitrário a `meetingDay`. Por exemplo, esta linha de código não produz um erro: `meetingDay = (Days) 42`. No entanto, você não deve fazer isso porque a expectativa implícita é que uma variável enum conterá apenas um dos valores definidos pela enumeração. Atribuir um valor arbitrário a uma variável de um tipo de enumeração é introduzir um alto risco de erros.  
  
 Você pode atribuir quaisquer valores aos elementos na lista de enumeradores de um tipo de enumeração e também pode usar valores computados:  
  
 [!code-cs[csProgGuideEnums#3](../../csharp/programming-guide/codesnippet/CSharp/enumeration-types_3.cs)]  
  
## <a name="enumeration-types-as-bit-flags"></a>Tipos de Enumeração como Sinalizadores de Bit  
 Você pode usar um tipo de enumeração para definir sinalizadores de bits, que permite que uma instância do tipo de enumeração armazenar qualquer combinação dos valores que são definidos na lista de enumeradores. (Claro, algumas combinações podem não ser significativas ou permitidas em seu código de programa.)  
  
 Crie uma enumeração de sinalizadores de bits aplicando o atributo <xref:System.FlagsAttribute?displayProperty=fullName> e definindo os valores apropriadamente para que operações bit a bit `AND`, `OR`, `NOT` e `XOR` possam ser executadas neles. Em uma enumeração de sinalizadores de bits, inclua uma constante nomeada com um valor de zero que significa “nenhum sinalizador está definido”. Não forneça um valor de zero a um sinalizador se isso não significar “nenhum sinalizador está definido”.  
  
 No exemplo a seguir, outra versão da enumeração `Days`, que é chamada de `Days2`, é definida. `Days2` tem o atributo `Flags` e a cada valor é atribuída a próxima maior potência de 2. Isso permite que você crie uma variável `Days2` cujo valor é `Days2.Tuesday` e `Days2.Thursday`.  
  
 [!code-cs[csProgGuideEnums#2](../../csharp/programming-guide/codesnippet/CSharp/enumeration-types_4.cs)]  
  
 Para definir um sinalizador em uma enumeração, use o operador `OR` de bit a bit mostrado no exemplo a seguir:  
  
 [!code-cs[csProgGuideEnums#6](../../csharp/programming-guide/codesnippet/CSharp/enumeration-types_5.cs)]  
  
 Para determinar se um sinalizador específico é definido, use uma operação `AND` bit a bit, conforme mostrado no exemplo a seguir:  
  
 [!code-cs[csProgGuideEnums#7](../../csharp/programming-guide/codesnippet/CSharp/enumeration-types_6.cs)]  
  
 Para obter mais informações sobre o que considerar ao definir os tipos de enumeração com o atributo <xref:System.FlagsAttribute?displayProperty=fullName>, consulte <xref:System.Enum?displayProperty=fullName>.  
  
## <a name="using-the-systemenum-methods-to-discover-and-manipulate-enum-values"></a>Usando os Métodos System.Enum Methods para Descobrir e Manipular Valores Enum  
 Todas as enumerações são instâncias do tipo <xref:System.Enum?displayProperty=fullName>. Não é possível derivar novas classes de <xref:System.Enum?displayProperty=fullName>, mas você pode usar seus métodos para descobrir informações sobre e manipular valores em uma instância de enumeração.  
  
 [!code-cs[csProgGuideEnums#5](../../csharp/programming-guide/codesnippet/CSharp/enumeration-types_7.cs)]  
  
 Para obter mais informações, consulte <xref:System.Enum?displayProperty=fullName>.  
  
 Você também pode criar um novo método para uma enumeração usando um método de extensão. Para obter mais informações, consulte [Como criar um novo método para uma enumeração](../../csharp/programming-guide/classes-and-structs/how-to-create-a-new-method-for-an-enumeration.md).  
  
## <a name="featured-book-chapter"></a>Capítulo do Livro em Destaque  
 [Mais informações sobre variáveis](http://go.microsoft.com/fwlink/?LinkId=221230) em [Beginning Visual C# 2010](http://go.microsoft.com/fwlink/?LinkId=221214) (Introdução ao Visual C# 2010)  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Enum?displayProperty=fullName>   
 [Guia de Programação em C#](../../csharp/programming-guide/index.md)   
 [enum](../../csharp/language-reference/keywords/enum.md)
