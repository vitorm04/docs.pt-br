---
description: ':::no-loc text=interface::: (Referência C#)'
title: interface – Referência de C#
ms.date: 01/17/2020
f1_keywords:
- interface_CSharpKeyword
helpviewer_keywords:
- interface keyword [C#]
ms.assetid: 7da38e81-4f99-4bc5-b07d-c986b687eeba
ms.openlocfilehash: 24f95e828522f467c519c0c8a7ba9410aa97af4e
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89134582"
---
# <a name="no-loc-textinterface-c-reference"></a><span data-ttu-id="216e7-103">:::no-loc text="interface"::: (Referência C#)</span><span class="sxs-lookup"><span data-stu-id="216e7-103">:::no-loc text="interface"::: (C# Reference)</span></span>

<span data-ttu-id="216e7-104">Uma interface define um contrato.</span><span class="sxs-lookup"><span data-stu-id="216e7-104">An interface defines a contract.</span></span> <span data-ttu-id="216e7-105">Qualquer um [`class`](class.md) ou [`struct`](../builtin-types/struct.md) que implemente esse contrato deve fornecer uma implementação dos membros definidos na interface.</span><span class="sxs-lookup"><span data-stu-id="216e7-105">Any [`class`](class.md) or [`struct`](../builtin-types/struct.md) that implements that contract must provide an implementation of the members defined in the interface.</span></span> <span data-ttu-id="216e7-106">A partir do C# 8,0, uma interface pode definir uma implementação padrão para membros.</span><span class="sxs-lookup"><span data-stu-id="216e7-106">Beginning with C# 8.0, an interface may define a default implementation for members.</span></span> <span data-ttu-id="216e7-107">Ele também pode definir [`static`](static.md) Membros para fornecer uma única implementação para a funcionalidade comum.</span><span class="sxs-lookup"><span data-stu-id="216e7-107">It may also define [`static`](static.md) members in order to provide a single implementation for common functionality.</span></span>

<span data-ttu-id="216e7-108">No exemplo a seguir, a classe `ImplementationClass` deve implementar um método chamado `SampleMethod` que não tem parâmetros e retorna `void`.</span><span class="sxs-lookup"><span data-stu-id="216e7-108">In the following example, class `ImplementationClass` must implement a method named `SampleMethod` that has no parameters and returns `void`.</span></span>

<span data-ttu-id="216e7-109">Para obter mais informações e exemplos, consulte [Interfaces](../../programming-guide/interfaces/index.md).</span><span class="sxs-lookup"><span data-stu-id="216e7-109">For more information and examples, see [Interfaces](../../programming-guide/interfaces/index.md).</span></span>

## <a name="example"></a><span data-ttu-id="216e7-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="216e7-110">Example</span></span>

[!code-csharp[csrefKeywordsTypes#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#14)]

<span data-ttu-id="216e7-111">Uma interface pode ser membro de um namespace ou de uma classe.</span><span class="sxs-lookup"><span data-stu-id="216e7-111">An interface can be a member of a namespace or a class.</span></span> <span data-ttu-id="216e7-112">Uma declaração de interface pode conter declarações (assinaturas sem qualquer implementação) dos seguintes membros:</span><span class="sxs-lookup"><span data-stu-id="216e7-112">An interface declaration can contain declarations (signatures without any implementation) of the following members:</span></span>

- [<span data-ttu-id="216e7-113">Métodos</span><span class="sxs-lookup"><span data-stu-id="216e7-113">Methods</span></span>](../../programming-guide/classes-and-structs/methods.md)
- [<span data-ttu-id="216e7-114">Propriedades</span><span class="sxs-lookup"><span data-stu-id="216e7-114">Properties</span></span>](../../programming-guide/classes-and-structs/using-properties.md)
- [<span data-ttu-id="216e7-115">Indexadores</span><span class="sxs-lookup"><span data-stu-id="216e7-115">Indexers</span></span>](../../programming-guide/indexers/using-indexers.md)
- [<span data-ttu-id="216e7-116">Eventos</span><span class="sxs-lookup"><span data-stu-id="216e7-116">Events</span></span>](event.md)

<span data-ttu-id="216e7-117">Essas declarações de membro anteriores normalmente não contêm um corpo.</span><span class="sxs-lookup"><span data-stu-id="216e7-117">These preceding member declarations typically do not contain a body.</span></span> <span data-ttu-id="216e7-118">A partir do C# 8,0, um membro de interface pode declarar um corpo.</span><span class="sxs-lookup"><span data-stu-id="216e7-118">Beginning with C# 8.0, an interface member may declare a body.</span></span> <span data-ttu-id="216e7-119">Isso é chamado de *implementação padrão*.</span><span class="sxs-lookup"><span data-stu-id="216e7-119">This is called a *default implementation*.</span></span> <span data-ttu-id="216e7-120">Os membros com corpos permitem que a interface forneça uma implementação "padrão" para classes e estruturas que não fornecem uma implementação de substituição.</span><span class="sxs-lookup"><span data-stu-id="216e7-120">Members with bodies permit the interface to provide a "default" implementation for classes and structs that don't provide an overriding implementation.</span></span> <span data-ttu-id="216e7-121">Além disso, a partir do C# 8,0, uma interface pode incluir:</span><span class="sxs-lookup"><span data-stu-id="216e7-121">In addition, beginning with C# 8.0, an interface may include:</span></span>

- [<span data-ttu-id="216e7-122">Constantes</span><span class="sxs-lookup"><span data-stu-id="216e7-122">Constants</span></span>](const.md)
- [<span data-ttu-id="216e7-123">Operadores</span><span class="sxs-lookup"><span data-stu-id="216e7-123">Operators</span></span>](../operators/operator-overloading.md)
- <span data-ttu-id="216e7-124">[Construtor estático](../../programming-guide/classes-and-structs/constructors.md#static-constructors).</span><span class="sxs-lookup"><span data-stu-id="216e7-124">[Static constructor](../../programming-guide/classes-and-structs/constructors.md#static-constructors).</span></span>
- [<span data-ttu-id="216e7-125">Tipos aninhados</span><span class="sxs-lookup"><span data-stu-id="216e7-125">Nested types</span></span>](../../programming-guide/classes-and-structs/nested-types.md)
- [<span data-ttu-id="216e7-126">Campos, métodos, propriedades, indexadores e eventos estáticos</span><span class="sxs-lookup"><span data-stu-id="216e7-126">Static fields, methods, properties, indexers, and events</span></span>](static.md)
- <span data-ttu-id="216e7-127">Declarações de membro usando a sintaxe de implementação de interface explícita.</span><span class="sxs-lookup"><span data-stu-id="216e7-127">Member declarations using the explicit interface implementation syntax.</span></span>
- <span data-ttu-id="216e7-128">Modificadores de acesso explícitos (o acesso padrão é [`public`](access-modifiers.md) ).</span><span class="sxs-lookup"><span data-stu-id="216e7-128">Explicit access modifiers (the default access is [`public`](access-modifiers.md)).</span></span>

<span data-ttu-id="216e7-129">As interfaces não podem conter o estado da instância.</span><span class="sxs-lookup"><span data-stu-id="216e7-129">Interfaces may not contain instance state.</span></span> <span data-ttu-id="216e7-130">Embora os campos estáticos agora sejam permitidos, os campos de instância não são permitidos em interfaces.</span><span class="sxs-lookup"><span data-stu-id="216e7-130">While static fields are now permitted, instance fields are not permitted in interfaces.</span></span> <span data-ttu-id="216e7-131">Não há suporte para [Propriedades automáticas de instância](../../programming-guide/classes-and-structs/auto-implemented-properties.md) em interfaces, pois elas declarariam implicitamente um campo oculto.</span><span class="sxs-lookup"><span data-stu-id="216e7-131">[Instance auto-properties](../../programming-guide/classes-and-structs/auto-implemented-properties.md) are not supported in interfaces, as they would implicitly declare a hidden field.</span></span> <span data-ttu-id="216e7-132">Essa regra tem um efeito sutil nas declarações de propriedade.</span><span class="sxs-lookup"><span data-stu-id="216e7-132">This rule has a subtle effect on property declarations.</span></span> <span data-ttu-id="216e7-133">Em uma declaração de interface, o código a seguir não declara uma propriedade implementada automaticamente como faz em um `class` ou `struct` .</span><span class="sxs-lookup"><span data-stu-id="216e7-133">In an interface declaration, the following code does not declare an auto-implemented property as it does in a `class` or `struct`.</span></span> <span data-ttu-id="216e7-134">Em vez disso, ele declara uma propriedade que não tem uma implementação padrão, mas que deve ser implementada em qualquer tipo que implemente a interface:</span><span class="sxs-lookup"><span data-stu-id="216e7-134">Instead, it declares a property that doesn't have a default implementation but must be implemented in any type that implements the interface:</span></span>

```csharp
public interface INamed
{
  public string Name {get; set;}
}
```

<span data-ttu-id="216e7-135">Uma interface pode herdar de uma ou mais interfaces base.</span><span class="sxs-lookup"><span data-stu-id="216e7-135">An interface can inherit from one or more base interfaces.</span></span> <span data-ttu-id="216e7-136">Quando uma interface [substitui um método](override.md) implementado em uma interface base, ela deve usar a sintaxe de [implementação de interface explícita](../../programming-guide/interfaces/explicit-interface-implementation.md) .</span><span class="sxs-lookup"><span data-stu-id="216e7-136">When an interface [overrides a method](override.md) implemented in a base interface, it must use the [explicit interface implementation](../../programming-guide/interfaces/explicit-interface-implementation.md) syntax.</span></span>

<span data-ttu-id="216e7-137">Quando uma lista de tipos base contém uma classe base e interfaces, a classe base deve vir em primeiro na lista.</span><span class="sxs-lookup"><span data-stu-id="216e7-137">When a base type list contains a base class and interfaces, the base class must come first in the list.</span></span>

<span data-ttu-id="216e7-138">Uma classe que implementa uma interface pode implementar membros dessa interface explicitamente.</span><span class="sxs-lookup"><span data-stu-id="216e7-138">A class that implements an interface can explicitly implement members of that interface.</span></span> <span data-ttu-id="216e7-139">Um membro implementado explicitamente não pode ser acessado por meio de uma instância da classe, mas apenas por meio de uma instância da interface.</span><span class="sxs-lookup"><span data-stu-id="216e7-139">An explicitly implemented member cannot be accessed through a class instance, but only through an instance of the interface.</span></span> <span data-ttu-id="216e7-140">Além disso, os membros de interface padrão só podem ser acessados por meio de uma instância da interface.</span><span class="sxs-lookup"><span data-stu-id="216e7-140">In addition, default interface members can only be accessed through an instance of the interface.</span></span>

<span data-ttu-id="216e7-141">Para obter mais informações sobre implementação de interface explícita, consulte [implementação de interface explícita](../../programming-guide/interfaces/explicit-interface-implementation.md).</span><span class="sxs-lookup"><span data-stu-id="216e7-141">For more information about explicit interface implementation, see [Explicit Interface Implementation](../../programming-guide/interfaces/explicit-interface-implementation.md).</span></span>

## <a name="example"></a><span data-ttu-id="216e7-142">Exemplo</span><span class="sxs-lookup"><span data-stu-id="216e7-142">Example</span></span>

<span data-ttu-id="216e7-143">O exemplo a seguir demonstra a implementação da interface.</span><span class="sxs-lookup"><span data-stu-id="216e7-143">The following example demonstrates interface implementation.</span></span> <span data-ttu-id="216e7-144">Neste exemplo, a interface contém a declaração de propriedade e a classe contém a implementação.</span><span class="sxs-lookup"><span data-stu-id="216e7-144">In this example, the interface contains the property declaration and the class contains the implementation.</span></span> <span data-ttu-id="216e7-145">Qualquer instância de uma classe que implementa `IPoint` tem propriedades de inteiro `x` e `y`.</span><span class="sxs-lookup"><span data-stu-id="216e7-145">Any instance of a class that implements `IPoint` has integer properties `x` and `y`.</span></span>

[!code-csharp[csrefKeywordsTypes#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#15)]

## <a name="c-language-specification"></a><span data-ttu-id="216e7-146">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="216e7-146">C# language specification</span></span>

<span data-ttu-id="216e7-147">Para obter mais informações, consulte a seção [interfaces](~/_csharplang/spec/interfaces.md) da [especificação da linguagem C#](~/_csharplang/spec/introduction.md) e a especificação de recurso para [membros de interface padrão-C# 8,0](~/_csharplang/proposals/csharp-8.0/default-interface-methods.md)</span><span class="sxs-lookup"><span data-stu-id="216e7-147">For more information, see the [Interfaces](~/_csharplang/spec/interfaces.md) section of the [C# language specification](~/_csharplang/spec/introduction.md) and the feature specification for [Default interface members - C# 8.0](~/_csharplang/proposals/csharp-8.0/default-interface-methods.md)</span></span>

## <a name="see-also"></a><span data-ttu-id="216e7-148">Confira também</span><span class="sxs-lookup"><span data-stu-id="216e7-148">See also</span></span>

- [<span data-ttu-id="216e7-149">Referência do C#</span><span class="sxs-lookup"><span data-stu-id="216e7-149">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="216e7-150">Guia de programação C#</span><span class="sxs-lookup"><span data-stu-id="216e7-150">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="216e7-151">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="216e7-151">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="216e7-152">Tipos de referência</span><span class="sxs-lookup"><span data-stu-id="216e7-152">Reference Types</span></span>](reference-types.md)
- [<span data-ttu-id="216e7-153">Interfaces</span><span class="sxs-lookup"><span data-stu-id="216e7-153">Interfaces</span></span>](../../programming-guide/interfaces/index.md)
- [<span data-ttu-id="216e7-154">Usando propriedades</span><span class="sxs-lookup"><span data-stu-id="216e7-154">Using Properties</span></span>](../../programming-guide/classes-and-structs/using-properties.md)
- [<span data-ttu-id="216e7-155">Usando indexadores</span><span class="sxs-lookup"><span data-stu-id="216e7-155">Using Indexers</span></span>](../../programming-guide/indexers/using-indexers.md)
