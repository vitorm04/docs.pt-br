---
title: "Tipos de enumeração (Guia de Programação em C#)"
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 677de7c6e0c0f72b600ce8ee5a8bad265725f6d3
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="enumeration-types-c-programming-guide"></a><span data-ttu-id="974cd-102">Tipos de enumeração (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="974cd-102">Enumeration Types (C# Programming Guide)</span></span>
<span data-ttu-id="974cd-103">Um tipo de enumeração (também chamado de uma enumeração ou enum) fornece uma maneira eficiente para definir um conjunto de constantes integrais nomeadas que podem ser atribuídas a um valor.</span><span class="sxs-lookup"><span data-stu-id="974cd-103">An enumeration type (also named an enumeration or an enum) provides an efficient way to define a set of named integral constants that may be assigned to a variable.</span></span> <span data-ttu-id="974cd-104">Por exemplo, suponha que você precisa definir uma variável cujo valor representará um dia da semana.</span><span class="sxs-lookup"><span data-stu-id="974cd-104">For example, assume that you have to define a variable whose value will represent a day of the week.</span></span> <span data-ttu-id="974cd-105">Há apenas sete valores significativos que essa variável armazenará.</span><span class="sxs-lookup"><span data-stu-id="974cd-105">There are only seven meaningful values which that variable will ever store.</span></span> <span data-ttu-id="974cd-106">Para definir esses valores, você pode usar um tipo de enumeração, que é declarado usando a palavra-chave [enum](../../csharp/language-reference/keywords/enum.md).</span><span class="sxs-lookup"><span data-stu-id="974cd-106">To define those values, you can use an enumeration type, which is declared by using the [enum](../../csharp/language-reference/keywords/enum.md) keyword.</span></span>  
  
 <span data-ttu-id="974cd-107">[!code-cs[csProgGuideEnums#1](../../csharp/programming-guide/codesnippet/CSharp/enumeration-types_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="974cd-107">[!code-cs[csProgGuideEnums#1](../../csharp/programming-guide/codesnippet/CSharp/enumeration-types_1.cs)]</span></span>  
  
 <span data-ttu-id="974cd-108">Por padrão o tipo subjacente de cada elemento na enumeração é [int](../../csharp/language-reference/keywords/int.md).</span><span class="sxs-lookup"><span data-stu-id="974cd-108">By default the underlying type of each element in the enum is [int](../../csharp/language-reference/keywords/int.md).</span></span> <span data-ttu-id="974cd-109">Você pode especificar outro tipo numérico integral usando dois-pontos, como mostrado no exemplo anterior.</span><span class="sxs-lookup"><span data-stu-id="974cd-109">You can specify another integral numeric type by using a colon, as shown in the previous example.</span></span> <span data-ttu-id="974cd-110">Para obter uma lista completa dos tipos possíveis, consulte [enum (Referência de C#)](../../csharp/language-reference/keywords/enum.md).</span><span class="sxs-lookup"><span data-stu-id="974cd-110">For a full list of possible types, see [enum (C# Reference)](../../csharp/language-reference/keywords/enum.md).</span></span>  
  
 <span data-ttu-id="974cd-111">Você pode verificar os valores numéricos subjacentes com a conversão em tipo subjacente, como mostra o exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="974cd-111">You can verify the underlying numeric values by casting  to the underlying type, as the following example shows.</span></span>  
  
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
  
 <span data-ttu-id="974cd-112">A seguir estão as vantagens de usar uma enumeração, em vez de um tipo numérico:</span><span class="sxs-lookup"><span data-stu-id="974cd-112">The following are advantages of using an enum instead of a numeric type:</span></span>  
  
-   <span data-ttu-id="974cd-113">Você especifica claramente para o código do cliente quais valores são válidos para a variável.</span><span class="sxs-lookup"><span data-stu-id="974cd-113">You clearly specify for client code which values are valid for the variable.</span></span>  
  
-   <span data-ttu-id="974cd-114">Em [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)], o IntelliSense lista os valores definidos.</span><span class="sxs-lookup"><span data-stu-id="974cd-114">In [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)], IntelliSense lists the defined values.</span></span>  
  
 <span data-ttu-id="974cd-115">Quando você não especifica valores para os elementos na lista de enumerador, os valores são automaticamente incrementados em 1.</span><span class="sxs-lookup"><span data-stu-id="974cd-115">When you do not specify values for the elements in the enumerator list, the values are automatically incremented by 1.</span></span> <span data-ttu-id="974cd-116">No exemplo anterior, `Days.Sunday` tem um valor de 0, `Days.Monday` tem um valor de 1 e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="974cd-116">In the previous example, `Days.Sunday` has a value of 0, `Days.Monday` has a value of 1, and so on.</span></span> <span data-ttu-id="974cd-117">Ao criar um novo objeto `Days`, ele terá um valor padrão de `Days.Sunday` (0) se você não atribuir explicitamente um valor a ele.</span><span class="sxs-lookup"><span data-stu-id="974cd-117">When you create a new `Days` object, it will have a default value of `Days.Sunday` (0) if you do not explicitly assign it a value.</span></span> <span data-ttu-id="974cd-118">Quando você criar uma enumeração, selecione o valor padrão mais lógico e forneça a ele um valor igual a zero.</span><span class="sxs-lookup"><span data-stu-id="974cd-118">When you create an enum, select the most logical default value and give it a value of zero.</span></span> <span data-ttu-id="974cd-119">Isso fará com que todos os enumeradores tenham esse valor padrão se eles não tiverem um valor explicitamente atribuído quando forem criados.</span><span class="sxs-lookup"><span data-stu-id="974cd-119">That will cause all enums to have that default value if they are not explicitly assigned a value when they are created.</span></span>  
  
 <span data-ttu-id="974cd-120">Se a variável `meetingDay` for do tipo `Days`, (sem uma conversão explícita) você pode apenas atribuir a ele um dos valores definidos por `Days`.</span><span class="sxs-lookup"><span data-stu-id="974cd-120">If the variable `meetingDay` is of type `Days`, then (without an explicit cast) you can only assign it one of the values defined by `Days`.</span></span> <span data-ttu-id="974cd-121">E se o dia da reunião for alterado, você poderá atribuir um novo valor de `Days` para `meetingDay`:</span><span class="sxs-lookup"><span data-stu-id="974cd-121">And if the meeting day changes, you can assign a new value from `Days` to `meetingDay`:</span></span>  
  
 <span data-ttu-id="974cd-122">[!code-cs[csProgGuideEnums#4](../../csharp/programming-guide/codesnippet/CSharp/enumeration-types_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="974cd-122">[!code-cs[csProgGuideEnums#4](../../csharp/programming-guide/codesnippet/CSharp/enumeration-types_2.cs)]</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="974cd-123">É possível atribuir qualquer valor inteiro arbitrário a `meetingDay`.</span><span class="sxs-lookup"><span data-stu-id="974cd-123">It is possible to assign any arbitrary integer value to `meetingDay`.</span></span> <span data-ttu-id="974cd-124">Por exemplo, esta linha de código não produz um erro: `meetingDay = (Days) 42`.</span><span class="sxs-lookup"><span data-stu-id="974cd-124">For example, this line of code does not produce an error: `meetingDay = (Days) 42`.</span></span> <span data-ttu-id="974cd-125">No entanto, você não deve fazer isso porque a expectativa implícita é que uma variável enum conterá apenas um dos valores definidos pela enumeração.</span><span class="sxs-lookup"><span data-stu-id="974cd-125">However, you should not do this because the implicit expectation is that an enum variable will only hold one of the values defined by the enum.</span></span> <span data-ttu-id="974cd-126">Atribuir um valor arbitrário a uma variável de um tipo de enumeração é introduzir um alto risco de erros.</span><span class="sxs-lookup"><span data-stu-id="974cd-126">To assign an arbitrary value to a variable of an enumeration type is to introduce a high risk for errors.</span></span>  
  
 <span data-ttu-id="974cd-127">Você pode atribuir quaisquer valores aos elementos na lista de enumeradores de um tipo de enumeração e também pode usar valores computados:</span><span class="sxs-lookup"><span data-stu-id="974cd-127">You can assign any values to the elements in the enumerator list of an enumeration type, and you can also use computed values:</span></span>  
  
 <span data-ttu-id="974cd-128">[!code-cs[csProgGuideEnums#3](../../csharp/programming-guide/codesnippet/CSharp/enumeration-types_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="974cd-128">[!code-cs[csProgGuideEnums#3](../../csharp/programming-guide/codesnippet/CSharp/enumeration-types_3.cs)]</span></span>  
  
## <a name="enumeration-types-as-bit-flags"></a><span data-ttu-id="974cd-129">Tipos de Enumeração como Sinalizadores de Bit</span><span class="sxs-lookup"><span data-stu-id="974cd-129">Enumeration Types as Bit Flags</span></span>  
 <span data-ttu-id="974cd-130">Você pode usar um tipo de enumeração para definir sinalizadores de bits, que permite que uma instância do tipo de enumeração armazenar qualquer combinação dos valores que são definidos na lista de enumeradores.</span><span class="sxs-lookup"><span data-stu-id="974cd-130">You can use an enumeration type to define bit flags, which enables an instance of the enumeration type to store any combination of the values that are defined in the enumerator list.</span></span> <span data-ttu-id="974cd-131">(Claro, algumas combinações podem não ser significativas ou permitidas em seu código de programa.)</span><span class="sxs-lookup"><span data-stu-id="974cd-131">(Of course, some combinations may not be meaningful or allowed in your program code.)</span></span>  
  
 <span data-ttu-id="974cd-132">Crie uma enumeração de sinalizadores de bits aplicando o atributo <xref:System.FlagsAttribute?displayProperty=fullName> e definindo os valores apropriadamente para que operações bit a bit `AND`, `OR`, `NOT` e `XOR` possam ser executadas neles.</span><span class="sxs-lookup"><span data-stu-id="974cd-132">You create a bit flags enum by applying the <xref:System.FlagsAttribute?displayProperty=fullName> attribute and defining the values appropriately so that `AND`, `OR`, `NOT` and `XOR` bitwise operations can be performed on them.</span></span> <span data-ttu-id="974cd-133">Em uma enumeração de sinalizadores de bits, inclua uma constante nomeada com um valor de zero que significa “nenhum sinalizador está definido”.</span><span class="sxs-lookup"><span data-stu-id="974cd-133">In a bit flags enum, include a named constant with a value of zero that means "no flags are set."</span></span> <span data-ttu-id="974cd-134">Não forneça um valor de zero a um sinalizador se isso não significar “nenhum sinalizador está definido”.</span><span class="sxs-lookup"><span data-stu-id="974cd-134">Do not give a flag a value of zero if it does not mean "no flags are set".</span></span>  
  
 <span data-ttu-id="974cd-135">No exemplo a seguir, outra versão da enumeração `Days`, que é chamada de `Days2`, é definida.</span><span class="sxs-lookup"><span data-stu-id="974cd-135">In the following example, another version of the `Days` enum, which is named `Days2`, is defined.</span></span> <span data-ttu-id="974cd-136">`Days2` tem o atributo `Flags` e a cada valor é atribuída a próxima maior potência de 2.</span><span class="sxs-lookup"><span data-stu-id="974cd-136">`Days2` has the `Flags` attribute and each value is assigned the next greater power of 2.</span></span> <span data-ttu-id="974cd-137">Isso permite que você crie uma variável `Days2` cujo valor é `Days2.Tuesday` e `Days2.Thursday`.</span><span class="sxs-lookup"><span data-stu-id="974cd-137">This enables you to create a `Days2` variable whose value is `Days2.Tuesday` and `Days2.Thursday`.</span></span>  
  
 <span data-ttu-id="974cd-138">[!code-cs[csProgGuideEnums#2](../../csharp/programming-guide/codesnippet/CSharp/enumeration-types_4.cs)]</span><span class="sxs-lookup"><span data-stu-id="974cd-138">[!code-cs[csProgGuideEnums#2](../../csharp/programming-guide/codesnippet/CSharp/enumeration-types_4.cs)]</span></span>  
  
 <span data-ttu-id="974cd-139">Para definir um sinalizador em uma enumeração, use o operador `OR` de bit a bit mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="974cd-139">To set a flag on an enum, use the bitwise `OR` operator as shown in the following example:</span></span>  
  
 <span data-ttu-id="974cd-140">[!code-cs[csProgGuideEnums#6](../../csharp/programming-guide/codesnippet/CSharp/enumeration-types_5.cs)]</span><span class="sxs-lookup"><span data-stu-id="974cd-140">[!code-cs[csProgGuideEnums#6](../../csharp/programming-guide/codesnippet/CSharp/enumeration-types_5.cs)]</span></span>  
  
 <span data-ttu-id="974cd-141">Para determinar se um sinalizador específico é definido, use uma operação `AND` bit a bit, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="974cd-141">To determine whether a specific flag is set, use a bitwise `AND` operation, as shown in the following example:</span></span>  
  
 <span data-ttu-id="974cd-142">[!code-cs[csProgGuideEnums#7](../../csharp/programming-guide/codesnippet/CSharp/enumeration-types_6.cs)]</span><span class="sxs-lookup"><span data-stu-id="974cd-142">[!code-cs[csProgGuideEnums#7](../../csharp/programming-guide/codesnippet/CSharp/enumeration-types_6.cs)]</span></span>  
  
 <span data-ttu-id="974cd-143">Para saber mais sobre o que considerar ao definir tipos de enumeração com o atributo <xref:System.FlagsAttribute?displayProperty=fullName>, veja <xref:System.Enum?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="974cd-143">For more information about what to consider when you define enumeration types with the <xref:System.FlagsAttribute?displayProperty=fullName> attribute, see <xref:System.Enum?displayProperty=fullName>.</span></span>  
  
## <a name="using-the-systemenum-methods-to-discover-and-manipulate-enum-values"></a><span data-ttu-id="974cd-144">Usando os Métodos System.Enum Methods para Descobrir e Manipular Valores Enum</span><span class="sxs-lookup"><span data-stu-id="974cd-144">Using the System.Enum Methods to Discover and Manipulate Enum Values</span></span>  
 <span data-ttu-id="974cd-145">Todas as enumerações são instâncias do tipo <xref:System.Enum?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="974cd-145">All enums are instances of the <xref:System.Enum?displayProperty=fullName> type.</span></span> <span data-ttu-id="974cd-146">Não é possível derivar novas classes de <xref:System.Enum?displayProperty=fullName>, mas você pode usar seus métodos para descobrir informações sobre e manipular valores em uma instância de enumeração.</span><span class="sxs-lookup"><span data-stu-id="974cd-146">You cannot derive new classes from <xref:System.Enum?displayProperty=fullName>, but you can use its methods to discover information about and manipulate values in an enum instance.</span></span>  
  
 <span data-ttu-id="974cd-147">[!code-cs[csProgGuideEnums#5](../../csharp/programming-guide/codesnippet/CSharp/enumeration-types_7.cs)]</span><span class="sxs-lookup"><span data-stu-id="974cd-147">[!code-cs[csProgGuideEnums#5](../../csharp/programming-guide/codesnippet/CSharp/enumeration-types_7.cs)]</span></span>  
  
 <span data-ttu-id="974cd-148">Para obter mais informações, consulte <xref:System.Enum?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="974cd-148">For more information, see <xref:System.Enum?displayProperty=fullName>.</span></span>  
  
 <span data-ttu-id="974cd-149">Você também pode criar um novo método para uma enumeração usando um método de extensão.</span><span class="sxs-lookup"><span data-stu-id="974cd-149">You can also create a new method for an enum by using an extension method.</span></span> <span data-ttu-id="974cd-150">Para obter mais informações, consulte [Como criar um novo método para uma enumeração](../../csharp/programming-guide/classes-and-structs/how-to-create-a-new-method-for-an-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="974cd-150">For more information, see [How to: Create a New Method for an Enumeration](../../csharp/programming-guide/classes-and-structs/how-to-create-a-new-method-for-an-enumeration.md).</span></span>  

## <a name="see-also"></a><span data-ttu-id="974cd-151">Consulte também</span><span class="sxs-lookup"><span data-stu-id="974cd-151">See Also</span></span>  
 <span data-ttu-id="974cd-152"><xref:System.Enum?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="974cd-152"><xref:System.Enum?displayProperty=fullName></span></span>   
 <span data-ttu-id="974cd-153">[Guia de Programação em C#](../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="974cd-153">[C# Programming Guide](../../csharp/programming-guide/index.md) </span></span>  
 [<span data-ttu-id="974cd-154">enum</span><span class="sxs-lookup"><span data-stu-id="974cd-154">enum</span></span>](../../csharp/language-reference/keywords/enum.md)

