---
title: Delegados Fortemente Tipados
description: "Saiba como usar tipos de delegado genérico para declarar tipos personalizados ao criar um recurso que exige delegados."
keywords: .NET, .NET Core
author: BillWagner
ms.author: wiwagn
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 564a683d-352b-4e57-8bac-b466529daf6b
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 0a8185c21e129c91b2c3ecb1f74f8ce2f75c5db9
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---

# <a name="strongly-typed-delegates"></a><span data-ttu-id="214ad-104">Delegados Fortemente Tipados</span><span class="sxs-lookup"><span data-stu-id="214ad-104">Strongly Typed Delegates</span></span>

[<span data-ttu-id="214ad-105">Anterior</span><span class="sxs-lookup"><span data-stu-id="214ad-105">Previous</span></span>](delegate-class.md)

<span data-ttu-id="214ad-106">No artigo anterior, você viu como criar tipos de delegado específicos usando a palavra-chave `delegate`.</span><span class="sxs-lookup"><span data-stu-id="214ad-106">In the previous article, you saw that you create specific delegate types using the `delegate` keyword.</span></span> 

<span data-ttu-id="214ad-107">A classe de delegado abstrata fornece a infraestrutura para a invocação e acoplamento fraco.</span><span class="sxs-lookup"><span data-stu-id="214ad-107">The abstract Delegate class provide the infrastructure for loose coupling and invocation.</span></span> <span data-ttu-id="214ad-108">Os tipos de delegado concretos se tornam muito mais úteis adotando e impondo a segurança de tipos para os métodos que são adicionados à lista de invocação para um objeto delegado.</span><span class="sxs-lookup"><span data-stu-id="214ad-108">Concrete Delegate types become much more useful by embracing and enforcing type safety for the methods that are added to the invocation list for a delegate object.</span></span> <span data-ttu-id="214ad-109">Quando você usa a palavra-chave `delegate` e define um tipo de delegado concreto, o compilador gera esses métodos.</span><span class="sxs-lookup"><span data-stu-id="214ad-109">When you use the `delegate` keyword and define a concrete delegate type, the compiler generates those methods.</span></span>

<span data-ttu-id="214ad-110">Na prática, isso poderia levar à criação de novos tipos de delegado sempre que precisar de uma assinatura de método diferente.</span><span class="sxs-lookup"><span data-stu-id="214ad-110">In practice, this would lead to creating new delegate types whenever you need a different method signature.</span></span> <span data-ttu-id="214ad-111">Esse trabalho pode se tornar entediante depois de um tempo.</span><span class="sxs-lookup"><span data-stu-id="214ad-111">This work could get tedious after a time.</span></span> <span data-ttu-id="214ad-112">Cada novo recurso exige novos tipos de delegado.</span><span class="sxs-lookup"><span data-stu-id="214ad-112">Every new feature requires new delegate types.</span></span>

<span data-ttu-id="214ad-113">Felizmente, isso não é necessário.</span><span class="sxs-lookup"><span data-stu-id="214ad-113">Thankfully, this isn't necessary.</span></span> <span data-ttu-id="214ad-114">O .NET Core Framework contém vários tipos que podem ser reutilizados sempre que você precisar de tipos de delegado.</span><span class="sxs-lookup"><span data-stu-id="214ad-114">The .NET Core framework contains several types that you can reuse whenever you need delegate types.</span></span> <span data-ttu-id="214ad-115">Essas são definições [genéricas](programming-guide/generics/index.md) para que você possa declarar personalizações quando precisar de novas declarações de método.</span><span class="sxs-lookup"><span data-stu-id="214ad-115">These are [generic](programming-guide/generics/index.md) definitions so you can declare customizations when you need new method declarations.</span></span> 

<span data-ttu-id="214ad-116">O primeiro desses tipos é o tipo @System.Action e diversas variações:</span><span class="sxs-lookup"><span data-stu-id="214ad-116">The first of these types is the @System.Action type, and several variations:</span></span>

```csharp
public delegate void Action();
public delegate void Action<in T>(T arg);
public delegate void Action<in T1, in T2>(T1 arg1, T2 arg2);
// Other variations removed for brevity.
```

<span data-ttu-id="214ad-117">O modificador `in` no argumento de tipo genérico é abordado neste artigo sobre covariância.</span><span class="sxs-lookup"><span data-stu-id="214ad-117">The `in` modifier on the generic type argument is covered in the article on covariance.</span></span>

<span data-ttu-id="214ad-118">Há variações do delegado `Action` que contêm até 16 argumentos como @System.Action%6016.</span><span class="sxs-lookup"><span data-stu-id="214ad-118">There are variations of the `Action` delegate that contain up to 16 arguments such as @System.Action%6016 .</span></span>
<span data-ttu-id="214ad-119">É importante que essas definições usem argumentos genéricos diferentes para cada um dos argumentos do delegado: isso proporciona a máxima flexibilidade.</span><span class="sxs-lookup"><span data-stu-id="214ad-119">It's important that these definitions use different generic arguments for each of the delegate arguments: That gives you maximum flexibility.</span></span> <span data-ttu-id="214ad-120">Os argumentos de método não precisam ser, mas podem ser, do mesmo tipo.</span><span class="sxs-lookup"><span data-stu-id="214ad-120">The method arguments need not be, but may be, the same type.</span></span>

<span data-ttu-id="214ad-121">Use um dos tipos `Action` para qualquer tipo de delegado que tenha um tipo de retorno nulo.</span><span class="sxs-lookup"><span data-stu-id="214ad-121">Use one of the `Action` types for any delegate type that has a void return type.</span></span>

