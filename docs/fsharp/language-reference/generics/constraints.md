---
title: Restrições
description: Saiba mais F# sobre restrições que se aplicam a parâmetros de tipo genérico para especificar os requisitos para um argumento de tipo em um tipo ou função genérica.
ms.date: 05/16/2016
ms.openlocfilehash: 9912ba63138d893a7c616661dd2b1cbdbe51916c
ms.sourcegitcommit: 878ca7550b653114c3968ef8906da2b3e60e3c7a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/02/2019
ms.locfileid: "71736798"
---
# <a name="constraints"></a><span data-ttu-id="1d237-103">Restrições</span><span class="sxs-lookup"><span data-stu-id="1d237-103">Constraints</span></span>

<span data-ttu-id="1d237-104">Este tópico descreve as restrições que você pode aplicar a parâmetros de tipo genérico para especificar os requisitos para um argumento de tipo em um tipo ou função genérica.</span><span class="sxs-lookup"><span data-stu-id="1d237-104">This topic describes constraints that you can apply to generic type parameters to specify the requirements for a type argument in a generic type or function.</span></span>

## <a name="syntax"></a><span data-ttu-id="1d237-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1d237-105">Syntax</span></span>

```fsharp
type-parameter-list when constraint1 [ and constraint2]
```

## <a name="remarks"></a><span data-ttu-id="1d237-106">Comentários</span><span class="sxs-lookup"><span data-stu-id="1d237-106">Remarks</span></span>

<span data-ttu-id="1d237-107">Há várias restrições diferentes que você pode aplicar para limitar os tipos que podem ser usados em um tipo genérico.</span><span class="sxs-lookup"><span data-stu-id="1d237-107">There are several different constraints you can apply to limit the types that can be used in a generic type.</span></span> <span data-ttu-id="1d237-108">A tabela a seguir lista e descreve essas restrições.</span><span class="sxs-lookup"><span data-stu-id="1d237-108">The following table lists and describes these constraints.</span></span>

