---
title: Palavra-chave const – Referência de C#
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- const_CSharpKeyword
- const
helpviewer_keywords:
- const keyword [C#]
ms.assetid: 79eb447c-117b-4418-933f-97c50aa472db
ms.openlocfilehash: f0b2b3632e767710bd31f5f6edaccaf0c2ef8c85
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54526971"
---
# <a name="const-c-reference"></a><span data-ttu-id="66102-102">const (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="66102-102">const (C# Reference)</span></span>

<span data-ttu-id="66102-103">Use a palavra-chave `const` para declarar um campo constante ou um local constante.</span><span class="sxs-lookup"><span data-stu-id="66102-103">You use the `const` keyword to declare a constant field or a constant local.</span></span> <span data-ttu-id="66102-104">Campos e locais constantes não são variáveis ​​e não podem ser modificados.</span><span class="sxs-lookup"><span data-stu-id="66102-104">Constant fields and locals aren't variables and may not be modified.</span></span> <span data-ttu-id="66102-105">As constantes podem ser números, valores boolianos, cadeias de caracteres ou uma referência nula.</span><span class="sxs-lookup"><span data-stu-id="66102-105">Constants can be numbers, Boolean values, strings, or a null reference.</span></span> <span data-ttu-id="66102-106">Não crie uma constante para representar informações que você espera mudar a qualquer momento.</span><span class="sxs-lookup"><span data-stu-id="66102-106">Don’t create a constant to represent information that you expect to change at any time.</span></span> <span data-ttu-id="66102-107">Por exemplo, não use um campo constante para armazenar o preço de um serviço, um número de versão de produto ou a marca de uma empresa.</span><span class="sxs-lookup"><span data-stu-id="66102-107">For example, don’t use a constant field to store the price of a service, a product version number, or the brand name of a company.</span></span> <span data-ttu-id="66102-108">Esses valores podem mudar ao longo do tempo e como os compiladores propagam constantes, outro código compilado com as bibliotecas terá que ser recompilado para ver as alterações.</span><span class="sxs-lookup"><span data-stu-id="66102-108">These values can change over time, and because compilers propagate constants, other code compiled with your libraries will have to be recompiled to see the changes.</span></span> <span data-ttu-id="66102-109">Veja também a palavra-chave [readonly](../../../csharp/language-reference/keywords/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="66102-109">See also the [readonly](../../../csharp/language-reference/keywords/readonly.md) keyword.</span></span> <span data-ttu-id="66102-110">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="66102-110">For example:</span></span>

```csharp
const int x = 0;
public const double gravitationalConstant = 6.673e-11;
private const string productName = "Visual C#";
```

## <a name="remarks"></a><span data-ttu-id="66102-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="66102-111">Remarks</span></span>

<span data-ttu-id="66102-112">O tipo de uma declaração constante especifica o tipo dos membros que a declaração apresenta.</span><span class="sxs-lookup"><span data-stu-id="66102-112">The type of a constant declaration specifies the type of the members that the declaration introduces.</span></span> <span data-ttu-id="66102-113">O inicializador de um local ou um campo constante deve ser uma expressão constante que pode ser implicitamente convertida para o tipo de destino.</span><span class="sxs-lookup"><span data-stu-id="66102-113">The initializer of a constant local or a constant field must be a constant expression that can be implicitly converted to the target type.</span></span>

<span data-ttu-id="66102-114">Uma expressão constante é uma expressão que pode ser completamente avaliada em tempo de compilação.</span><span class="sxs-lookup"><span data-stu-id="66102-114">A constant expression is an expression that can be fully evaluated at compile time.</span></span> <span data-ttu-id="66102-115">Portanto, os únicos valores possíveis para as constantes de tipos de referência são `string` e uma referência nula.</span><span class="sxs-lookup"><span data-stu-id="66102-115">Therefore, the only possible values for constants of reference types are `string` and a null reference.</span></span>

<span data-ttu-id="66102-116">A declaração constante pode declarar constantes múltiplas como:</span><span class="sxs-lookup"><span data-stu-id="66102-116">The constant declaration can declare multiple constants, such as:</span></span>

```csharp
public const double x = 1.0, y = 2.0, z = 3.0;
```

<span data-ttu-id="66102-117">O modificador `static` não é permitido em uma declaração constante.</span><span class="sxs-lookup"><span data-stu-id="66102-117">The `static` modifier is not allowed in a constant declaration.</span></span>

<span data-ttu-id="66102-118">A constante pode fazer parte de uma expressão constante, como a seguir:</span><span class="sxs-lookup"><span data-stu-id="66102-118">A constant can participate in a constant expression, as follows:</span></span>

```csharp
public const int c1 = 5;
public const int c2 = c1 + 100;
```

> [!NOTE]
> <span data-ttu-id="66102-119">A palavra-chave [readonly](../../../csharp/language-reference/keywords/readonly.md) é diferente da palavra-chave `const`.</span><span class="sxs-lookup"><span data-stu-id="66102-119">The [readonly](../../../csharp/language-reference/keywords/readonly.md) keyword differs from the `const` keyword.</span></span> <span data-ttu-id="66102-120">O campo `const` pode ser inicializado apenas na declaração do campo.</span><span class="sxs-lookup"><span data-stu-id="66102-120">A `const` field can only be initialized at the declaration of the field.</span></span> <span data-ttu-id="66102-121">Um campo `readonly` pode ser inicializado na declaração ou em um construtor.</span><span class="sxs-lookup"><span data-stu-id="66102-121">A `readonly` field can be initialized either at the declaration or in a constructor.</span></span> <span data-ttu-id="66102-122">Portanto, campos `readonly` podem ter valores diferentes dependendo do construtor usado.</span><span class="sxs-lookup"><span data-stu-id="66102-122">Therefore, `readonly` fields can have different values depending on the constructor used.</span></span> <span data-ttu-id="66102-123">Além disso, embora um campo `const` seja uma constante em tempo de compilação, o campo `readonly` pode ser usado para constantes de tempo de execução, como nesta linha: `public static readonly uint l1 = (uint)DateTime.Now.Ticks;`</span><span class="sxs-lookup"><span data-stu-id="66102-123">Also, although a `const` field is a compile-time constant, the `readonly` field can be used for run-time constants, as in this line: `public static readonly uint l1 = (uint)DateTime.Now.Ticks;`</span></span>

## <a name="example"></a><span data-ttu-id="66102-124">Exemplo</span><span class="sxs-lookup"><span data-stu-id="66102-124">Example</span></span>

[!code-csharp[csrefKeywordsModifiers#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#5)]

## <a name="example"></a><span data-ttu-id="66102-125">Exemplo</span><span class="sxs-lookup"><span data-stu-id="66102-125">Example</span></span>

<span data-ttu-id="66102-126">Este exemplo demonstra como usar constantes como variáveis ​​locais.</span><span class="sxs-lookup"><span data-stu-id="66102-126">This example demonstrates how to use constants as local variables.</span></span>

[!code-csharp[csrefKeywordsModifiers#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#6)]

## <a name="c-language-specification"></a><span data-ttu-id="66102-127">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="66102-127">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="66102-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="66102-128">See also</span></span>

- [<span data-ttu-id="66102-129">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="66102-129">C# Reference</span></span>](../../../csharp/language-reference/index.md)
- [<span data-ttu-id="66102-130">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="66102-130">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="66102-131">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="66102-131">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)
- [<span data-ttu-id="66102-132">Modificadores</span><span class="sxs-lookup"><span data-stu-id="66102-132">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)
- [<span data-ttu-id="66102-133">readonly</span><span class="sxs-lookup"><span data-stu-id="66102-133">readonly</span></span>](../../../csharp/language-reference/keywords/readonly.md)
