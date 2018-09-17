---
title: Operador false (Referência de C#)
ms.date: 07/20/2015
helpviewer_keywords:
- false operator keyword [C#]
ms.assetid: 81a888fd-011e-4589-b242-6c261fea505e
ms.openlocfilehash: e73113bd37dbb68590267141ad037f78919520bc
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45648919"
---
# <a name="false-operator-c-reference"></a><span data-ttu-id="608ed-102">Operador false (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="608ed-102">false operator (C# Reference)</span></span>

<span data-ttu-id="608ed-103">Retorna o valor [bool](bool.md) `true` para indicar que um operando é `false`, caso contrário, retorna `false`.</span><span class="sxs-lookup"><span data-stu-id="608ed-103">Returns the [bool](bool.md) value `true` to indicate that an operand is `false` and returns `false` otherwise.</span></span>

<span data-ttu-id="608ed-104">Antes do C# 2.0, os operadores `true` e `false` eram usados para criar tipos que permitem valor nulo definidos pelo usuário que eram compatíveis com tipos como `SqlBool`.</span><span class="sxs-lookup"><span data-stu-id="608ed-104">Prior to C# 2.0, the `true` and `false` operators were used to create user-defined nullable value types that were compatible with types such as `SqlBool`.</span></span> <span data-ttu-id="608ed-105">No entanto, a linguagem agora fornece suporte interno para tipos que permitem valor nulo e, sempre que possível, você deve usá-los em vez de sobrecarregar os operadores `true` e `false`.</span><span class="sxs-lookup"><span data-stu-id="608ed-105">However, the language now provides built-in support for nullable value types, and whenever possible you should use those instead of overloading the `true` and `false` operators.</span></span> <span data-ttu-id="608ed-106">Para obter mais informações, consulte [Nullable Types (Tipos que permitem valores nulos)](../../programming-guide/nullable-types/index.md).</span><span class="sxs-lookup"><span data-stu-id="608ed-106">For more information, see [Nullable Types](../../programming-guide/nullable-types/index.md).</span></span>

<span data-ttu-id="608ed-107">Com boolianos que permitem valor nulo, a expressão `a != b` não é necessariamente igual a `!(a == b)` porque um ou ambos os valores podem ser nulos.</span><span class="sxs-lookup"><span data-stu-id="608ed-107">With nullable Booleans, the expression `a != b` is not necessarily equal to `!(a == b)` because one or both of the values might be null.</span></span> <span data-ttu-id="608ed-108">Você deve sobrecarregar os operadores `true` e `false` separadamente para manipular corretamente os valores nulos na expressão.</span><span class="sxs-lookup"><span data-stu-id="608ed-108">You have to overload both the `true` and `false` operators separately to correctly handle the null values in the expression.</span></span> <span data-ttu-id="608ed-109">O exemplo a seguir mostra como sobrecarregar e usar os operadores `true` e `false`.</span><span class="sxs-lookup"><span data-stu-id="608ed-109">The following example shows how to overload and use the `true` and `false` operators.</span></span>

[!code-csharp[csrefKeywordsOperator#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#16)]

<span data-ttu-id="608ed-110">Um tipo que sobrecarrega os operadores `true` e `false` pode ser usado para a expressão de controle nas instruções [if](if-else.md), [do](do.md), [while](while.md) e [for](for.md), bem como em [expressões condicionais](../operators/conditional-operator.md).</span><span class="sxs-lookup"><span data-stu-id="608ed-110">A type that overloads the `true` and `false` operators can be used for the controlling expression in [if](if-else.md), [do](do.md), [while](while.md), and [for](for.md) statements and in [conditional expressions](../operators/conditional-operator.md).</span></span>

<span data-ttu-id="608ed-111">Se um tipo define o operador `false`, ele também deve definir o operador [true](true.md).</span><span class="sxs-lookup"><span data-stu-id="608ed-111">If a type defines operator `false`, it must also define operator [true](true.md).</span></span>

<span data-ttu-id="608ed-112">Um tipo não pode sobrecarregar diretamente os operadores lógicos condicionais [ && ](../operators/conditional-and-operator.md) e [&#124;&#124;](../operators/conditional-or-operator.md), mas um efeito equivalente poderá ser obtido ao sobrecarregar os operadores lógicos regulares e operadores `true` e `false`.</span><span class="sxs-lookup"><span data-stu-id="608ed-112">A type cannot directly overload the conditional logical operators [&&](../operators/conditional-and-operator.md) and [&#124;&#124;](../operators/conditional-or-operator.md), but an equivalent effect can be achieved by overloading the regular logical operators and operators `true` and `false`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="608ed-113">especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="608ed-113">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="608ed-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="608ed-114">See also</span></span>

- [<span data-ttu-id="608ed-115">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="608ed-115">C# Reference</span></span>](../index.md)  
- [<span data-ttu-id="608ed-116">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="608ed-116">C# Programming Guide</span></span>](../../programming-guide/index.md)  
- [<span data-ttu-id="608ed-117">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="608ed-117">C# Keywords</span></span>](index.md)  
- [<span data-ttu-id="608ed-118">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="608ed-118">C# Operators</span></span>](../operators/index.md)  
- [<span data-ttu-id="608ed-119">true</span><span class="sxs-lookup"><span data-stu-id="608ed-119">true</span></span>](true.md)  