|<span data-ttu-id="1d237-109">Restrição</span><span class="sxs-lookup"><span data-stu-id="1d237-109">Constraint</span></span>|<span data-ttu-id="1d237-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1d237-110">Syntax</span></span>|<span data-ttu-id="1d237-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="1d237-111">Description</span></span>|
|----------|------|-----------|
|<span data-ttu-id="1d237-112">Restrição de tipo</span><span class="sxs-lookup"><span data-stu-id="1d237-112">Type Constraint</span></span>|<span data-ttu-id="1d237-113">*type-parameter* :&gt; *type*</span><span class="sxs-lookup"><span data-stu-id="1d237-113">*type-parameter* :&gt; *type*</span></span>|<span data-ttu-id="1d237-114">O tipo fornecido deve ser igual ou derivado do tipo especificado, ou, se o tipo for uma interface, o tipo fornecido deverá implementar a interface.</span><span class="sxs-lookup"><span data-stu-id="1d237-114">The provided type must be equal to or derived from the type specified, or, if the type is an interface, the provided type must implement the interface.</span></span>|
|<span data-ttu-id="1d237-115">Restrição NULL</span><span class="sxs-lookup"><span data-stu-id="1d237-115">Null Constraint</span></span>|<span data-ttu-id="1d237-116">*type-parameter* : null</span><span class="sxs-lookup"><span data-stu-id="1d237-116">*type-parameter* : null</span></span>|<span data-ttu-id="1d237-117">O tipo fornecido deve dar suporte ao literal nulo.</span><span class="sxs-lookup"><span data-stu-id="1d237-117">The provided type must support the null literal.</span></span> <span data-ttu-id="1d237-118">Isso inclui todos os tipos de objeto do F# .net, mas não os tipos lista, tupla, função, classe, registro ou União.</span><span class="sxs-lookup"><span data-stu-id="1d237-118">This includes all .NET object types but not F# list, tuple, function, class, record, or union types.</span></span>|
|<span data-ttu-id="1d237-119">Restrição de membro explícita</span><span class="sxs-lookup"><span data-stu-id="1d237-119">Explicit Member Constraint</span></span>|<span data-ttu-id="1d237-120">[(]*parâmetro de tipo* [ou... ou *parâmetro de tipo*)]: (*assinatura do membro*)</span><span class="sxs-lookup"><span data-stu-id="1d237-120">[(]*type-parameter* [or ... or *type-parameter*)] : (*member-signature*)</span></span>|<span data-ttu-id="1d237-121">Pelo menos um dos argumentos de tipo fornecidos deve ter um membro que tenha a assinatura especificada; Não se destina ao uso comum.</span><span class="sxs-lookup"><span data-stu-id="1d237-121">At least one of the type arguments provided must have a member that has the specified signature; not intended for common use.</span></span> <span data-ttu-id="1d237-122">Os membros devem ser explicitamente definidos no tipo ou parte de uma extensão de tipo implícita para serem destinos válidos para uma restrição de membro explícita.</span><span class="sxs-lookup"><span data-stu-id="1d237-122">Members must be either explicitly defined on the type or part of an implicit type extension to be valid targets for an Explicit Member Constraint.</span></span>|
|<span data-ttu-id="1d237-123">Restrição de Construtor</span><span class="sxs-lookup"><span data-stu-id="1d237-123">Constructor Constraint</span></span>|<span data-ttu-id="1d237-124">*tipo-parâmetro* : (novo: unidade-&gt; ' a)</span><span class="sxs-lookup"><span data-stu-id="1d237-124">*type-parameter* : ( new : unit -&gt; 'a )</span></span>|<span data-ttu-id="1d237-125">O tipo fornecido deve ter um construtor sem parâmetros.</span><span class="sxs-lookup"><span data-stu-id="1d237-125">The provided type must have a parameterless constructor.</span></span>|
|<span data-ttu-id="1d237-126">Restrição de tipo de valor</span><span class="sxs-lookup"><span data-stu-id="1d237-126">Value Type Constraint</span></span>|<span data-ttu-id="1d237-127">: struct</span><span class="sxs-lookup"><span data-stu-id="1d237-127">: struct</span></span>|<span data-ttu-id="1d237-128">O tipo fornecido deve ser um tipo de valor .NET.</span><span class="sxs-lookup"><span data-stu-id="1d237-128">The provided type must be a .NET value type.</span></span>|
|<span data-ttu-id="1d237-129">Restrição de tipo de referência</span><span class="sxs-lookup"><span data-stu-id="1d237-129">Reference Type Constraint</span></span>|<span data-ttu-id="1d237-130">: não struct</span><span class="sxs-lookup"><span data-stu-id="1d237-130">: not struct</span></span>|<span data-ttu-id="1d237-131">O tipo fornecido deve ser um tipo de referência do .NET.</span><span class="sxs-lookup"><span data-stu-id="1d237-131">The provided type must be a .NET reference type.</span></span>|
|<span data-ttu-id="1d237-132">Restrição de tipo de enumeração</span><span class="sxs-lookup"><span data-stu-id="1d237-132">Enumeration Type Constraint</span></span>|<span data-ttu-id="1d237-133">: enum @ no__t-0*tipo subjacente*&gt;</span><span class="sxs-lookup"><span data-stu-id="1d237-133">: enum&lt;*underlying-type*&gt;</span></span>|<span data-ttu-id="1d237-134">O tipo fornecido deve ser um tipo enumerado que tenha o tipo subjacente especificado; Não se destina ao uso comum.</span><span class="sxs-lookup"><span data-stu-id="1d237-134">The provided type must be an enumerated type that has the specified underlying type; not intended for common use.</span></span>|
|<span data-ttu-id="1d237-135">Delegar restrição</span><span class="sxs-lookup"><span data-stu-id="1d237-135">Delegate Constraint</span></span>|<span data-ttu-id="1d237-136">: delegate @ no__t-0*tupla-Parameter-Type*, *tipo de retorno*&gt;</span><span class="sxs-lookup"><span data-stu-id="1d237-136">: delegate&lt;*tuple-parameter-type*, *return-type*&gt;</span></span>|<span data-ttu-id="1d237-137">O tipo fornecido deve ser um tipo delegado que tenha os argumentos especificados e o valor de retorno; Não se destina ao uso comum.</span><span class="sxs-lookup"><span data-stu-id="1d237-137">The provided type must be a delegate type that has the specified arguments and return value; not intended for common use.</span></span>|
|<span data-ttu-id="1d237-138">Restrição de comparação</span><span class="sxs-lookup"><span data-stu-id="1d237-138">Comparison Constraint</span></span>|<span data-ttu-id="1d237-139">: comparação</span><span class="sxs-lookup"><span data-stu-id="1d237-139">: comparison</span></span>|<span data-ttu-id="1d237-140">O tipo fornecido deve dar suporte à comparação.</span><span class="sxs-lookup"><span data-stu-id="1d237-140">The provided type must support comparison.</span></span>|
|<span data-ttu-id="1d237-141">Restrição de igualdade</span><span class="sxs-lookup"><span data-stu-id="1d237-141">Equality Constraint</span></span>|<span data-ttu-id="1d237-142">: igualdade</span><span class="sxs-lookup"><span data-stu-id="1d237-142">: equality</span></span>|<span data-ttu-id="1d237-143">O tipo fornecido deve dar suporte à igualdade.</span><span class="sxs-lookup"><span data-stu-id="1d237-143">The provided type must support equality.</span></span>|
|<span data-ttu-id="1d237-144">Restrição não gerenciada</span><span class="sxs-lookup"><span data-stu-id="1d237-144">Unmanaged Constraint</span></span>|<span data-ttu-id="1d237-145">: não gerenciado</span><span class="sxs-lookup"><span data-stu-id="1d237-145">: unmanaged</span></span>|<span data-ttu-id="1d237-146">O tipo fornecido deve ser um tipo não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="1d237-146">The provided type must be an unmanaged type.</span></span> <span data-ttu-id="1d237-147">Tipos não gerenciados são determinados tipos primitivos (`sbyte`, `byte`, `char`, `nativeint`, `unativeint`, `float32`, `float`, `int16`, `uint16`, `int32`, 0, 1, 2 ou 3), tipos de enumeração, 4 ou um não genérico estrutura cujos campos são todos os tipos não gerenciados.</span><span class="sxs-lookup"><span data-stu-id="1d237-147">Unmanaged types are either certain primitive types (`sbyte`, `byte`, `char`, `nativeint`, `unativeint`, `float32`, `float`, `int16`, `uint16`, `int32`, `uint32`, `int64`, `uint64`, or `decimal`), enumeration types, `nativeptr<_>`, or a non-generic structure whose fields are all unmanaged types.</span></span>|

