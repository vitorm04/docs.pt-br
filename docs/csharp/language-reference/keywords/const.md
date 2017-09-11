---
title: "const (Referência de C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- const_CSharpKeyword
- const
dev_langs:
- CSharp
helpviewer_keywords:
- const keyword [C#]
ms.assetid: 79eb447c-117b-4418-933f-97c50aa472db
caps.latest.revision: 28
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
ms.openlocfilehash: b8f6d567deed513ff5693fe39bd21c8607677402
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="const-c-reference"></a><span data-ttu-id="87bf5-102">const (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="87bf5-102">const (C# Reference)</span></span>
<span data-ttu-id="87bf5-103">Use a palavra-chave `const` para declarar um campo constante ou um local constante.</span><span class="sxs-lookup"><span data-stu-id="87bf5-103">You use the `const` keyword to declare a constant field or a constant local.</span></span> <span data-ttu-id="87bf5-104">Campos e locais constantes não são variáveis ​​e não podem ser modificados.</span><span class="sxs-lookup"><span data-stu-id="87bf5-104">Constant fields and locals aren't variables and may not be modified.</span></span> <span data-ttu-id="87bf5-105">As constantes podem ser números, valores boolianos, cadeias de caracteres ou uma referência nula.</span><span class="sxs-lookup"><span data-stu-id="87bf5-105">Constants can be numbers, Boolean values, strings, or a null reference.</span></span> <span data-ttu-id="87bf5-106">Não crie uma constante para representar informações que você espera mudar a qualquer momento.</span><span class="sxs-lookup"><span data-stu-id="87bf5-106">Don’t create a constant to represent information that you expect to change at any time.</span></span> <span data-ttu-id="87bf5-107">Por exemplo, não use um campo constante para armazenar o preço de um serviço, um número de versão de produto ou a marca de uma empresa.</span><span class="sxs-lookup"><span data-stu-id="87bf5-107">For example, don’t use a constant field to store the price of a service, a product version number, or the brand name of a company.</span></span> <span data-ttu-id="87bf5-108">Esses valores podem mudar ao longo do tempo e como os compiladores propagam constantes, outro código compilado com as bibliotecas terá que ser recompilado para ver as alterações.</span><span class="sxs-lookup"><span data-stu-id="87bf5-108">These values can change over time, and because compilers propagate constants, other code compiled with your libraries will have to be recompiled to see the changes.</span></span> <span data-ttu-id="87bf5-109">Veja também a palavra-chave [readonly](../../../csharp/language-reference/keywords/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="87bf5-109">See also the [readonly](../../../csharp/language-reference/keywords/readonly.md) keyword.</span></span> <span data-ttu-id="87bf5-110">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="87bf5-110">For example:</span></span>  
  
```csharp
const int x = 0;  
public const double gravitationalConstant = 6.673e-11;  
private const string productName = "Visual C#";  
```  
  
## <a name="remarks"></a><span data-ttu-id="87bf5-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="87bf5-111">Remarks</span></span>  
 <span data-ttu-id="87bf5-112">O tipo de uma declaração constante especifica o tipo dos membros que a declaração apresenta.</span><span class="sxs-lookup"><span data-stu-id="87bf5-112">The type of a constant declaration specifies the type of the members that the declaration introduces.</span></span> <span data-ttu-id="87bf5-113">O inicializador de um local ou um campo constante deve ser uma expressão constante que pode ser implicitamente convertida para o tipo de destino.</span><span class="sxs-lookup"><span data-stu-id="87bf5-113">The initializer of a constant local or a constant field must be a constant expression that can be implicitly converted to the target type.</span></span>  
  
 <span data-ttu-id="87bf5-114">Uma expressão constante é uma expressão que pode ser completamente avaliada em tempo de compilação.</span><span class="sxs-lookup"><span data-stu-id="87bf5-114">A constant expression is an expression that can be fully evaluated at compile time.</span></span> <span data-ttu-id="87bf5-115">Portanto, os únicos valores possíveis para as constantes de tipos de referência são `string` e uma referência nula.</span><span class="sxs-lookup"><span data-stu-id="87bf5-115">Therefore, the only possible values for constants of reference types are `string` and a null reference.</span></span>  
  
 <span data-ttu-id="87bf5-116">A declaração constante pode declarar constantes múltiplas como:</span><span class="sxs-lookup"><span data-stu-id="87bf5-116">The constant declaration can declare multiple constants, such as:</span></span>  
  
```csharp
public const double x = 1.0, y = 2.0, z = 3.0;  
```  
  
 <span data-ttu-id="87bf5-117">O modificador `static` não é permitido em uma declaração constante.</span><span class="sxs-lookup"><span data-stu-id="87bf5-117">The `static` modifier is not allowed in a constant declaration.</span></span>  
  
 <span data-ttu-id="87bf5-118">A constante pode fazer parte de uma expressão constante, como a seguir:</span><span class="sxs-lookup"><span data-stu-id="87bf5-118">A constant can participate in a constant expression, as follows:</span></span>  
  
```csharp
public const int c1 = 5;  
public const int c2 = c1 + 100;  
```  
  
> [!NOTE]
>  <span data-ttu-id="87bf5-119">A palavra-chave [readonly](../../../csharp/language-reference/keywords/readonly.md) é diferente da palavra-chave `const`.</span><span class="sxs-lookup"><span data-stu-id="87bf5-119">The [readonly](../../../csharp/language-reference/keywords/readonly.md) keyword differs from the `const` keyword.</span></span> <span data-ttu-id="87bf5-120">O campo `const` pode ser inicializado apenas na declaração do campo.</span><span class="sxs-lookup"><span data-stu-id="87bf5-120">A `const` field can only be initialized at the declaration of the field.</span></span> <span data-ttu-id="87bf5-121">Um campo `readonly` pode ser inicializado na declaração ou em um construtor.</span><span class="sxs-lookup"><span data-stu-id="87bf5-121">A `readonly` field can be initialized either at the declaration or in a constructor.</span></span> <span data-ttu-id="87bf5-122">Portanto, campos `readonly` podem ter valores diferentes dependendo do construtor usado.</span><span class="sxs-lookup"><span data-stu-id="87bf5-122">Therefore, `readonly` fields can have different values depending on the constructor used.</span></span> <span data-ttu-id="87bf5-123">Além disso, embora um campo `const` seja uma constante em tempo de compilação, o campo `readonly` pode ser usado para constantes de tempo de execução, como nesta linha: `public static readonly uint l1 = (uint)DateTime.Now.Ticks;`</span><span class="sxs-lookup"><span data-stu-id="87bf5-123">Also, although a `const` field is a compile-time constant, the `readonly` field can be used for run-time constants, as in this line: `public static readonly uint l1 = (uint)DateTime.Now.Ticks;`</span></span>  
  
## <a name="example"></a><span data-ttu-id="87bf5-124">Exemplo</span><span class="sxs-lookup"><span data-stu-id="87bf5-124">Example</span></span>  
 <span data-ttu-id="87bf5-125">[!code-cs[csrefKeywordsModifiers#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/const_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="87bf5-125">[!code-cs[csrefKeywordsModifiers#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/const_1.cs)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="87bf5-126">Exemplo</span><span class="sxs-lookup"><span data-stu-id="87bf5-126">Example</span></span>  
 <span data-ttu-id="87bf5-127">Este exemplo demonstra como usar constantes como variáveis ​​locais.</span><span class="sxs-lookup"><span data-stu-id="87bf5-127">This example demonstrates how to use constants as local variables.</span></span>  
  
 <span data-ttu-id="87bf5-128">[!code-cs[csrefKeywordsModifiers#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/const_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="87bf5-128">[!code-cs[csrefKeywordsModifiers#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/const_2.cs)]</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="87bf5-129">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="87bf5-129">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="87bf5-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="87bf5-130">See Also</span></span>  
 <span data-ttu-id="87bf5-131">[Referência de C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="87bf5-131">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="87bf5-132">[Guia de Programação em C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="87bf5-132">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="87bf5-133">[Palavras-chave de C#](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="87bf5-133">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="87bf5-134">[Modificadores](../../../csharp/language-reference/keywords/modifiers.md) </span><span class="sxs-lookup"><span data-stu-id="87bf5-134">[Modifiers](../../../csharp/language-reference/keywords/modifiers.md) </span></span>  
 [<span data-ttu-id="87bf5-135">readonly</span><span class="sxs-lookup"><span data-stu-id="87bf5-135">readonly</span></span>](../../../csharp/language-reference/keywords/readonly.md)