<span data-ttu-id="214ad-122">A estrutura também inclui vários tipos de delegado genérico que você pode usar para tipos de delegado que retornam valores:</span><span class="sxs-lookup"><span data-stu-id="214ad-122">The framework also includes several generic delegate types that you can use for delegate types that return values:</span></span>

```csharp
public delegate TResult Func<out TResult>();
public delegate TResult Func<in T1, out TResult>(T1 arg);
public delegate TResult Func<in T1, in T2, out TResult>(T1 arg1, T2 arg2);
// Other variations removed for brevity
```

<span data-ttu-id="214ad-123">O modificador `out` no argumento de tipo genérico de resultado é abordado neste artigo sobre covariância.</span><span class="sxs-lookup"><span data-stu-id="214ad-123">The `out` modifier on the result generic type argument is covered in the article on covariance.</span></span>

<span data-ttu-id="214ad-124">Há variações do delegado `Func` com até 16 argumentos de entrada como @System.Func%6017.</span><span class="sxs-lookup"><span data-stu-id="214ad-124">There are variations of the `Func` delegate with up to 16 input arguments such as @System.Func%6017 .</span></span>
<span data-ttu-id="214ad-125">O tipo do resultado é sempre o último parâmetro de tipo em todas as declarações `Func`, por convenção.</span><span class="sxs-lookup"><span data-stu-id="214ad-125">The type of the result is always the last type parameter in all the `Func` declarations, by convention.</span></span>

<span data-ttu-id="214ad-126">Use um dos tipos `Func` para qualquer tipo de delegado que retorna um valor.</span><span class="sxs-lookup"><span data-stu-id="214ad-126">Use one of the `Func` types for any delegate type that returns a value.</span></span>

<span data-ttu-id="214ad-127">Há também um tipo @System.Predicate%601 especializado para um delegado que retorna um teste em um único valor:</span><span class="sxs-lookup"><span data-stu-id="214ad-127">There's also a specialized @System.Predicate%601 type for a delegate that returns a test on a single value:</span></span>

```csharp
public delegate bool Predicate<in T>(T obj);
```

<span data-ttu-id="214ad-128">Você pode observar que para qualquer tipo `Predicate`, há um tipo `Func` estruturalmente equivalente, por exemplo:</span><span class="sxs-lookup"><span data-stu-id="214ad-128">You may notice that for any `Predicate` type, a structurally equivalent `Func` type exists For example:</span></span>

```csharp
Func<string, bool> TestForString;
Predicate<string> AnotherTestForString;
```

<span data-ttu-id="214ad-129">Você pode pensar que esses dois tipos são equivalentes.</span><span class="sxs-lookup"><span data-stu-id="214ad-129">You might think these two types are equivalent.</span></span> <span data-ttu-id="214ad-130">Eles não são.</span><span class="sxs-lookup"><span data-stu-id="214ad-130">They are not.</span></span>
<span data-ttu-id="214ad-131">Essas duas variáveis não podem ser usadas alternadamente.</span><span class="sxs-lookup"><span data-stu-id="214ad-131">These two variables cannot be used interchangeably.</span></span> <span data-ttu-id="214ad-132">Uma variável de um tipo não pode ser atribuída o outro tipo.</span><span class="sxs-lookup"><span data-stu-id="214ad-132">A variable of one type cannot be assigned the other type.</span></span> <span data-ttu-id="214ad-133">O sistema de tipo do C# usa os nomes dos tipos definidos, não a estrutura.</span><span class="sxs-lookup"><span data-stu-id="214ad-133">The C# type system uses the names of the defined types, not the structure.</span></span>

<span data-ttu-id="214ad-134">Todas essas definições de tipo de delegado na Biblioteca do .NET Core devem significar que você não precisa definir um novo tipo de delegado para qualquer novo recurso criado que exige delegados.</span><span class="sxs-lookup"><span data-stu-id="214ad-134">All these delegate type definitions in the .NET Core Library should mean that you do not need to define a new delegate type for any new feature you create that requires delegates.</span></span> <span data-ttu-id="214ad-135">Essas definições genéricas devem fornecer todos os tipos de delegado necessários na maioria das situações.</span><span class="sxs-lookup"><span data-stu-id="214ad-135">These generic definitions should provide all the delegate types you need under most situations.</span></span> <span data-ttu-id="214ad-136">Você pode simplesmente instanciar um desses tipos com os parâmetros de tipo necessários.</span><span class="sxs-lookup"><span data-stu-id="214ad-136">You can simply instantiate one of these types with the required type parameters.</span></span> <span data-ttu-id="214ad-137">No caso de algoritmos que podem ser tornados genéricos, esses delegados podem ser usados como tipos genéricos.</span><span class="sxs-lookup"><span data-stu-id="214ad-137">In the case of algorithms that can be made generic, these delegates can be used as generic types.</span></span> 

<span data-ttu-id="214ad-138">Isso deve economizar tempo e minimizar o número de novos tipos de que você precisa criar a fim de trabalhar com delegados.</span><span class="sxs-lookup"><span data-stu-id="214ad-138">This should save time, and minimize the number of new types that you need to create in order to work with delegates.</span></span>

<span data-ttu-id="214ad-139">No próximo artigo, você verá vários padrões comuns para trabalhar com delegados na prática.</span><span class="sxs-lookup"><span data-stu-id="214ad-139">In the next article, you'll see several common patterns for working with delegates in practice.</span></span>

[<span data-ttu-id="214ad-140">Avançar</span><span class="sxs-lookup"><span data-stu-id="214ad-140">Next</span></span>](delegates-patterns.md)

