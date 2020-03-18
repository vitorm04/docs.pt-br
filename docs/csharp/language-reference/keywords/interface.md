---
title: interface – Referência de C#
ms.date: 01/17/2020
f1_keywords:
- interface_CSharpKeyword
helpviewer_keywords:
- interface keyword [C#]
ms.assetid: 7da38e81-4f99-4bc5-b07d-c986b687eeba
ms.openlocfilehash: 473f5f8e226f0a144746ac943afcffdccd4777c7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77625846"
---
# <a name="no-loc-textinterface-c-reference"></a><span data-ttu-id="91805-102">:::no-loc text="interface":::(C# Referência)</span><span class="sxs-lookup"><span data-stu-id="91805-102">:::no-loc text="interface"::: (C# Reference)</span></span>

<span data-ttu-id="91805-103">Uma interface define um contrato.</span><span class="sxs-lookup"><span data-stu-id="91805-103">An interface defines a contract.</span></span> <span data-ttu-id="91805-104">Qualquer [`class`](class.md) [`struct`](../builtin-types/struct.md) ou que implemente esse contrato deve fornecer uma implementação dos membros definidos na interface.</span><span class="sxs-lookup"><span data-stu-id="91805-104">Any [`class`](class.md) or [`struct`](../builtin-types/struct.md) that implements that contract must provide an implementation of the members defined in the interface.</span></span> <span data-ttu-id="91805-105">Começando com C# 8.0, uma interface pode definir uma implementação padrão para membros.</span><span class="sxs-lookup"><span data-stu-id="91805-105">Beginning with C# 8.0, an interface may define a default implementation for members.</span></span> <span data-ttu-id="91805-106">Ele também [`static`](static.md) pode definir membros a fim de fornecer uma única implementação para funcionalidade comum.</span><span class="sxs-lookup"><span data-stu-id="91805-106">It may also define [`static`](static.md) members in order to provide a single implementation for common functionality.</span></span>

<span data-ttu-id="91805-107">No exemplo a seguir, a classe `ImplementationClass` deve implementar um método chamado `SampleMethod` que não tem parâmetros e retorna `void`.</span><span class="sxs-lookup"><span data-stu-id="91805-107">In the following example, class `ImplementationClass` must implement a method named `SampleMethod` that has no parameters and returns `void`.</span></span>

<span data-ttu-id="91805-108">Para obter mais informações e exemplos, consulte [Interfaces](../../programming-guide/interfaces/index.md).</span><span class="sxs-lookup"><span data-stu-id="91805-108">For more information and examples, see [Interfaces](../../programming-guide/interfaces/index.md).</span></span>

## <a name="example"></a><span data-ttu-id="91805-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="91805-109">Example</span></span>

[!code-csharp[csrefKeywordsTypes#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#14)]

<span data-ttu-id="91805-110">Uma interface pode ser um membro de um namespace ou de uma classe.</span><span class="sxs-lookup"><span data-stu-id="91805-110">An interface can be a member of a namespace or a class.</span></span> <span data-ttu-id="91805-111">Uma declaração de interface pode conter declarações (assinaturas sem qualquer implementação) dos seguintes membros:</span><span class="sxs-lookup"><span data-stu-id="91805-111">An interface declaration can contain declarations (signatures without any implementation) of the following members:</span></span>

- [<span data-ttu-id="91805-112">Métodos</span><span class="sxs-lookup"><span data-stu-id="91805-112">Methods</span></span>](../../programming-guide/classes-and-structs/methods.md)
- [<span data-ttu-id="91805-113">Propriedades</span><span class="sxs-lookup"><span data-stu-id="91805-113">Properties</span></span>](../../programming-guide/classes-and-structs/using-properties.md)
- [<span data-ttu-id="91805-114">Indexadores</span><span class="sxs-lookup"><span data-stu-id="91805-114">Indexers</span></span>](../../programming-guide/indexers/using-indexers.md)
- [<span data-ttu-id="91805-115">Eventos</span><span class="sxs-lookup"><span data-stu-id="91805-115">Events</span></span>](event.md)

<span data-ttu-id="91805-116">Essas declarações de membros anteriores normalmente não contêm um corpo.</span><span class="sxs-lookup"><span data-stu-id="91805-116">These preceding member declarations typically do not contain a body.</span></span> <span data-ttu-id="91805-117">Começando com C# 8.0, um membro da interface pode declarar um corpo.</span><span class="sxs-lookup"><span data-stu-id="91805-117">Beginning with C# 8.0, an interface member may declare a body.</span></span> <span data-ttu-id="91805-118">Isso é chamado de *implementação padrão*.</span><span class="sxs-lookup"><span data-stu-id="91805-118">This is called a *default implementation*.</span></span> <span data-ttu-id="91805-119">Membros com órgãos permitem que a interface forneça uma implementação "padrão" para classes e estruturas que não forneçam uma implementação predominante.</span><span class="sxs-lookup"><span data-stu-id="91805-119">Members with bodies permit the interface to provide a "default" implementation for classes and structs that don't provide an overriding implementation.</span></span> <span data-ttu-id="91805-120">Além disso, começando com C# 8.0, uma interface pode incluir:</span><span class="sxs-lookup"><span data-stu-id="91805-120">In addition, beginning with C# 8.0, an interface may include:</span></span>

- [<span data-ttu-id="91805-121">Constantes</span><span class="sxs-lookup"><span data-stu-id="91805-121">Constants</span></span>](const.md)
- [<span data-ttu-id="91805-122">Operadores</span><span class="sxs-lookup"><span data-stu-id="91805-122">Operators</span></span>](../operators/operator-overloading.md)
- <span data-ttu-id="91805-123">[Construtor estático](../../programming-guide/classes-and-structs/constructors.md#static-constructors).</span><span class="sxs-lookup"><span data-stu-id="91805-123">[Static constructor](../../programming-guide/classes-and-structs/constructors.md#static-constructors).</span></span>
- [<span data-ttu-id="91805-124">Tipos aninhados</span><span class="sxs-lookup"><span data-stu-id="91805-124">Nested types</span></span>](../../programming-guide/classes-and-structs/nested-types.md)
- [<span data-ttu-id="91805-125">Campos estáticos, métodos, propriedades, indexadores e eventos</span><span class="sxs-lookup"><span data-stu-id="91805-125">Static fields, methods, properties, indexers, and events</span></span>](static.md)
- <span data-ttu-id="91805-126">Declarações de membros usando a sintaxe de implementação de interface explícita.</span><span class="sxs-lookup"><span data-stu-id="91805-126">Member declarations using the explicit interface implementation syntax.</span></span>
- <span data-ttu-id="91805-127">Modificadores de acesso explícito (o acesso padrão é [`public`](access-modifiers.md)).</span><span class="sxs-lookup"><span data-stu-id="91805-127">Explicit access modifiers (the default access is [`public`](access-modifiers.md)).</span></span>

<span data-ttu-id="91805-128">As interfaces podem não conter o estado de ocorrência.</span><span class="sxs-lookup"><span data-stu-id="91805-128">Interfaces may not contain instance state.</span></span> <span data-ttu-id="91805-129">Embora os campos estáticos sejam agora permitidos, os campos de instância não são permitidos em interfaces.</span><span class="sxs-lookup"><span data-stu-id="91805-129">While static fields are now permitted, instance fields are not permitted in interfaces.</span></span> <span data-ttu-id="91805-130">[As propriedades automáticas de instância](../../programming-guide/classes-and-structs/auto-implemented-properties.md) não são suportadas em interfaces, pois declarariam implicitamente um campo oculto.</span><span class="sxs-lookup"><span data-stu-id="91805-130">[Instance auto-properties](../../programming-guide/classes-and-structs/auto-implemented-properties.md) are not supported in interfaces, as they would implicitly declare a hidden field.</span></span> <span data-ttu-id="91805-131">Esta regra tem um efeito sutil sobre as declarações de propriedade.</span><span class="sxs-lookup"><span data-stu-id="91805-131">This rule has a subtle effect on property declarations.</span></span> <span data-ttu-id="91805-132">Em uma declaração de interface, o código a seguir não `class` `struct`declara uma propriedade auto-implementada como faz em um ou .</span><span class="sxs-lookup"><span data-stu-id="91805-132">In an interface declaration, the following code does not declare an auto-implemented property as it does in a `class` or `struct`.</span></span> <span data-ttu-id="91805-133">Em vez disso, declara uma propriedade que não tem uma implementação padrão, mas deve ser implementada em qualquer tipo que implemente a interface:</span><span class="sxs-lookup"><span data-stu-id="91805-133">Instead, it declares a property that doesn't have a default implementation but must be implemented in any type that implements the interface:</span></span>

```csharp
public interface INamed
{
  public string Name {get; set;}
}
```

<span data-ttu-id="91805-134">Uma interface pode herdar de uma ou mais interfaces base.</span><span class="sxs-lookup"><span data-stu-id="91805-134">An interface can inherit from one or more base interfaces.</span></span> <span data-ttu-id="91805-135">Quando uma interface [substitui um método](override.md) implementado em uma interface base, ele deve usar a sintaxe de [implementação de interface explícita.](../../programming-guide/interfaces/explicit-interface-implementation.md)</span><span class="sxs-lookup"><span data-stu-id="91805-135">When an interface [overrides a method](override.md) implemented in a base interface, it must use the [explicit interface implementation](../../programming-guide/interfaces/explicit-interface-implementation.md) syntax.</span></span>

<span data-ttu-id="91805-136">Quando uma lista de tipos base contém uma classe base e interfaces, a classe base deve vir em primeiro na lista.</span><span class="sxs-lookup"><span data-stu-id="91805-136">When a base type list contains a base class and interfaces, the base class must come first in the list.</span></span>

<span data-ttu-id="91805-137">Uma classe que implementa uma interface pode implementar membros dessa interface explicitamente.</span><span class="sxs-lookup"><span data-stu-id="91805-137">A class that implements an interface can explicitly implement members of that interface.</span></span> <span data-ttu-id="91805-138">Um membro implementado explicitamente não pode ser acessado por meio de uma instância da classe, mas apenas por meio de uma instância da interface.</span><span class="sxs-lookup"><span data-stu-id="91805-138">An explicitly implemented member cannot be accessed through a class instance, but only through an instance of the interface.</span></span> <span data-ttu-id="91805-139">Além disso, os membros de interface padrão só podem ser acessados através de uma instância da interface.</span><span class="sxs-lookup"><span data-stu-id="91805-139">In addition, default interface members can only be accessed through an instance of the interface.</span></span>

<span data-ttu-id="91805-140">Para obter mais informações sobre a implementação explícita da interface, consulte [Implementação de interface explícita](../../programming-guide/interfaces/explicit-interface-implementation.md).</span><span class="sxs-lookup"><span data-stu-id="91805-140">For more information about explicit interface implementation, see [Explicit Interface Implementation](../../programming-guide/interfaces/explicit-interface-implementation.md).</span></span>

## <a name="example"></a><span data-ttu-id="91805-141">Exemplo</span><span class="sxs-lookup"><span data-stu-id="91805-141">Example</span></span>

<span data-ttu-id="91805-142">O exemplo a seguir demonstra a implementação da interface.</span><span class="sxs-lookup"><span data-stu-id="91805-142">The following example demonstrates interface implementation.</span></span> <span data-ttu-id="91805-143">Neste exemplo, a interface contém a declaração de propriedade e a classe contém a implementação.</span><span class="sxs-lookup"><span data-stu-id="91805-143">In this example, the interface contains the property declaration and the class contains the implementation.</span></span> <span data-ttu-id="91805-144">Qualquer instância de uma classe que implementa `IPoint` tem propriedades de inteiro `x` e `y`.</span><span class="sxs-lookup"><span data-stu-id="91805-144">Any instance of a class that implements `IPoint` has integer properties `x` and `y`.</span></span>

[!code-csharp[csrefKeywordsTypes#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#15)]

## <a name="c-language-specification"></a><span data-ttu-id="91805-145">especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="91805-145">C# language specification</span></span>

<span data-ttu-id="91805-146">Para obter mais informações, consulte a seção [Interfaces](~/_csharplang/spec/interfaces.md) da especificação do [idioma C#](~/_csharplang/spec/introduction.md) e a especificação do recurso para [membros de interface Padrão - C# 8.0](~/_csharplang/proposals/csharp-8.0/default-interface-methods.md)</span><span class="sxs-lookup"><span data-stu-id="91805-146">For more information, see the [Interfaces](~/_csharplang/spec/interfaces.md) section of the [C# language specification](~/_csharplang/spec/introduction.md) and the feature specification for [Default interface members - C# 8.0](~/_csharplang/proposals/csharp-8.0/default-interface-methods.md)</span></span>

## <a name="see-also"></a><span data-ttu-id="91805-147">Confira também</span><span class="sxs-lookup"><span data-stu-id="91805-147">See also</span></span>

- [<span data-ttu-id="91805-148">C# Referência</span><span class="sxs-lookup"><span data-stu-id="91805-148">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="91805-149">C# Guia de Programação</span><span class="sxs-lookup"><span data-stu-id="91805-149">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="91805-150">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="91805-150">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="91805-151">Tipos de referência</span><span class="sxs-lookup"><span data-stu-id="91805-151">Reference Types</span></span>](reference-types.md)
- [<span data-ttu-id="91805-152">Interfaces</span><span class="sxs-lookup"><span data-stu-id="91805-152">Interfaces</span></span>](../../programming-guide/interfaces/index.md)
- [<span data-ttu-id="91805-153">Usando propriedades</span><span class="sxs-lookup"><span data-stu-id="91805-153">Using Properties</span></span>](../../programming-guide/classes-and-structs/using-properties.md)
- [<span data-ttu-id="91805-154">Usando indexadores</span><span class="sxs-lookup"><span data-stu-id="91805-154">Using Indexers</span></span>](../../programming-guide/indexers/using-indexers.md)
- [<span data-ttu-id="91805-155">Interfaces</span><span class="sxs-lookup"><span data-stu-id="91805-155">Interfaces</span></span>](../../programming-guide/interfaces/index.md)
