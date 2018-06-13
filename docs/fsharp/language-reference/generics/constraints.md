---
title: Restrições (F#)
description: 'Saiba mais sobre F # restrições que se aplicam aos parâmetros de tipo genérico para especificar os requisitos para um argumento de tipo em um tipo genérico ou função.'
ms.date: 05/16/2016
ms.openlocfilehash: f0722cafe27a4e2c38dfbf091973edb136cf5228
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33562304"
---
# <a name="constraints"></a><span data-ttu-id="99ae7-103">Restrições</span><span class="sxs-lookup"><span data-stu-id="99ae7-103">Constraints</span></span>

<span data-ttu-id="99ae7-104">Este tópico descreve as restrições que você pode aplicar a genérico parâmetros para especificar os requisitos para um argumento de tipo em um tipo genérico ou uma função de tipo.</span><span class="sxs-lookup"><span data-stu-id="99ae7-104">This topic describes constraints that you can apply to generic type parameters to specify the requirements for a type argument in a generic type or function.</span></span>


## <a name="syntax"></a><span data-ttu-id="99ae7-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="99ae7-105">Syntax</span></span>

```fsharp
type-parameter-list when constraint1 [ and constraint2]
```

## <a name="remarks"></a><span data-ttu-id="99ae7-106">Comentários</span><span class="sxs-lookup"><span data-stu-id="99ae7-106">Remarks</span></span>
<span data-ttu-id="99ae7-107">Há várias restrições diferentes, que você pode aplicar para limitar os tipos que podem ser usados em um tipo genérico.</span><span class="sxs-lookup"><span data-stu-id="99ae7-107">There are several different constraints you can apply to limit the types that can be used in a generic type.</span></span> <span data-ttu-id="99ae7-108">A tabela a seguir lista e descreve essas restrições.</span><span class="sxs-lookup"><span data-stu-id="99ae7-108">The following table lists and describes these constraints.</span></span>

|<span data-ttu-id="99ae7-109">Restrição</span><span class="sxs-lookup"><span data-stu-id="99ae7-109">Constraint</span></span>|<span data-ttu-id="99ae7-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="99ae7-110">Syntax</span></span>|<span data-ttu-id="99ae7-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="99ae7-111">Description</span></span>|
|----------|------|-----------|
|<span data-ttu-id="99ae7-112">Restrição de tipo</span><span class="sxs-lookup"><span data-stu-id="99ae7-112">Type Constraint</span></span>|<span data-ttu-id="99ae7-113">*parâmetro de tipo* :&gt; *tipo*</span><span class="sxs-lookup"><span data-stu-id="99ae7-113">*type-parameter* :&gt; *type*</span></span>|<span data-ttu-id="99ae7-114">O tipo fornecido deve ser igual ou derivada do tipo especificado ou, se o tipo é uma interface, o tipo fornecido deve implementar a interface.</span><span class="sxs-lookup"><span data-stu-id="99ae7-114">The provided type must be equal to or derived from the type specified, or, if the type is an interface, the provided type must implement the interface.</span></span>|
|<span data-ttu-id="99ae7-115">Restrição de nulos</span><span class="sxs-lookup"><span data-stu-id="99ae7-115">Null Constraint</span></span>|<span data-ttu-id="99ae7-116">*parâmetro de tipo* : nulo</span><span class="sxs-lookup"><span data-stu-id="99ae7-116">*type-parameter* : null</span></span>|<span data-ttu-id="99ae7-117">O tipo fornecido deve dar suporte o literal nulo.</span><span class="sxs-lookup"><span data-stu-id="99ae7-117">The provided type must support the null literal.</span></span> <span data-ttu-id="99ae7-118">Isso inclui todos os tipos de objeto do .NET, mas não F # lista, tupla, função, classe, registro ou tipos de união.</span><span class="sxs-lookup"><span data-stu-id="99ae7-118">This includes all .NET object types but not F# list, tuple, function, class, record, or union types.</span></span>|
|<span data-ttu-id="99ae7-119">Restrição de membro explícito</span><span class="sxs-lookup"><span data-stu-id="99ae7-119">Explicit Member Constraint</span></span>|<span data-ttu-id="99ae7-120">[()]*parâmetro de tipo* [ou... ou *parâmetro de tipo*)]: (* assinatura de membro *)</span><span class="sxs-lookup"><span data-stu-id="99ae7-120">[(]*type-parameter* [or ... or *type-parameter*)] : (*member-signature *)</span></span>|<span data-ttu-id="99ae7-121">Pelo menos um dos argumentos de tipo fornecidos deve ter um membro que tem a assinatura especificada; não se destina para uso comum.</span><span class="sxs-lookup"><span data-stu-id="99ae7-121">At least one of the type arguments provided must have a member that has the specified signature; not intended for common use.</span></span> <span data-ttu-id="99ae7-122">Membros devem ser seja explicitamente definidos no tipo ou em parte de uma extensão de tipo implícito alvo válido de uma restrição de membro explícito.</span><span class="sxs-lookup"><span data-stu-id="99ae7-122">Members must be either explicitly defined on the type or part of an implicit type extension to be valid targets for an Explicit Member Constraint.</span></span>|
|<span data-ttu-id="99ae7-123">Restrição de construtor</span><span class="sxs-lookup"><span data-stu-id="99ae7-123">Constructor Constraint</span></span>|<span data-ttu-id="99ae7-124">*parâmetro de tipo* : (novo: unidade -&gt; ' um)</span><span class="sxs-lookup"><span data-stu-id="99ae7-124">*type-parameter* : ( new : unit -&gt; 'a )</span></span>|<span data-ttu-id="99ae7-125">O tipo fornecido deve ter um construtor padrão.</span><span class="sxs-lookup"><span data-stu-id="99ae7-125">The provided type must have a default constructor.</span></span>|
|<span data-ttu-id="99ae7-126">Restrição de tipo de valor</span><span class="sxs-lookup"><span data-stu-id="99ae7-126">Value Type Constraint</span></span>|<span data-ttu-id="99ae7-127">: struct</span><span class="sxs-lookup"><span data-stu-id="99ae7-127">: struct</span></span>|<span data-ttu-id="99ae7-128">O tipo fornecido deve ser um tipo de valor de .NET.</span><span class="sxs-lookup"><span data-stu-id="99ae7-128">The provided type must be a .NET value type.</span></span>|
|<span data-ttu-id="99ae7-129">Restrição de tipo de referência</span><span class="sxs-lookup"><span data-stu-id="99ae7-129">Reference Type Constraint</span></span>|<span data-ttu-id="99ae7-130">: não struct</span><span class="sxs-lookup"><span data-stu-id="99ae7-130">: not struct</span></span>|<span data-ttu-id="99ae7-131">O tipo fornecido deve ser um tipo de referência do .NET.</span><span class="sxs-lookup"><span data-stu-id="99ae7-131">The provided type must be a .NET reference type.</span></span>|
|<span data-ttu-id="99ae7-132">Restrição de tipo de enumeração</span><span class="sxs-lookup"><span data-stu-id="99ae7-132">Enumeration Type Constraint</span></span>|<span data-ttu-id="99ae7-133">: enum&lt;*tipo subjacente*&gt;</span><span class="sxs-lookup"><span data-stu-id="99ae7-133">: enum&lt;*underlying-type*&gt;</span></span>|<span data-ttu-id="99ae7-134">O tipo fornecido deve ser um tipo enumerado que tem o tipo base especificado. não se destina para uso comum.</span><span class="sxs-lookup"><span data-stu-id="99ae7-134">The provided type must be an enumerated type that has the specified underlying type; not intended for common use.</span></span>|
|<span data-ttu-id="99ae7-135">Restrição de representante</span><span class="sxs-lookup"><span data-stu-id="99ae7-135">Delegate Constraint</span></span>|<span data-ttu-id="99ae7-136">: Delegar&lt;*tipo de parâmetro de tupla*, *tipo de retorno*&gt;</span><span class="sxs-lookup"><span data-stu-id="99ae7-136">: delegate&lt;*tuple-parameter-type*, *return-type*&gt;</span></span>|<span data-ttu-id="99ae7-137">O tipo fornecido deve ser um tipo de delegado que tenha os argumentos especificados e retornar o valor. não se destina para uso comum.</span><span class="sxs-lookup"><span data-stu-id="99ae7-137">The provided type must be a delegate type that has the specified arguments and return value; not intended for common use.</span></span>|
|<span data-ttu-id="99ae7-138">Restrição de comparação</span><span class="sxs-lookup"><span data-stu-id="99ae7-138">Comparison Constraint</span></span>|<span data-ttu-id="99ae7-139">: comparação</span><span class="sxs-lookup"><span data-stu-id="99ae7-139">: comparison</span></span>|<span data-ttu-id="99ae7-140">O tipo fornecido deve oferecer suporte a comparação.</span><span class="sxs-lookup"><span data-stu-id="99ae7-140">The provided type must support comparison.</span></span>|
|<span data-ttu-id="99ae7-141">Restrição de igualdade</span><span class="sxs-lookup"><span data-stu-id="99ae7-141">Equality Constraint</span></span>|<span data-ttu-id="99ae7-142">: igualdade</span><span class="sxs-lookup"><span data-stu-id="99ae7-142">: equality</span></span>|<span data-ttu-id="99ae7-143">O tipo fornecido deve dar suporte a igualdade.</span><span class="sxs-lookup"><span data-stu-id="99ae7-143">The provided type must support equality.</span></span>|
|<span data-ttu-id="99ae7-144">Restrição não gerenciada</span><span class="sxs-lookup"><span data-stu-id="99ae7-144">Unmanaged Constraint</span></span>|<span data-ttu-id="99ae7-145">: não gerenciado</span><span class="sxs-lookup"><span data-stu-id="99ae7-145">: unmanaged</span></span>|<span data-ttu-id="99ae7-146">O tipo fornecido deve ser um tipo não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="99ae7-146">The provided type must be an unmanaged type.</span></span> <span data-ttu-id="99ae7-147">Tipos não gerenciados são determinados tipos de primitivo (`sbyte`, `byte`, `char`, `nativeint`, `unativeint`, `float32`, `float`, `int16`, `uint16`, `int32`, `uint32`, `int64`, `uint64`, ou `decimal`), tipos de enumeração, `nativeptr&lt;_&gt;`, ou uma estrutura genérica não cujos campos são todos os tipos não gerenciados.</span><span class="sxs-lookup"><span data-stu-id="99ae7-147">Unmanaged types are either certain primitive types (`sbyte`, `byte`, `char`, `nativeint`, `unativeint`, `float32`, `float`, `int16`, `uint16`, `int32`, `uint32`, `int64`, `uint64`, or `decimal`), enumeration types, `nativeptr&lt;_&gt;`, or a non-generic structure whose fields are all unmanaged types.</span></span>|
<span data-ttu-id="99ae7-148">Você precisa adicionar uma restrição quando seu código precisa usar um recurso que está disponível no tipo de restrição mas não em tipos em geral.</span><span class="sxs-lookup"><span data-stu-id="99ae7-148">You have to add a constraint when your code has to use a feature that is available on the constraint type but not on types in general.</span></span> <span data-ttu-id="99ae7-149">Por exemplo, se você usar a restrição de tipo para especificar um tipo de classe, você pode usar qualquer um dos métodos da classe no tipo ou função genérica.</span><span class="sxs-lookup"><span data-stu-id="99ae7-149">For example, if you use the type constraint to specify a class type, you can use any one of the methods of that class in the generic function or type.</span></span>

