---
title: "bool (Referência de C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- bool_CSharpKeyword
- bool
dev_langs:
- CSharp
helpviewer_keywords:
- bool keyword [C#]
ms.assetid: 551cfe35-2632-4343-af49-33ad12da08e2
caps.latest.revision: 30
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
ms.openlocfilehash: f3b7455ab6b0ec780afe7d81b2ff990d47a31d20
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="bool-c-reference"></a><span data-ttu-id="dcfbf-102">bool (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="dcfbf-102">bool (C# Reference)</span></span>
<span data-ttu-id="dcfbf-103">A palavra-chave `bool` é um alias de <xref:System.Boolean?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="dcfbf-103">The `bool` keyword is an alias of <xref:System.Boolean?displayProperty=fullName>.</span></span> <span data-ttu-id="dcfbf-104">Ela é usada para declarar variáveis para armazenar os valores boolianos [true](../../../csharp/language-reference/keywords/true.md) e [false](../../../csharp/language-reference/keywords/false.md).</span><span class="sxs-lookup"><span data-stu-id="dcfbf-104">It is used to declare variables to store the Boolean values, [true](../../../csharp/language-reference/keywords/true.md) and [false](../../../csharp/language-reference/keywords/false.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="dcfbf-105">Se você precisar de uma variável booliana que também pode ter um valor de `null`, use `bool?`.</span><span class="sxs-lookup"><span data-stu-id="dcfbf-105">If you require a Boolean variable that can also have a value of `null`, use `bool?`.</span></span> <span data-ttu-id="dcfbf-106">Para obter mais informações, consulte [Nullable Types (Tipos que permitem valores nulos)](../../../csharp/programming-guide/nullable-types/index.md).</span><span class="sxs-lookup"><span data-stu-id="dcfbf-106">For more information, see [Nullable Types](../../../csharp/programming-guide/nullable-types/index.md).</span></span>  
  
## <a name="literals"></a><span data-ttu-id="dcfbf-107">Literais</span><span class="sxs-lookup"><span data-stu-id="dcfbf-107">Literals</span></span>  
 <span data-ttu-id="dcfbf-108">Você pode atribuir um valor booliano a uma variável `bool`.</span><span class="sxs-lookup"><span data-stu-id="dcfbf-108">You can assign a Boolean value to a `bool` variable.</span></span> <span data-ttu-id="dcfbf-109">Você também pode atribuir uma expressão que é calculada como `bool` para um variável `bool`.</span><span class="sxs-lookup"><span data-stu-id="dcfbf-109">You can also assign an expression that evaluates to `bool` to a `bool` variable.</span></span>  
  
 <span data-ttu-id="dcfbf-110">[!code-cs[csrefKeywordsTypes#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/bool_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="dcfbf-110">[!code-cs[csrefKeywordsTypes#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/bool_1.cs)]</span></span>  
  
 <span data-ttu-id="dcfbf-111">O valor padrão de uma variável `bool` é `false`.</span><span class="sxs-lookup"><span data-stu-id="dcfbf-111">The default value of a `bool` variable is `false`.</span></span> <span data-ttu-id="dcfbf-112">O valor padrão de uma variável `bool?` é `null`.</span><span class="sxs-lookup"><span data-stu-id="dcfbf-112">The default value of a `bool?` variable is `null`.</span></span>  
  
## <a name="conversions"></a><span data-ttu-id="dcfbf-113">Conversões</span><span class="sxs-lookup"><span data-stu-id="dcfbf-113">Conversions</span></span>  
 <span data-ttu-id="dcfbf-114">No C++, um valor do tipo `bool` pode ser convertido em um valor do tipo `int`. Em outras palavras, `false` é equivalente a zero e `true` é equivalente a valores diferentes de zero.</span><span class="sxs-lookup"><span data-stu-id="dcfbf-114">In C++, a value of type `bool` can be converted to a value of type `int`; in other words, `false` is equivalent to zero and `true` is equivalent to nonzero values.</span></span> <span data-ttu-id="dcfbf-115">No C#, não há conversão entre o tipo `bool` e outros tipos.</span><span class="sxs-lookup"><span data-stu-id="dcfbf-115">In C#, there is no conversion between the `bool` type and other types.</span></span> <span data-ttu-id="dcfbf-116">Por exemplo, a seguinte instrução `if` é inválida no C#:</span><span class="sxs-lookup"><span data-stu-id="dcfbf-116">For example, the following `if` statement is invalid in C#:</span></span>  
  
 <span data-ttu-id="dcfbf-117">[!code-cs[csrefKeywordsTypes#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/bool_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="dcfbf-117">[!code-cs[csrefKeywordsTypes#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/bool_2.cs)]</span></span>  
  
 <span data-ttu-id="dcfbf-118">Para testar uma variável do tipo `int`, você precisa compará-la explicitamente com um valor, como zero, da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="dcfbf-118">To test a variable of the type `int`, you have to explicitly compare it to a value, such as zero, as follows:</span></span>  
  
 <span data-ttu-id="dcfbf-119">[!code-cs[csrefKeywordsTypes#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/bool_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="dcfbf-119">[!code-cs[csrefKeywordsTypes#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/bool_3.cs)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="dcfbf-120">Exemplo</span><span class="sxs-lookup"><span data-stu-id="dcfbf-120">Example</span></span>  
 <span data-ttu-id="dcfbf-121">Neste exemplo, você insere um caractere do teclado e o programa verifica se o caractere de entrada é uma letra.</span><span class="sxs-lookup"><span data-stu-id="dcfbf-121">In this example, you enter a character from the keyboard and the program checks if the input character is a letter.</span></span> <span data-ttu-id="dcfbf-122">Se for uma letra, ele verificará se é maiúscula ou minúscula.</span><span class="sxs-lookup"><span data-stu-id="dcfbf-122">If it is a letter, it checks if it is lowercase or uppercase.</span></span> <span data-ttu-id="dcfbf-123">Essas verificações são executadas com o <xref:System.Char.IsLetter%2A> e o <xref:System.Char.IsLower%2A>, ambos os quais retornam o tipo `bool`:</span><span class="sxs-lookup"><span data-stu-id="dcfbf-123">These checks are performed with the <xref:System.Char.IsLetter%2A>, and <xref:System.Char.IsLower%2A>, both of which return the `bool` type:</span></span>  
  
 <span data-ttu-id="dcfbf-124">[!code-cs[csrefKeywordsTypes#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/bool_4.cs)]</span><span class="sxs-lookup"><span data-stu-id="dcfbf-124">[!code-cs[csrefKeywordsTypes#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/bool_4.cs)]</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="dcfbf-125">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="dcfbf-125">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="dcfbf-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="dcfbf-126">See Also</span></span>  
 <span data-ttu-id="dcfbf-127">[Referência de C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="dcfbf-127">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="dcfbf-128">[Guia de Programação em C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="dcfbf-128">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="dcfbf-129">[Palavras-chave de C#](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="dcfbf-129">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="dcfbf-130">[Tabela de Tipos Integrais](../../../csharp/language-reference/keywords/integral-types-table.md) </span><span class="sxs-lookup"><span data-stu-id="dcfbf-130">[Integral Types Table](../../../csharp/language-reference/keywords/integral-types-table.md) </span></span>  
 <span data-ttu-id="dcfbf-131">[Tabela de Tipos Internos](../../../csharp/language-reference/keywords/built-in-types-table.md) </span><span class="sxs-lookup"><span data-stu-id="dcfbf-131">[Built-In Types Table](../../../csharp/language-reference/keywords/built-in-types-table.md) </span></span>  
 <span data-ttu-id="dcfbf-132">[Tabela de conversões numéricas implícitas](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md) </span><span class="sxs-lookup"><span data-stu-id="dcfbf-132">[Implicit Numeric Conversions Table](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md) </span></span>  
 [<span data-ttu-id="dcfbf-133">Tabela de conversões numéricas explícitas</span><span class="sxs-lookup"><span data-stu-id="dcfbf-133">Explicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)

