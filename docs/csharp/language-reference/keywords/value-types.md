---
title: Tipos de valor (Referência de C#)
ms.date: 07/20/2015
f1_keywords:
- cs.valuetypes
helpviewer_keywords:
- value types [C#]
- types [C#], value types
- C# language, value types
ms.assetid: 471eb994-2958-49d5-a6be-19b4313f80a3
ms.openlocfilehash: 3bbaea9247d975c27ed6f49dedb749312f675296
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43526457"
---
# <a name="value-types-c-reference"></a><span data-ttu-id="19a65-102">Tipos de valor (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="19a65-102">Value Types (C# Reference)</span></span>
<span data-ttu-id="19a65-103">Os tipos de valor consistem em duas categorias principais:</span><span class="sxs-lookup"><span data-stu-id="19a65-103">The value types consist of two main categories:</span></span>  
  
-   [<span data-ttu-id="19a65-104">Estruturas</span><span class="sxs-lookup"><span data-stu-id="19a65-104">Structs</span></span>](../../../csharp/language-reference/keywords/struct.md)  
  
-   [<span data-ttu-id="19a65-105">Enumerações</span><span class="sxs-lookup"><span data-stu-id="19a65-105">Enumerations</span></span>](../../../csharp/language-reference/keywords/enum.md)  
  
 <span data-ttu-id="19a65-106">Os structs se enquadram nestas categorias:</span><span class="sxs-lookup"><span data-stu-id="19a65-106">Structs fall into these categories:</span></span>  
  
-   <span data-ttu-id="19a65-107">Tipos numéricos</span><span class="sxs-lookup"><span data-stu-id="19a65-107">Numeric types</span></span>  
  
    -   [<span data-ttu-id="19a65-108">Tipos integrais</span><span class="sxs-lookup"><span data-stu-id="19a65-108">Integral types</span></span>](../../../csharp/language-reference/keywords/integral-types-table.md)  
  
    -   [<span data-ttu-id="19a65-109">Tipos de ponto flutuante</span><span class="sxs-lookup"><span data-stu-id="19a65-109">Floating-point types</span></span>](../../../csharp/language-reference/keywords/floating-point-types-table.md)  
  
-   [<span data-ttu-id="19a65-110">bool</span><span class="sxs-lookup"><span data-stu-id="19a65-110">bool</span></span>](../../../csharp/language-reference/keywords/bool.md)  
  
-   <span data-ttu-id="19a65-111">Structs definidos pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="19a65-111">User defined structs.</span></span>  
  
## <a name="main-features-of-value-types"></a><span data-ttu-id="19a65-112">Principais recursos dos tipos de valor</span><span class="sxs-lookup"><span data-stu-id="19a65-112">Main Features of Value Types</span></span>  
 <span data-ttu-id="19a65-113">As variáveis que são baseadas diretamente em tipos de valor contêm valores.</span><span class="sxs-lookup"><span data-stu-id="19a65-113">Variables that are based on value types directly contain values.</span></span> <span data-ttu-id="19a65-114">Atribuir uma variável de tipo de valor à outra, copia o valor contido.</span><span class="sxs-lookup"><span data-stu-id="19a65-114">Assigning one value type variable to another copies the contained value.</span></span> <span data-ttu-id="19a65-115">Isso difere da atribuição de variáveis de tipo de referência, que copiam uma referência para o objeto, mas não o próprio objeto.</span><span class="sxs-lookup"><span data-stu-id="19a65-115">This differs from the assignment of reference type variables, which copies a reference to the object but not the object itself.</span></span>  
  
 <span data-ttu-id="19a65-116">Todos os tipos de valor são derivados implicitamente da <xref:System.ValueType?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="19a65-116">All value types are derived implicitly from the <xref:System.ValueType?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="19a65-117">Ao contrário do que acontece com tipos de referência, você não pode derivar um novo tipo de um tipo de valor.</span><span class="sxs-lookup"><span data-stu-id="19a65-117">Unlike with reference types, you cannot derive a new type from a value type.</span></span> <span data-ttu-id="19a65-118">No entanto, assim como com tipos de referência, os structs podem implementar interfaces.</span><span class="sxs-lookup"><span data-stu-id="19a65-118">However, like reference types, structs can implement interfaces.</span></span>  
  
 <span data-ttu-id="19a65-119">Ao contrário dos tipos de referência, um tipo de valor não pode conter o valor `null`.</span><span class="sxs-lookup"><span data-stu-id="19a65-119">Unlike reference types, a value type cannot contain the `null` value.</span></span> <span data-ttu-id="19a65-120">No entanto, o recurso [tipos que permitem valor nulo](../../../csharp/programming-guide/nullable-types/index.md) permite que os tipos de valor sejam atribuídos como `null`.</span><span class="sxs-lookup"><span data-stu-id="19a65-120">However, the [nullable types](../../../csharp/programming-guide/nullable-types/index.md) feature does allow for value types to be assigned to `null`.</span></span>  
  
 <span data-ttu-id="19a65-121">Cada tipo de valor tem um construtor padrão implícito que inicializa o valor padrão desse tipo.</span><span class="sxs-lookup"><span data-stu-id="19a65-121">Each value type has an implicit default constructor that initializes the default value of that type.</span></span> <span data-ttu-id="19a65-122">Para obter informações sobre valores padrão de tipos de valor, consulte [Tabela de valores padrão](../../../csharp/language-reference/keywords/default-values-table.md).</span><span class="sxs-lookup"><span data-stu-id="19a65-122">For information about default values of value types, see [Default Values Table](../../../csharp/language-reference/keywords/default-values-table.md).</span></span>  
  
## <a name="main-features-of-simple-types"></a><span data-ttu-id="19a65-123">Principais recursos dos tipos simples</span><span class="sxs-lookup"><span data-stu-id="19a65-123">Main Features of Simple Types</span></span>  
 <span data-ttu-id="19a65-124">Todos os tipos simples – os integrantes à linguagem C# – são aliases dos tipos de sistema do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="19a65-124">All of the simple types -- those integral to the C# language -- are aliases of the .NET Framework System types.</span></span> <span data-ttu-id="19a65-125">Por exemplo, [int](../../../csharp/language-reference/keywords/int.md) é um alias de <xref:System.Int32?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="19a65-125">For example, [int](../../../csharp/language-reference/keywords/int.md) is an alias of <xref:System.Int32?displayProperty=nameWithType>.</span></span> <span data-ttu-id="19a65-126">Para obter uma lista completa de aliases, consulte [Tabela de tipos internos](../../../csharp/language-reference/keywords/built-in-types-table.md).</span><span class="sxs-lookup"><span data-stu-id="19a65-126">For a complete list of aliases, see [Built-In Types Table](../../../csharp/language-reference/keywords/built-in-types-table.md).</span></span>  
  
 <span data-ttu-id="19a65-127">As expressões constantes, cujos operandos são todos constantes de tipo simples, são avaliadas em tempo de compilação.</span><span class="sxs-lookup"><span data-stu-id="19a65-127">Constant expressions, whose operands are all simple type constants, are evaluated at compilation time.</span></span>  
  
 <span data-ttu-id="19a65-128">Os tipos simples podem ser inicializados com o uso de literais.</span><span class="sxs-lookup"><span data-stu-id="19a65-128">Simple types can be initialized by using literals.</span></span> <span data-ttu-id="19a65-129">Por exemplo, 'A' é um literal do tipo `char` e 2001 é um literal do tipo `int`.</span><span class="sxs-lookup"><span data-stu-id="19a65-129">For example, 'A' is a literal of the type `char` and 2001 is a literal of the type `int`.</span></span>  
  
## <a name="initializing-value-types"></a><span data-ttu-id="19a65-130">Inicializando tipos de valor</span><span class="sxs-lookup"><span data-stu-id="19a65-130">Initializing Value Types</span></span>  
 <span data-ttu-id="19a65-131">As variáveis locais no C# devem ser inicializadas antes de serem usadas.</span><span class="sxs-lookup"><span data-stu-id="19a65-131">Local variables in C# must be initialized before they are used.</span></span> <span data-ttu-id="19a65-132">Por exemplo, você pode declarar uma variável local sem inicialização, como no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="19a65-132">For example, you might declare a local variable without initialization as in the following example:</span></span>  
  
```csharp  
int myInt;  
```  
  
 <span data-ttu-id="19a65-133">Você não pode usá-la antes de inicializá-la.</span><span class="sxs-lookup"><span data-stu-id="19a65-133">You cannot use it before you initialize it.</span></span> <span data-ttu-id="19a65-134">Você pode inicializar a variável usando a instrução a seguir:</span><span class="sxs-lookup"><span data-stu-id="19a65-134">You can initialize it using the following statement:</span></span>  
  
```csharp  
myInt = new int();  // Invoke default constructor for int type.  
```  
  
 <span data-ttu-id="19a65-135">Essa instrução é equivalente à instrução a seguir:</span><span class="sxs-lookup"><span data-stu-id="19a65-135">This statement is equivalent to the following statement:</span></span>  
  
```csharp  
myInt = 0;         // Assign an initial value, 0 in this example.  
```  
  
 <span data-ttu-id="19a65-136">É claro que a declaração e a inicialização podem ser feitas na mesma instrução, como nos exemplos a seguir:</span><span class="sxs-lookup"><span data-stu-id="19a65-136">You can, of course, have the declaration and the initialization in the same statement as in the following examples:</span></span>  
  
```csharp  
int myInt = new int();  
```  
  
 <span data-ttu-id="19a65-137">– ou –</span><span class="sxs-lookup"><span data-stu-id="19a65-137">–or–</span></span>  
  
```csharp  
int myInt = 0;  
```  
  
 <span data-ttu-id="19a65-138">Usando o operador [new](../../../csharp/language-reference/keywords/new.md), chama o construtor padrão do tipo específico e atribui o valor padrão à variável.</span><span class="sxs-lookup"><span data-stu-id="19a65-138">Using the [new](../../../csharp/language-reference/keywords/new.md) operator calls the default constructor of the specific type and assigns the default value to the variable.</span></span> <span data-ttu-id="19a65-139">No exemplo anterior, o construtor padrão atribuiu o valor `0` para `myInt`.</span><span class="sxs-lookup"><span data-stu-id="19a65-139">In the preceding example, the default constructor assigned the value `0` to `myInt`.</span></span> <span data-ttu-id="19a65-140">Para obter mais informações sobre valores atribuídos ao chamar construtores padrão, consulte [Tabela de valores padrão](../../../csharp/language-reference/keywords/default-values-table.md).</span><span class="sxs-lookup"><span data-stu-id="19a65-140">For more information about values assigned by calling default constructors, see [Default Values Table](../../../csharp/language-reference/keywords/default-values-table.md).</span></span>  
  
 <span data-ttu-id="19a65-141">Com tipos definidos pelo usuário, use [new](../../../csharp/language-reference/keywords/new.md) para invocar o construtor padrão.</span><span class="sxs-lookup"><span data-stu-id="19a65-141">With user-defined types, use [new](../../../csharp/language-reference/keywords/new.md) to invoke the default constructor.</span></span> <span data-ttu-id="19a65-142">Por exemplo, a instrução a seguir invoca o construtor padrão do struct `Point`:</span><span class="sxs-lookup"><span data-stu-id="19a65-142">For example, the following statement invokes the default constructor of the `Point` struct:</span></span>  
  
```csharp  
Point p = new Point(); // Invoke default constructor for the struct.  
```  
  
 <span data-ttu-id="19a65-143">Após esta chamada, o struct é considerado para ser definitivamente atribuído, ou seja, todos os seus membros são inicializados com seus valores padrão.</span><span class="sxs-lookup"><span data-stu-id="19a65-143">After this call, the struct is considered to be definitely assigned; that is, all its members are initialized to their default values.</span></span>  
  
 <span data-ttu-id="19a65-144">Para obter mais informações sobre o operador new, consulte [new](../../../csharp/language-reference/keywords/new.md).</span><span class="sxs-lookup"><span data-stu-id="19a65-144">For more information about the new operator, see [new](../../../csharp/language-reference/keywords/new.md).</span></span>  
  
 <span data-ttu-id="19a65-145">Para obter informações sobre a formatação da saída de tipos numéricos, consulte [Tabela de formatação de resultados numéricos](../../../csharp/language-reference/keywords/formatting-numeric-results-table.md).</span><span class="sxs-lookup"><span data-stu-id="19a65-145">For information about formatting the output of numeric types, see [Formatting Numeric Results Table](../../../csharp/language-reference/keywords/formatting-numeric-results-table.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19a65-146">Consulte também</span><span class="sxs-lookup"><span data-stu-id="19a65-146">See Also</span></span>

- [<span data-ttu-id="19a65-147">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="19a65-147">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="19a65-148">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="19a65-148">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="19a65-149">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="19a65-149">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
- [<span data-ttu-id="19a65-150">Tipos</span><span class="sxs-lookup"><span data-stu-id="19a65-150">Types</span></span>](../../../csharp/language-reference/keywords/types.md)  
- [<span data-ttu-id="19a65-151">Tabelas de referência de tipos</span><span class="sxs-lookup"><span data-stu-id="19a65-151">Reference Tables for Types</span></span>](../../../csharp/language-reference/keywords/reference-tables-for-types.md)  
- [<span data-ttu-id="19a65-152">Tipos de referência</span><span class="sxs-lookup"><span data-stu-id="19a65-152">Reference Types</span></span>](../../../csharp/language-reference/keywords/reference-types.md)  
- [<span data-ttu-id="19a65-153">Tipos que permitem valor nulo</span><span class="sxs-lookup"><span data-stu-id="19a65-153">Nullable types</span></span>](../../programming-guide/nullable-types/index.md)  