<span data-ttu-id="99ae7-150">Especificando restrições às vezes é necessária ao gravar os parâmetros de tipo explicitamente, porque sem uma restrição, o compilador não tem como verificar que os recursos que você está usando estejam disponíveis em qualquer tipo que pode ser fornecido em tempo de execução para o tipo parâmetro.</span><span class="sxs-lookup"><span data-stu-id="99ae7-150">Specifying constraints is sometimes required when writing type parameters explicitly, because without a constraint, the compiler has no way of verifying that the features that you are using will be available on any type that might be supplied at run time for the type parameter.</span></span>

<span data-ttu-id="99ae7-151">As restrições mais comuns que usar no código F # são restrições de tipo que especificar classes base ou interfaces.</span><span class="sxs-lookup"><span data-stu-id="99ae7-151">The most common constraints you use in F# code are type constraints that specify base classes or interfaces.</span></span> <span data-ttu-id="99ae7-152">As outras restrições são usadas pela biblioteca F # para implementar determinadas funcionalidades, como a restrição de membro explícito, que é usada para implementar o sobrecarregamento de operadores aritméticos ou é fornecida principalmente como F # oferece suporte completo conjunto de restrições que é compatível com o common language runtime.</span><span class="sxs-lookup"><span data-stu-id="99ae7-152">The other constraints are either used by the F# library to implement certain functionality, such as the explicit member constraint, which is used to implement operator overloading for arithmetic operators, or are provided mainly because F# supports the complete set of constraints that is supported by the common language runtime.</span></span>

