---
title: bool (Referência de C#)
ms.date: 07/20/2015
f1_keywords:
- bool_CSharpKeyword
- bool
helpviewer_keywords:
- bool keyword [C#]
ms.assetid: 551cfe35-2632-4343-af49-33ad12da08e2
ms.openlocfilehash: 1045a459491b0d0d6a84c60f6e820297b47efd5f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33215948"
---
# <a name="bool-c-reference"></a><span data-ttu-id="8f7da-102">bool (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="8f7da-102">bool (C# Reference)</span></span>
<span data-ttu-id="8f7da-103">A palavra-chave `bool` é um alias de <xref:System.Boolean?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="8f7da-103">The `bool` keyword is an alias of <xref:System.Boolean?displayProperty=nameWithType>.</span></span> <span data-ttu-id="8f7da-104">Ela é usada para declarar variáveis para armazenar os valores boolianos [true](../../../csharp/language-reference/keywords/true.md) e [false](../../../csharp/language-reference/keywords/false.md).</span><span class="sxs-lookup"><span data-stu-id="8f7da-104">It is used to declare variables to store the Boolean values, [true](../../../csharp/language-reference/keywords/true.md) and [false](../../../csharp/language-reference/keywords/false.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8f7da-105">Se você precisar de uma variável booliana que também pode ter um valor de `null`, use `bool?`.</span><span class="sxs-lookup"><span data-stu-id="8f7da-105">If you require a Boolean variable that can also have a value of `null`, use `bool?`.</span></span> <span data-ttu-id="8f7da-106">Para obter mais informações, consulte [Tipos que permitem valor nulo](../../../csharp/programming-guide/nullable-types/index.md).</span><span class="sxs-lookup"><span data-stu-id="8f7da-106">For more information, see [Nullable Types](../../../csharp/programming-guide/nullable-types/index.md).</span></span>  
  
## <a name="literals"></a><span data-ttu-id="8f7da-107">Literais</span><span class="sxs-lookup"><span data-stu-id="8f7da-107">Literals</span></span>  
 <span data-ttu-id="8f7da-108">Você pode atribuir um valor booliano a uma variável `bool`.</span><span class="sxs-lookup"><span data-stu-id="8f7da-108">You can assign a Boolean value to a `bool` variable.</span></span> <span data-ttu-id="8f7da-109">Você também pode atribuir uma expressão que é calculada como `bool` para um variável `bool`.</span><span class="sxs-lookup"><span data-stu-id="8f7da-109">You can also assign an expression that evaluates to `bool` to a `bool` variable.</span></span>  
  
 [!code-csharp[csrefKeywordsTypes#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/bool_1.cs)]  
  
 <span data-ttu-id="8f7da-110">O valor padrão de uma variável `bool` é `false`.</span><span class="sxs-lookup"><span data-stu-id="8f7da-110">The default value of a `bool` variable is `false`.</span></span> <span data-ttu-id="8f7da-111">O valor padrão de uma variável `bool?` é `null`.</span><span class="sxs-lookup"><span data-stu-id="8f7da-111">The default value of a `bool?` variable is `null`.</span></span>  
  
## <a name="conversions"></a><span data-ttu-id="8f7da-112">Conversões</span><span class="sxs-lookup"><span data-stu-id="8f7da-112">Conversions</span></span>  
 <span data-ttu-id="8f7da-113">No C++, um valor do tipo `bool` pode ser convertido em um valor do tipo `int`. Em outras palavras, `false` é equivalente a zero e `true` é equivalente a valores diferentes de zero.</span><span class="sxs-lookup"><span data-stu-id="8f7da-113">In C++, a value of type `bool` can be converted to a value of type `int`; in other words, `false` is equivalent to zero and `true` is equivalent to nonzero values.</span></span> <span data-ttu-id="8f7da-114">No C#, não há conversão entre o tipo `bool` e outros tipos.</span><span class="sxs-lookup"><span data-stu-id="8f7da-114">In C#, there is no conversion between the `bool` type and other types.</span></span> <span data-ttu-id="8f7da-115">Por exemplo, a seguinte instrução `if` é inválida no C#:</span><span class="sxs-lookup"><span data-stu-id="8f7da-115">For example, the following `if` statement is invalid in C#:</span></span>  
  
 [!code-csharp[csrefKeywordsTypes#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/bool_2.cs)]  
  
 <span data-ttu-id="8f7da-116">Para testar uma variável do tipo `int`, você precisa compará-la explicitamente com um valor, como zero, da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="8f7da-116">To test a variable of the type `int`, you have to explicitly compare it to a value, such as zero, as follows:</span></span>  
  
 [!code-csharp[csrefKeywordsTypes#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/bool_3.cs)]  
  
## <a name="example"></a><span data-ttu-id="8f7da-117">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8f7da-117">Example</span></span>  
 <span data-ttu-id="8f7da-118">Neste exemplo, você insere um caractere do teclado e o programa verifica se o caractere de entrada é uma letra.</span><span class="sxs-lookup"><span data-stu-id="8f7da-118">In this example, you enter a character from the keyboard and the program checks if the input character is a letter.</span></span> <span data-ttu-id="8f7da-119">Se for uma letra, ele verificará se é maiúscula ou minúscula.</span><span class="sxs-lookup"><span data-stu-id="8f7da-119">If it is a letter, it checks if it is lowercase or uppercase.</span></span> <span data-ttu-id="8f7da-120">Essas verificações são executadas com o <xref:System.Char.IsLetter%2A> e o <xref:System.Char.IsLower%2A>, ambos os quais retornam o tipo `bool`:</span><span class="sxs-lookup"><span data-stu-id="8f7da-120">These checks are performed with the <xref:System.Char.IsLetter%2A>, and <xref:System.Char.IsLower%2A>, both of which return the `bool` type:</span></span>  
  
 [!code-csharp[csrefKeywordsTypes#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/bool_4.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="8f7da-121">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="8f7da-121">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="8f7da-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8f7da-122">See Also</span></span>  
 [<span data-ttu-id="8f7da-123">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="8f7da-123">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="8f7da-124">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="8f7da-124">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="8f7da-125">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="8f7da-125">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="8f7da-126">Tabela de tipos integrais</span><span class="sxs-lookup"><span data-stu-id="8f7da-126">Integral Types Table</span></span>](../../../csharp/language-reference/keywords/integral-types-table.md)  
 [<span data-ttu-id="8f7da-127">Tabela de tipos internos</span><span class="sxs-lookup"><span data-stu-id="8f7da-127">Built-In Types Table</span></span>](../../../csharp/language-reference/keywords/built-in-types-table.md)  
 [<span data-ttu-id="8f7da-128">Tabela de conversões numéricas implícitas</span><span class="sxs-lookup"><span data-stu-id="8f7da-128">Implicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)  
 [<span data-ttu-id="8f7da-129">Tabela de conversões numéricas explícitas</span><span class="sxs-lookup"><span data-stu-id="8f7da-129">Explicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)