<span data-ttu-id="1d237-148">Você precisa adicionar uma restrição quando seu código precisa usar um recurso que está disponível no tipo de restrição, mas não em tipos em geral.</span><span class="sxs-lookup"><span data-stu-id="1d237-148">You have to add a constraint when your code has to use a feature that is available on the constraint type but not on types in general.</span></span> <span data-ttu-id="1d237-149">Por exemplo, se você usar a restrição de tipo para especificar um tipo de classe, poderá usar qualquer um dos métodos dessa classe na função ou no tipo genérico.</span><span class="sxs-lookup"><span data-stu-id="1d237-149">For example, if you use the type constraint to specify a class type, you can use any one of the methods of that class in the generic function or type.</span></span>

<span data-ttu-id="1d237-150">Às vezes, especificar restrições é necessário ao escrever parâmetros de tipo explicitamente, porque sem uma restrição, o compilador não tem como verificar se os recursos que você está usando estará disponível em qualquer tipo que possa ser fornecido no tempo de execução para o tipo meter.</span><span class="sxs-lookup"><span data-stu-id="1d237-150">Specifying constraints is sometimes required when writing type parameters explicitly, because without a constraint, the compiler has no way of verifying that the features that you are using will be available on any type that might be supplied at run time for the type parameter.</span></span>

