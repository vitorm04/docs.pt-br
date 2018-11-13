---
title: 'Operador ?: (Referência de C#)'
ms.date: 07/20/2015
f1_keywords:
- ?:_CSharpKeyword
- ?_CSharpKeyword
- :_CSharpKeyword
helpviewer_keywords:
- '?: operator [C#]'
- conditional operator (?:) [C#]
ms.assetid: e83a17f1-7500-48ba-8bee-2fbc4c847af4
ms.openlocfilehash: 3e45ff6eaaefa5829c3ed9415abe1a12b7a1d069
ms.sourcegitcommit: 4bca8f7e172fd019ef437a4803bf5895c6bc4781
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/03/2018
ms.locfileid: "50980616"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="62d05-102">Operador ?: (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="62d05-102">?: Operator (C# Reference)</span></span>

<span data-ttu-id="62d05-103">O operador condicional (`?:`), comumente conhecido como o operador condicional ternário, retorna um de dois valores dependendo do valor de uma expressão booliana.</span><span class="sxs-lookup"><span data-stu-id="62d05-103">The conditional operator (`?:`), commonly known as the ternary conditional operator, returns one of two values depending on the value of a Boolean expression.</span></span> <span data-ttu-id="62d05-104">Esta é a sintaxe do operador condicional.</span><span class="sxs-lookup"><span data-stu-id="62d05-104">Following is the syntax for the conditional operator.</span></span>  

```csharp
condition ? first_expression : second_expression;  
```

<span data-ttu-id="62d05-105">Começando com C# 7.2, `first_expression` e `second_expression` podem ser [expressões `ref`](https://github.com/dotnet/csharplang/blob/master/proposals/csharp-7.2/conditional-ref.md):</span><span class="sxs-lookup"><span data-stu-id="62d05-105">Beginning with C# 7.2, the `first_expression` and `second_expression` my be [`ref` expressions](https://github.com/dotnet/csharplang/blob/master/proposals/csharp-7.2/conditional-ref.md):</span></span>

```csharp
ref condition ? ref first_expression : ref second_expression;  
```

<span data-ttu-id="62d05-106">O resultado pode ser atribuído a uma variável `ref` ou `ref readonly`, ou a uma variável sem nenhum modificador.</span><span class="sxs-lookup"><span data-stu-id="62d05-106">The result may be assigned to a `ref` or `ref readonly` variable, or to a variable with neither modifier.</span></span>

## <a name="remarks"></a><span data-ttu-id="62d05-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="62d05-107">Remarks</span></span>

<span data-ttu-id="62d05-108">A `condition` deve ser avaliada como `true` ou `false`.</span><span class="sxs-lookup"><span data-stu-id="62d05-108">The `condition` must evaluate to `true` or `false`.</span></span> <span data-ttu-id="62d05-109">Se `condition` for `true`, `first_expression` será avaliada e se tornará o resultado.</span><span class="sxs-lookup"><span data-stu-id="62d05-109">If `condition` is `true`, `first_expression` is evaluated and becomes the result.</span></span> <span data-ttu-id="62d05-110">Se `condition` for `false`, `second_expression` será avaliada e se tornará o resultado.</span><span class="sxs-lookup"><span data-stu-id="62d05-110">If `condition` is `false`, `second_expression` is evaluated and becomes the result.</span></span> <span data-ttu-id="62d05-111">Somente uma das duas expressões será avaliada.</span><span class="sxs-lookup"><span data-stu-id="62d05-111">Only one of the two expressions is evaluated.</span></span> <span data-ttu-id="62d05-112">Isso é particularmente importante para expressões nas quais o resultado é um `ref`, como o seguinte é válido:</span><span class="sxs-lookup"><span data-stu-id="62d05-112">This is particularly important for expressions where the result is a `ref`, as the following is valid:</span></span>

```csharp
ref (storage != null) ? ref storage[3] : ref defaultValue;
```

<span data-ttu-id="62d05-113">A referência ao `storage` não será avaliada quando `storage` for nulo.</span><span class="sxs-lookup"><span data-stu-id="62d05-113">The reference to `storage` is not evaluated when `storage` is null.</span></span>

<span data-ttu-id="62d05-114">Quando o resultado for um valor, o tipo de `first_expression` e `second_expression` devem ser iguais ou, deve haver uma conversão implícita de um tipo para outro.</span><span class="sxs-lookup"><span data-stu-id="62d05-114">When the result is a value, the type of `first_expression` and `second_expression` must be the same, or there must be an implicit conversion from one type to the other.</span></span> <span data-ttu-id="62d05-115">Quando o resultado é um `ref`, o tipo de `first_expression` e `second_expression` devem ser iguais.</span><span class="sxs-lookup"><span data-stu-id="62d05-115">When the result is a `ref`, the type of `first_expression` and `second_expression` must be the same.</span></span>

<span data-ttu-id="62d05-116">Você pode expressar cálculos que podem, de outra forma, exigir uma construção `if-else` mais concisamente ao usar o operador condicional.</span><span class="sxs-lookup"><span data-stu-id="62d05-116">You can express calculations that might otherwise require an `if-else` construction more concisely by using the conditional operator.</span></span> <span data-ttu-id="62d05-117">Por exemplo, o código a seguir usa primeiro uma instrução `if` e, em seguida, um operador condicional para classificar um inteiro como positivo ou negativo.</span><span class="sxs-lookup"><span data-stu-id="62d05-117">For example, the following code uses first an `if` statement and then a conditional operator to classify an integer as positive or negative.</span></span>

```csharp
int input = Convert.ToInt32(Console.ReadLine());  
string classify;  
  
// if-else construction.  
if (input > 0)  
    classify = "positive";  
else  
    classify = "negative";  
  
// ?: conditional operator.  
classify = (input > 0) ? "positive" : "negative";  
```

<span data-ttu-id="62d05-118">O operador condicional é associativo direito.</span><span class="sxs-lookup"><span data-stu-id="62d05-118">The conditional operator is right-associative.</span></span> <span data-ttu-id="62d05-119">A expressão `a ? b : c ? d : e` é avaliada como `a ? b : (c ? d : e)`, não como `(a ? b : c) ? d : e`.</span><span class="sxs-lookup"><span data-stu-id="62d05-119">The expression `a ? b : c ? d : e` is evaluated as `a ? b : (c ? d : e)`, not as `(a ? b : c) ? d : e`.</span></span>  
  
<span data-ttu-id="62d05-120">O operador condicional não pode ser sobrecarregado.</span><span class="sxs-lookup"><span data-stu-id="62d05-120">The conditional operator cannot be overloaded.</span></span>
  
## <a name="example"></a><span data-ttu-id="62d05-121">Exemplo</span><span class="sxs-lookup"><span data-stu-id="62d05-121">Example</span></span>

<span data-ttu-id="62d05-122">O exemplo a seguir mostra o operador condicional, cujo resultado é um valor:</span><span class="sxs-lookup"><span data-stu-id="62d05-122">The following example shows the conditional operator whose result is a value:</span></span>

[!code-csharp[csRefOperators?:](~/samples/snippets/csharp/language-reference/operators/ConditionalExamples.cs#ConditionalValue)]

<span data-ttu-id="62d05-123">A alternativa a seguir mostra o operador condicional, cujo resultado é uma referência:</span><span class="sxs-lookup"><span data-stu-id="62d05-123">The following alternative shows the conditional operator where the result is a reference:</span></span>

[!code-csharp[csRefOperatorsRef?:](~/samples/snippets/csharp/language-reference/operators/ConditionalExamples.cs#ConditionalRef)]

## <a name="see-also"></a><span data-ttu-id="62d05-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="62d05-124">See Also</span></span>

- [<span data-ttu-id="62d05-125">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="62d05-125">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="62d05-126">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="62d05-126">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="62d05-127">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="62d05-127">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)  
- [<span data-ttu-id="62d05-128">if-else</span><span class="sxs-lookup"><span data-stu-id="62d05-128">if-else</span></span>](../../../csharp/language-reference/keywords/if-else.md)  
- <span data-ttu-id="62d05-129">[Operadores ?. e ?[]](../../../csharp/language-reference/operators/null-conditional-operators.md)</span><span class="sxs-lookup"><span data-stu-id="62d05-129">[?. and ?[] Operators](../../../csharp/language-reference/operators/null-conditional-operators.md)</span></span>  
- [<span data-ttu-id="62d05-130">Operador ??</span><span class="sxs-lookup"><span data-stu-id="62d05-130">?? Operator</span></span>](../../../csharp/language-reference/operators/null-coalescing-operator.md)
