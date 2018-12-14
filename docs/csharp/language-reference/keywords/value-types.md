---
title: Tipos de valor (Referência de C#)
ms.date: 11/26/2018
f1_keywords:
- cs.valuetypes
helpviewer_keywords:
- value types [C#]
- types [C#], value types
- C# language, value types
ms.assetid: 471eb994-2958-49d5-a6be-19b4313f80a3
ms.openlocfilehash: baf0db751cd70d50d4cf440626dd405b01c8d7ad
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53147705"
---
# <a name="value-types-c-reference"></a><span data-ttu-id="7c109-102">Tipos de valor (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="7c109-102">Value types (C# Reference)</span></span>

<span data-ttu-id="7c109-103">Há dois tipos de valor:</span><span class="sxs-lookup"><span data-stu-id="7c109-103">There are two kinds of value types:</span></span>

- [<span data-ttu-id="7c109-104">Estruturas</span><span class="sxs-lookup"><span data-stu-id="7c109-104">Structs</span></span>](struct.md)

- [<span data-ttu-id="7c109-105">Enumerações</span><span class="sxs-lookup"><span data-stu-id="7c109-105">Enumerations</span></span>](enum.md)

## <a name="main-features-of-value-types"></a><span data-ttu-id="7c109-106">Principais recursos dos tipos de valor</span><span class="sxs-lookup"><span data-stu-id="7c109-106">Main features of value types</span></span>

<span data-ttu-id="7c109-107">Uma variável de um tipo de valor contém um valor do tipo.</span><span class="sxs-lookup"><span data-stu-id="7c109-107">A variable of a value type contains a value of the type.</span></span> <span data-ttu-id="7c109-108">Por exemplo, uma variável do tipo `int` pode conter o valor `42`.</span><span class="sxs-lookup"><span data-stu-id="7c109-108">For example, a variable of the `int` type might contain the value `42`.</span></span> <span data-ttu-id="7c109-109">Isso é diferente de uma variável de um tipo de referência, que contém uma referência a uma instância do tipo, também conhecida como um objeto.</span><span class="sxs-lookup"><span data-stu-id="7c109-109">This differs from a variable of a reference type, which contains a reference to an instance of the type, also known as an object.</span></span> <span data-ttu-id="7c109-110">Quando você atribui um novo valor a uma variável de um tipo de valor, esse valor é copiado.</span><span class="sxs-lookup"><span data-stu-id="7c109-110">When you assign a new value to a variable of a value type, that value is copied.</span></span> <span data-ttu-id="7c109-111">Quando você atribui um novo valor a uma variável de um tipo de referência, a referência é copiada, não o objeto.</span><span class="sxs-lookup"><span data-stu-id="7c109-111">When you assign a new value to a variable of a reference type, the reference is copied, not the object itself.</span></span>

<span data-ttu-id="7c109-112">Todos os tipos de valor são derivados implicitamente da <xref:System.ValueType?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="7c109-112">All value types are derived implicitly from the <xref:System.ValueType?displayProperty=nameWithType>.</span></span>  
  
<span data-ttu-id="7c109-113">Ao contrário do que acontece com tipos de referência, você não pode derivar um novo tipo de um tipo de valor.</span><span class="sxs-lookup"><span data-stu-id="7c109-113">Unlike with reference types, you cannot derive a new type from a value type.</span></span> <span data-ttu-id="7c109-114">No entanto, assim como com tipos de referência, os structs podem implementar interfaces.</span><span class="sxs-lookup"><span data-stu-id="7c109-114">However, like reference types, structs can implement interfaces.</span></span>  
  
<span data-ttu-id="7c109-115">Variáveis de tipo de valor não podem ser `null` por padrão.</span><span class="sxs-lookup"><span data-stu-id="7c109-115">Value type variables cannot be `null` by default.</span></span> <span data-ttu-id="7c109-116">No entanto, as variáveis dos [tipos que permitem valor nulo](../../../csharp/programming-guide/nullable-types/index.md) correspondentes podem ser `null`.</span><span class="sxs-lookup"><span data-stu-id="7c109-116">However, variables of the corresponding [nullable types](../../../csharp/programming-guide/nullable-types/index.md) can be `null`.</span></span>
  
<span data-ttu-id="7c109-117">Cada tipo de valor tem um construtor padrão implícito que inicializa o valor padrão desse tipo.</span><span class="sxs-lookup"><span data-stu-id="7c109-117">Each value type has an implicit default constructor that initializes the default value of that type.</span></span> <span data-ttu-id="7c109-118">Para saber mais sobre valores padrão de tipos de valor, consulte [Tabela de valores padrão](default-values-table.md).</span><span class="sxs-lookup"><span data-stu-id="7c109-118">For information about default values of value types, see [Default values table](default-values-table.md).</span></span>  
  
## <a name="simple-types"></a><span data-ttu-id="7c109-119">Tipos simples</span><span class="sxs-lookup"><span data-stu-id="7c109-119">Simple types</span></span>

<span data-ttu-id="7c109-120">Os *tipos simples* são um conjunto de tipos de struct predefinidos fornecidos por C# e incluem os seguintes tipos:</span><span class="sxs-lookup"><span data-stu-id="7c109-120">The *simple types* are a set of predefined struct types provided by C# and comprise the following types:</span></span>

- <span data-ttu-id="7c109-121">[Tipos integrais](integral-types-table.md): tipos numéricos inteiros e o tipo [char](char.md)</span><span class="sxs-lookup"><span data-stu-id="7c109-121">[Integral types](integral-types-table.md): integer numeric types and the [char](char.md) type</span></span>
- [<span data-ttu-id="7c109-122">Tipos de ponto flutuante</span><span class="sxs-lookup"><span data-stu-id="7c109-122">Floating-point types</span></span>](floating-point-types-table.md)
- [<span data-ttu-id="7c109-123">bool</span><span class="sxs-lookup"><span data-stu-id="7c109-123">bool</span></span>](bool.md)

<span data-ttu-id="7c109-124">Os tipos simples são identificados por meio de palavras-chave, mas essas palavras-chave são simplesmente aliases para tipos de struct predefinidos no namespace <xref:System>.</span><span class="sxs-lookup"><span data-stu-id="7c109-124">The simple types are identified through keywords, but these keywords are simply aliases for predefined struct types in the <xref:System> namespace.</span></span> <span data-ttu-id="7c109-125">Por exemplo, [int](int.md) é um alias de <xref:System.Int32?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="7c109-125">For example, [int](int.md) is an alias of <xref:System.Int32?displayProperty=nameWithType>.</span></span> <span data-ttu-id="7c109-126">Para obter uma lista completa de aliases, consulte [Tabela de tipos internos](built-in-types-table.md).</span><span class="sxs-lookup"><span data-stu-id="7c109-126">For a complete list of aliases, see [Built-in types table](built-in-types-table.md).</span></span>

<span data-ttu-id="7c109-127">Os tipos simples diferem de outros tipos de struct, pois permitem determinadas operações adicionais:</span><span class="sxs-lookup"><span data-stu-id="7c109-127">The simple types differ from other struct types in that they permit certain additional operations:</span></span>

- <span data-ttu-id="7c109-128">Os tipos simples podem ser inicializados com o uso de literais.</span><span class="sxs-lookup"><span data-stu-id="7c109-128">Simple types can be initialized by using literals.</span></span> <span data-ttu-id="7c109-129">Por exemplo, `'A'` é um literal do tipo `char` e `2001` é um literal do tipo `int`.</span><span class="sxs-lookup"><span data-stu-id="7c109-129">For example, `'A'` is a literal of the type `char` and `2001` is a literal of the type `int`.</span></span>

- <span data-ttu-id="7c109-130">Você pode declarar constantes dos tipos simples com a palavra-chave [const](const.md).</span><span class="sxs-lookup"><span data-stu-id="7c109-130">You can declare constants of the simple types with the [const](const.md) keyword.</span></span> <span data-ttu-id="7c109-131">Não é possível ter constantes de outros tipos de struct.</span><span class="sxs-lookup"><span data-stu-id="7c109-131">It's not possible to have constants of other struct types.</span></span>

- <span data-ttu-id="7c109-132">As expressões constantes, cujos operandos são todos constantes de tipo simples, são avaliadas em tempo de compilação.</span><span class="sxs-lookup"><span data-stu-id="7c109-132">Constant expressions, whose operands are all simple type constants, are evaluated at compile time.</span></span>

<span data-ttu-id="7c109-133">Para saber mais, confira a seção [Tipos simples](~/_csharplang/spec/types.md#simple-types) na [Especificação da linguagem C#](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="7c109-133">For more information, see the [Simple types](~/_csharplang/spec/types.md#simple-types) section of the [C# language specification](../language-specification/index.md).</span></span>
  
## <a name="initializing-value-types"></a><span data-ttu-id="7c109-134">Inicializando tipos de valor</span><span class="sxs-lookup"><span data-stu-id="7c109-134">Initializing value types</span></span>

 <span data-ttu-id="7c109-135">As variáveis locais no C# devem ser inicializadas antes de serem usadas.</span><span class="sxs-lookup"><span data-stu-id="7c109-135">Local variables in C# must be initialized before they are used.</span></span> <span data-ttu-id="7c109-136">Por exemplo, você pode declarar uma variável local sem inicialização, como no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="7c109-136">For example, you might declare a local variable without initialization as in the following example:</span></span>  
  
```csharp  
int myInt;  
```  
  
 <span data-ttu-id="7c109-137">Você não pode usá-la antes de inicializá-la.</span><span class="sxs-lookup"><span data-stu-id="7c109-137">You cannot use it before you initialize it.</span></span> <span data-ttu-id="7c109-138">Você pode inicializar a variável usando a instrução a seguir:</span><span class="sxs-lookup"><span data-stu-id="7c109-138">You can initialize it using the following statement:</span></span>  
  
```csharp  
myInt = new int();  // Invoke default constructor for int type.  
```  
  
 <span data-ttu-id="7c109-139">Essa instrução é equivalente à instrução a seguir:</span><span class="sxs-lookup"><span data-stu-id="7c109-139">This statement is equivalent to the following statement:</span></span>  
  
```csharp  
myInt = 0;         // Assign an initial value, 0 in this example.  
```  
  
 <span data-ttu-id="7c109-140">É claro que a declaração e a inicialização podem ser feitas na mesma instrução, como nos exemplos a seguir:</span><span class="sxs-lookup"><span data-stu-id="7c109-140">You can, of course, have the declaration and the initialization in the same statement as in the following examples:</span></span>  
  
```csharp  
int myInt = new int();  
```  
  
 <span data-ttu-id="7c109-141">– ou –</span><span class="sxs-lookup"><span data-stu-id="7c109-141">–or–</span></span>  
  
```csharp  
int myInt = 0;  
```  
  
 <span data-ttu-id="7c109-142">Usando o operador [new](new.md), chama o construtor padrão do tipo específico e atribui o valor padrão à variável.</span><span class="sxs-lookup"><span data-stu-id="7c109-142">Using the [new](new.md) operator calls the default constructor of the specific type and assigns the default value to the variable.</span></span> <span data-ttu-id="7c109-143">No exemplo anterior, o construtor padrão atribuiu o valor `0` para `myInt`.</span><span class="sxs-lookup"><span data-stu-id="7c109-143">In the preceding example, the default constructor assigned the value `0` to `myInt`.</span></span> <span data-ttu-id="7c109-144">Para obter mais informações sobre valores atribuídos ao chamar construtores padrão, consulte [Tabela de valores padrão](default-values-table.md).</span><span class="sxs-lookup"><span data-stu-id="7c109-144">For more information about values assigned by calling default constructors, see [Default values table](default-values-table.md).</span></span>  
  
 <span data-ttu-id="7c109-145">Com tipos definidos pelo usuário, use [new](new.md) para invocar o construtor padrão.</span><span class="sxs-lookup"><span data-stu-id="7c109-145">With user-defined types, use [new](new.md) to invoke the default constructor.</span></span> <span data-ttu-id="7c109-146">Por exemplo, a instrução a seguir invoca o construtor padrão do struct `Point`:</span><span class="sxs-lookup"><span data-stu-id="7c109-146">For example, the following statement invokes the default constructor of the `Point` struct:</span></span>  
  
```csharp  
Point p = new Point(); // Invoke default constructor for the struct.  
```  
  
 <span data-ttu-id="7c109-147">Após esta chamada, o struct é considerado para ser definitivamente atribuído, ou seja, todos os seus membros são inicializados com seus valores padrão.</span><span class="sxs-lookup"><span data-stu-id="7c109-147">After this call, the struct is considered to be definitely assigned; that is, all its members are initialized to their default values.</span></span>  
  
 <span data-ttu-id="7c109-148">Para saber mais sobre o operador `new`, confira [new](new.md).</span><span class="sxs-lookup"><span data-stu-id="7c109-148">For more information about the `new` operator, see [new](new.md).</span></span>  
  
 <span data-ttu-id="7c109-149">Para saber mais sobre a formatação da saída de tipos numéricos, consulte [Tabela de formatação de resultados numéricos](formatting-numeric-results-table.md).</span><span class="sxs-lookup"><span data-stu-id="7c109-149">For information about formatting the output of numeric types, see [Formatting numeric results table](formatting-numeric-results-table.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c109-150">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7c109-150">See also</span></span>

- [<span data-ttu-id="7c109-151">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="7c109-151">C# Reference</span></span>](../index.md)  
- [<span data-ttu-id="7c109-152">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="7c109-152">C# Programming Guide</span></span>](../../programming-guide/index.md)  
- [<span data-ttu-id="7c109-153">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="7c109-153">C# Keywords</span></span>](index.md)  
- [<span data-ttu-id="7c109-154">Tipos</span><span class="sxs-lookup"><span data-stu-id="7c109-154">Types</span></span>](types.md)  
- [<span data-ttu-id="7c109-155">Tabelas de referência de tipos</span><span class="sxs-lookup"><span data-stu-id="7c109-155">Reference tables for types</span></span>](reference-tables-for-types.md)  
- [<span data-ttu-id="7c109-156">Tipos de referência</span><span class="sxs-lookup"><span data-stu-id="7c109-156">Reference Types</span></span>](reference-types.md)  
- [<span data-ttu-id="7c109-157">Tipos que permitem valor nulo</span><span class="sxs-lookup"><span data-stu-id="7c109-157">Nullable types</span></span>](../../programming-guide/nullable-types/index.md)  