<span data-ttu-id="1d237-151">As restrições mais comuns que você usa F# no código são restrições de tipo que especificam classes ou interfaces base.</span><span class="sxs-lookup"><span data-stu-id="1d237-151">The most common constraints you use in F# code are type constraints that specify base classes or interfaces.</span></span> <span data-ttu-id="1d237-152">As outras restrições são usadas pela F# biblioteca para implementar determinadas funcionalidades, como a restrição de membro explícita, que é usada para implementar a sobrecarga de operador para operadores aritméticos ou são fornecidas principalmente porque F# dá suporte ao conjunto completo de restrições com suporte pelo Common Language Runtime.</span><span class="sxs-lookup"><span data-stu-id="1d237-152">The other constraints are either used by the F# library to implement certain functionality, such as the explicit member constraint, which is used to implement operator overloading for arithmetic operators, or are provided mainly because F# supports the complete set of constraints that is supported by the common language runtime.</span></span>

<span data-ttu-id="1d237-153">Durante o processo de inferência de tipos, algumas restrições são inferidas automaticamente pelo compilador.</span><span class="sxs-lookup"><span data-stu-id="1d237-153">During the type inference process, some constraints are inferred automatically by the compiler.</span></span> <span data-ttu-id="1d237-154">Por exemplo, se você usar o operador `+` em uma função, o compilador inferirá uma restrição de membro explícita em tipos de variáveis que são usados na expressão.</span><span class="sxs-lookup"><span data-stu-id="1d237-154">For example, if you use the `+` operator in a function, the compiler infers an explicit member constraint on variable types that are used in the expression.</span></span>

<span data-ttu-id="1d237-155">O código a seguir ilustra algumas declarações de restrição:</span><span class="sxs-lookup"><span data-stu-id="1d237-155">The following code illustrates some constraint declarations:</span></span>

```fsharp
// Base Type Constraint
type Class1<'T when 'T :> System.Exception> =
class end

// Interface Type Constraint
type Class2<'T when 'T :> System.IComparable> = 
class end

// Null constraint
type Class3<'T when 'T : null> =
class end

// Member constraint with instance member
type Class5<'T when 'T : (member Method1 : 'T -> int)> =
class end

// Member constraint with property
type Class6<'T when 'T : (member Property1 : int)> =
class end

// Constructor constraint
type Class7<'T when 'T : (new : unit -> 'T)>() =
member val Field = new 'T()

// Reference type constraint
type Class8<'T when 'T : not struct> =
class end

// Enumeration constraint with underlying value specified
type Class9<'T when 'T : enum<uint32>> =
class end

// 'T must implement IComparable, or be an array type with comparable
// elements, or be System.IntPtr or System.UIntPtr. Also, 'T must not have
// the NoComparison attribute.
type Class10<'T when 'T : comparison> =
class end

// 'T must support equality. This is true for any type that does not
// have the NoEquality attribute.
type Class11<'T when 'T : equality> =
class end

type Class12<'T when 'T : delegate<obj * System.EventArgs, unit>> =
class end

type Class13<'T when 'T : unmanaged> =
class end

// Member constraints with two type parameters
// Most often used with static type parameters in inline functions
let inline add(value1 : ^T when ^T : (static member (+) : ^T * ^T -> ^T), value2: ^T) =
value1 + value2

// ^T and ^U must support operator +
let inline heterogenousAdd(value1 : ^T when (^T or ^U) : (static member (+) : ^T * ^U -> ^T), value2 : ^U) =
value1 + value2

// If there are multiple constraints, use the and keyword to separate them.
type Class14<'T,'U when 'T : equality and 'U : equality> =
class end
```

## <a name="see-also"></a><span data-ttu-id="1d237-156">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1d237-156">See also</span></span>

- [<span data-ttu-id="1d237-157">Genéricos</span><span class="sxs-lookup"><span data-stu-id="1d237-157">Generics</span></span>](index.md)
- [<span data-ttu-id="1d237-158">Restrições</span><span class="sxs-lookup"><span data-stu-id="1d237-158">Constraints</span></span>](constraints.md)
