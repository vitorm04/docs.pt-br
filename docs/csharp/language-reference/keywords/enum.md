---
title: "enum (Referência de C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- enum
- enum_CSharpKeyword
helpviewer_keywords: enum keyword [C#]
ms.assetid: bbeb9a0f-e9b3-41ab-b0a6-c41b1a08974c
caps.latest.revision: "36"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 00ae9b555ae73db445fe4a4facf00753bf8c759a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="enum-c-reference"></a><span data-ttu-id="db723-102">enum (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="db723-102">enum (C# Reference)</span></span>
<span data-ttu-id="db723-103">A palavra-chave `enum` é usada para declarar uma enumeração, um tipo distinto que consiste em um conjunto de constantes nomeadas denominado lista de enumeradores.</span><span class="sxs-lookup"><span data-stu-id="db723-103">The `enum` keyword is used to declare an enumeration, a distinct type that consists of a set of named constants called the enumerator list.</span></span>  
  
 <span data-ttu-id="db723-104">Normalmente, é melhor definir um enum diretamente dentro de um namespace para que todas as classes no namespace possam acessá-lo com a mesma conveniência.</span><span class="sxs-lookup"><span data-stu-id="db723-104">Usually it is best to define an enum directly within a namespace so that all classes in the namespace can access it with equal convenience.</span></span> <span data-ttu-id="db723-105">No entanto, um enum também pode ser aninhado dentro de uma classe ou struct.</span><span class="sxs-lookup"><span data-stu-id="db723-105">However, an enum can also be nested within a class or struct.</span></span>  
  
 <span data-ttu-id="db723-106">Por padrão, o primeiro enumerador tem o valor 0 e o valor de cada enumerador seguinte é aumentado em 1.</span><span class="sxs-lookup"><span data-stu-id="db723-106">By default, the first enumerator has the value 0, and the value of each successive enumerator is increased by 1.</span></span> <span data-ttu-id="db723-107">Por exemplo, na seguinte enumeração, `Sat` é `0`, `Sun` é `1`, `Mon` é `2` e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="db723-107">For example, in the following enumeration, `Sat` is `0`, `Sun` is `1`, `Mon` is `2`, and so forth.</span></span>  
  
```  
enum Days {Sat, Sun, Mon, Tue, Wed, Thu, Fri};  
```  
  
 <span data-ttu-id="db723-108">Enumeradores podem usar inicializadores para substituir os valores padrão, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="db723-108">Enumerators can use initializers to override the default values, as shown in the following example.</span></span>  
  
```  
enum Days {Sat=1, Sun, Mon, Tue, Wed, Thu, Fri};  
```  
  
 <span data-ttu-id="db723-109">Nesta enumeração, a sequência de elementos é forçada a iniciar a partir de `1` em vez de `0`.</span><span class="sxs-lookup"><span data-stu-id="db723-109">In this enumeration, the sequence of elements is forced to start from `1` instead of `0`.</span></span> <span data-ttu-id="db723-110">No entanto, incluir uma constante que tenha o valor de 0 é recomendado.</span><span class="sxs-lookup"><span data-stu-id="db723-110">However, including a constant that has the value of 0 is recommended.</span></span> <span data-ttu-id="db723-111">Para obter mais informações, consulte [Tipos de enumeração](../../../csharp/programming-guide/enumeration-types.md).</span><span class="sxs-lookup"><span data-stu-id="db723-111">For more information, see [Enumeration Types](../../../csharp/programming-guide/enumeration-types.md).</span></span>  
  
 <span data-ttu-id="db723-112">Cada tipo de enumeração tem um tipo subjacente, que pode ser qualquer tipo integral exceto por [char](../../../csharp/language-reference/keywords/char.md).</span><span class="sxs-lookup"><span data-stu-id="db723-112">Every enumeration type has an underlying type, which can be any integral type except [char](../../../csharp/language-reference/keywords/char.md).</span></span> <span data-ttu-id="db723-113">O tipo subjacente padrão dos elementos de enumeração é [int](../../../csharp/language-reference/keywords/int.md). Para declarar um enum de outro tipo integral, como [bytes](../../../csharp/language-reference/keywords/byte.md), use uma vírgula após o identificador seguida pelo tipo, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="db723-113">The default underlying type of enumeration elements is [int](../../../csharp/language-reference/keywords/int.md). To declare an enum of another integral type, such as [byte](../../../csharp/language-reference/keywords/byte.md), use a colon after the identifier followed by the type, as shown in the following example.</span></span>  
  
```  
enum Days : byte {Sat=1, Sun, Mon, Tue, Wed, Thu, Fri};  
```  
  
 <span data-ttu-id="db723-114">Os tipos aprovados para um enum são `byte`, [sbyte](../../../csharp/language-reference/keywords/sbyte.md), [short](../../../csharp/language-reference/keywords/short.md), [ushort](../../../csharp/language-reference/keywords/ushort.md), [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), [long](../../../csharp/language-reference/keywords/long.md) ou [ulong](../../../csharp/language-reference/keywords/ulong.md).</span><span class="sxs-lookup"><span data-stu-id="db723-114">The approved types for an enum are `byte`, [sbyte](../../../csharp/language-reference/keywords/sbyte.md), [short](../../../csharp/language-reference/keywords/short.md), [ushort](../../../csharp/language-reference/keywords/ushort.md), [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), [long](../../../csharp/language-reference/keywords/long.md), or [ulong](../../../csharp/language-reference/keywords/ulong.md).</span></span>  
  
 <span data-ttu-id="db723-115">Qualquer valor no intervalo do tipo subjacente pode ser atribuído a uma variável do tipo `Days`; os valores não são limitados às constantes nomeadas.</span><span class="sxs-lookup"><span data-stu-id="db723-115">A variable of type `Days` can be assigned any value in the range of the underlying type; the values are not limited to the named constants.</span></span>  
  
 <span data-ttu-id="db723-116">O valor padrão de um `enum E` é o valor produzido pela expressão `(E)0`.</span><span class="sxs-lookup"><span data-stu-id="db723-116">The default value of an `enum E` is the value produced by the expression `(E)0`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="db723-117">Um enumerador não pode conter espaços em branco em seu nome.</span><span class="sxs-lookup"><span data-stu-id="db723-117">An enumerator cannot contain white space in its name.</span></span>  
  
 <span data-ttu-id="db723-118">O tipo subjacente especifica quanto armazenamento é alocado para cada enumerador.</span><span class="sxs-lookup"><span data-stu-id="db723-118">The underlying type specifies how much storage is allocated for each enumerator.</span></span> <span data-ttu-id="db723-119">No entanto, uma conversão explícita é necessária para converter de um tipo `enum` em um tipo integral.</span><span class="sxs-lookup"><span data-stu-id="db723-119">However, an explicit cast is necessary to convert from `enum` type to an integral type.</span></span> <span data-ttu-id="db723-120">Por exemplo, a instrução a seguir atribui o enumerador `Sun` a uma variável do tipo [int](../../../csharp/language-reference/keywords/int.md) usando uma conversão para converter de `enum` em `int`.</span><span class="sxs-lookup"><span data-stu-id="db723-120">For example, the following statement assigns the enumerator `Sun` to a variable of the type [int](../../../csharp/language-reference/keywords/int.md) by using a cast to convert from `enum` to `int`.</span></span>  
  
```  
int x = (int)Days.Sun;  
```  
  
 <span data-ttu-id="db723-121">Quando você aplica <xref:System.FlagsAttribute?displayProperty=nameWithType> a uma enumeração que contém elementos que podem ser combinados com uma operação `OR` bit a bit, o atributo afeta o comportamento do `enum` quando ele é usado com algumas ferramentas.</span><span class="sxs-lookup"><span data-stu-id="db723-121">When you apply <xref:System.FlagsAttribute?displayProperty=nameWithType> to an enumeration that contains elements that can be combined with a bitwise `OR` operation, the attribute affects the behavior of the `enum` when it is used with some tools.</span></span> <span data-ttu-id="db723-122">Você pode observar essas alterações quando usa ferramentas como os métodos da classe <xref:System.Console> e o Avaliador de Expressão.</span><span class="sxs-lookup"><span data-stu-id="db723-122">You can notice these changes when you use tools such as the <xref:System.Console> class methods and the Expression Evaluator.</span></span> <span data-ttu-id="db723-123">(Consulte o terceiro exemplo.)</span><span class="sxs-lookup"><span data-stu-id="db723-123">(See the third example.)</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="db723-124">Programação robusta</span><span class="sxs-lookup"><span data-stu-id="db723-124">Robust Programming</span></span>  
 <span data-ttu-id="db723-125">Assim como ocorre com qualquer constante, todas as referências aos valores individuais de um enum são convertidas em literais numéricos em tempo de compilação.</span><span class="sxs-lookup"><span data-stu-id="db723-125">Just as with any constant, all references to the individual values of an enum are converted to numeric literals at compile time.</span></span> <span data-ttu-id="db723-126">Isso pode criar problemas de controle de versão, conforme descrito em [Constantes](../../../csharp/programming-guide/classes-and-structs/constants.md).</span><span class="sxs-lookup"><span data-stu-id="db723-126">This can create potential versioning issues as described in [Constants](../../../csharp/programming-guide/classes-and-structs/constants.md).</span></span>  
  
 <span data-ttu-id="db723-127">Atribuir valores adicionais a novas versões de enums ou alterar os valores dos membros de enum em uma nova versão pode causar problemas para códigos-fonte dependentes.</span><span class="sxs-lookup"><span data-stu-id="db723-127">Assigning additional values to new versions of enums, or changing the values of the enum members in a new version, can cause problems for dependent source code.</span></span> <span data-ttu-id="db723-128">Valores de enum frequentemente são usados em instruções [switch](../../../csharp/language-reference/keywords/switch.md).</span><span class="sxs-lookup"><span data-stu-id="db723-128">Enum values often are used in [switch](../../../csharp/language-reference/keywords/switch.md) statements.</span></span> <span data-ttu-id="db723-129">Se elementos adicionais tiverem sido adicionados ao tipo `enum`, a seção padrão da instrução switch pode ser selecionada inesperadamente.</span><span class="sxs-lookup"><span data-stu-id="db723-129">If additional elements have been added to the `enum` type, the default section of the switch statement can be selected unexpectedly.</span></span>  
  
 <span data-ttu-id="db723-130">Se outros desenvolvedores usarem seu código, você deverá fornecer diretrizes sobre como seu código deve reagir se novos elementos forem adicionados a qualquer tipo `enum`.</span><span class="sxs-lookup"><span data-stu-id="db723-130">If other developers use your code, you should provide guidelines about how their code should react if new elements are added to any `enum` types.</span></span>  
  
## <a name="example"></a><span data-ttu-id="db723-131">Exemplo</span><span class="sxs-lookup"><span data-stu-id="db723-131">Example</span></span>  
 <span data-ttu-id="db723-132">No exemplo a seguir, uma enumeração, `Days`, é declarada.</span><span class="sxs-lookup"><span data-stu-id="db723-132">In the following example, an enumeration, `Days`, is declared.</span></span> <span data-ttu-id="db723-133">Dois enumeradores são convertidos explicitamente em inteiros e atribuídos a variáveis de inteiro.</span><span class="sxs-lookup"><span data-stu-id="db723-133">Two enumerators are explicitly converted to integer and assigned to integer variables.</span></span>  
  
 [!code-csharp[csrefKeywordsTypes#10](../../../csharp/language-reference/keywords/codesnippet/CSharp/enum_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="db723-134">Exemplo</span><span class="sxs-lookup"><span data-stu-id="db723-134">Example</span></span>  
 <span data-ttu-id="db723-135">No exemplo a seguir, a opção de tipo base é usada para declarar uma `enum` cujos membros são do tipo `long`.</span><span class="sxs-lookup"><span data-stu-id="db723-135">In the following example, the base-type option is used to declare an `enum` whose members are of type `long`.</span></span> <span data-ttu-id="db723-136">Observe que, mesmo que o tipo subjacente da enumeração seja `long`, os membros da enumeração ainda devem ser convertidos explicitamente no tipo `long` usando uma conversão.</span><span class="sxs-lookup"><span data-stu-id="db723-136">Notice that even though the underlying type of the enumeration is `long`, the enumeration members still must be explicitly converted to type `long` by using a cast.</span></span>  
  
 [!code-csharp[csrefKeywordsTypes#11](../../../csharp/language-reference/keywords/codesnippet/CSharp/enum_2.cs)]  
  
## <a name="example"></a><span data-ttu-id="db723-137">Exemplo</span><span class="sxs-lookup"><span data-stu-id="db723-137">Example</span></span>  
 <span data-ttu-id="db723-138">O exemplo de código a seguir ilustra o uso e o efeito do atributo <xref:System.FlagsAttribute?displayProperty=nameWithType> em uma declaração `enum`.</span><span class="sxs-lookup"><span data-stu-id="db723-138">The following code example illustrates the use and effect of the <xref:System.FlagsAttribute?displayProperty=nameWithType> attribute on an `enum` declaration.</span></span>  
  
 [!code-csharp[csrefKeywordsTypes#12](../../../csharp/language-reference/keywords/codesnippet/CSharp/enum_3.cs)]  
  
## <a name="comments"></a><span data-ttu-id="db723-139">Comentários</span><span class="sxs-lookup"><span data-stu-id="db723-139">Comments</span></span>  
 <span data-ttu-id="db723-140">Se você remover `Flags`, o exemplo exibirá os seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="db723-140">If you remove `Flags`, the example displays the following values:</span></span>  
  
 `5`  
  
 `5`  
  
## <a name="c-language-specification"></a><span data-ttu-id="db723-141">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="db723-141">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="db723-142">Consulte também</span><span class="sxs-lookup"><span data-stu-id="db723-142">See Also</span></span>  
 [<span data-ttu-id="db723-143">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="db723-143">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="db723-144">Tipos de enumeração</span><span class="sxs-lookup"><span data-stu-id="db723-144">Enumeration Types</span></span>](../../../csharp/programming-guide/enumeration-types.md)  
 [<span data-ttu-id="db723-145">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="db723-145">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="db723-146">Tabela de tipos integrais</span><span class="sxs-lookup"><span data-stu-id="db723-146">Integral Types Table</span></span>](../../../csharp/language-reference/keywords/integral-types-table.md)  
 [<span data-ttu-id="db723-147">Tabela de tipos internos</span><span class="sxs-lookup"><span data-stu-id="db723-147">Built-In Types Table</span></span>](../../../csharp/language-reference/keywords/built-in-types-table.md)  
 [<span data-ttu-id="db723-148">Tabela de conversões numéricas implícitas</span><span class="sxs-lookup"><span data-stu-id="db723-148">Implicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)  
 [<span data-ttu-id="db723-149">Tabela de conversões numéricas explícitas</span><span class="sxs-lookup"><span data-stu-id="db723-149">Explicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)