<span data-ttu-id="99ae7-153">Durante o processo de inferência de tipo, algumas restrições são inferidas automaticamente pelo compilador.</span><span class="sxs-lookup"><span data-stu-id="99ae7-153">During the type inference process, some constraints are inferred automatically by the compiler.</span></span> <span data-ttu-id="99ae7-154">Por exemplo, se você usar o `+` operador em uma função, o compilador infere uma restrição de membro explícito em tipos de variáveis que são usadas na expressão.</span><span class="sxs-lookup"><span data-stu-id="99ae7-154">For example, if you use the `+` operator in a function, the compiler infers an explicit member constraint on variable types that are used in the expression.</span></span>

<span data-ttu-id="99ae7-155">O código a seguir mostra algumas declarações de restrição.</span><span class="sxs-lookup"><span data-stu-id="99ae7-155">The following code illustrates some constraint declarations.</span></span>

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

// Member constraint with static member
type Class4<'T when 'T : (static member staticMethod1 : unit -> 'T) > =
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

## <a name="see-also"></a><span data-ttu-id="99ae7-156">Consulte também</span><span class="sxs-lookup"><span data-stu-id="99ae7-156">See Also</span></span>
[<span data-ttu-id="99ae7-157">Genéricos</span><span class="sxs-lookup"><span data-stu-id="99ae7-157">Generics</span></span>](index.md)

[<span data-ttu-id="99ae7-158">Restrições</span><span class="sxs-lookup"><span data-stu-id="99ae7-158">Constraints</span></span>](constraints.md)
