---
title: Interfaces em C# - um tour pela linguagem C#
description: As interfaces definem os contratos implementados pelos tipos no C#
ms.date: 08/10/2016
ms.assetid: a9bf82f4-efd1-4216-bd34-4ef0fa48c968
ms.openlocfilehash: 240ddfb321c5a89c8aada4353845915d0e242ae0
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65634550"
---
# <a name="interfaces"></a><span data-ttu-id="04076-103">Interfaces</span><span class="sxs-lookup"><span data-stu-id="04076-103">Interfaces</span></span>

<span data-ttu-id="04076-104">Uma ***interface*** define um contrato que pode ser implementado por classes e estruturas.</span><span class="sxs-lookup"><span data-stu-id="04076-104">An ***interface*** defines a contract that can be implemented by classes and structs.</span></span> <span data-ttu-id="04076-105">Uma interface pode conter métodos, propriedades, eventos e indexadores.</span><span class="sxs-lookup"><span data-stu-id="04076-105">An interface can contain methods, properties, events, and indexers.</span></span> <span data-ttu-id="04076-106">Uma interface não fornece implementações dos membros que define — ela simplesmente especifica os membros que devem ser fornecidos por classes ou estruturas que implementam a interface.</span><span class="sxs-lookup"><span data-stu-id="04076-106">An interface does not provide implementations of the members it defines—it merely specifies the members that must be supplied by classes or structs that implement the interface.</span></span>

<span data-ttu-id="04076-107">As interfaces podem empregar a ***herança múltipla***.</span><span class="sxs-lookup"><span data-stu-id="04076-107">Interfaces may employ ***multiple inheritance***.</span></span> <span data-ttu-id="04076-108">No exemplo a seguir, a interface `IComboBox` herda de `ITextBox` e `IListBox`.</span><span class="sxs-lookup"><span data-stu-id="04076-108">In the following example, the interface `IComboBox` inherits from both `ITextBox` and `IListBox`.</span></span>

[!code-csharp[InterfacesOne](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L5-L17)]

<span data-ttu-id="04076-109">Classes e structs podem implementar várias interfaces.</span><span class="sxs-lookup"><span data-stu-id="04076-109">Classes and structs can implement multiple interfaces.</span></span> <span data-ttu-id="04076-110">No exemplo a seguir, a classe `EditBox` implementa `IControl` e `IDataBound`.</span><span class="sxs-lookup"><span data-stu-id="04076-110">In the following example, the class `EditBox` implements both `IControl` and `IDataBound`.</span></span>

[!code-csharp[InterfacesTwo](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L19-L27)]

<span data-ttu-id="04076-111">Quando uma classe ou struct implementa uma interface específica, as instâncias dessa classe ou struct podem ser convertidas implicitamente para esse tipo de interface.</span><span class="sxs-lookup"><span data-stu-id="04076-111">When a class or struct implements a particular interface, instances of that class or struct can be implicitly converted to that interface type.</span></span> <span data-ttu-id="04076-112">Por exemplo</span><span class="sxs-lookup"><span data-stu-id="04076-112">For example</span></span>

[!code-csharp[InterfacesThree](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L33-L35)]

<span data-ttu-id="04076-113">Em casos nos quais uma instância não é conhecida por ser estática para implementar uma interface específica, é possível usar conversões de tipo dinâmico.</span><span class="sxs-lookup"><span data-stu-id="04076-113">In cases where an instance is not statically known to implement a particular interface, dynamic type casts can be used.</span></span> <span data-ttu-id="04076-114">Por exemplo, as instruções a seguir usam conversões de tipo dinâmico para obter as implementações de interface de `IControl` e `IDataBound` do objeto.</span><span class="sxs-lookup"><span data-stu-id="04076-114">For example, the following statements use dynamic type casts to obtain an object’s `IControl` and `IDataBound` interface implementations.</span></span> <span data-ttu-id="04076-115">Como o tipo de tempo de execução real do objeto é `EditBox`, as conversões são bem-sucedidas.</span><span class="sxs-lookup"><span data-stu-id="04076-115">Because the run-time actual type of the object is `EditBox`, the casts succeed.</span></span>

[!code-csharp[InterfacesFour](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L40-L42)]

<span data-ttu-id="04076-116">Na classe `EditBox` anterior, o método `Paint` da interface `IControl` e o método `Bind` da interface `IDataBound` são implementados usando membros públicos.</span><span class="sxs-lookup"><span data-stu-id="04076-116">In the previous `EditBox` class, the `Paint` method from the `IControl` interface and the `Bind` method from the `IDataBound` interface are implemented using public members.</span></span> <span data-ttu-id="04076-117">C# também oferece suporte explícito a ***implementações de membros de interface***, permitindo que a classe ou struct evite tornar os membros públicos.</span><span class="sxs-lookup"><span data-stu-id="04076-117">C# also supports explicit ***interface member implementations***, enabling the class or struct to avoid making the members public.</span></span> <span data-ttu-id="04076-118">Uma implementação de membro de interface explícita é escrita usando o nome do membro de interface totalmente qualificado.</span><span class="sxs-lookup"><span data-stu-id="04076-118">An explicit interface member implementation is written using the fully qualified interface member name.</span></span> <span data-ttu-id="04076-119">Por exemplo, a classe `EditBox` pode implementar os métodos `IControl.Paint` e `IDataBound.Bind` usando implementações de membros de interface explícita da seguinte maneira.</span><span class="sxs-lookup"><span data-stu-id="04076-119">For example, the `EditBox` class could implement the `IControl.Paint` and `IDataBound.Bind` methods using explicit interface member implementations as follows.</span></span>

[!code-csharp[InterfacesFive](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L60-L64)]

<span data-ttu-id="04076-120">Os membros de interface explícita só podem ser acessados por meio do tipo de interface.</span><span class="sxs-lookup"><span data-stu-id="04076-120">Explicit interface members can only be accessed via the interface type.</span></span> <span data-ttu-id="04076-121">Por exemplo, a implementação de `IControl.Paint` fornecida pela classe EditBox anterior só pode ser chamada convertendo primeiro a referência `EditBox` ao tipo de interface `IControl`.</span><span class="sxs-lookup"><span data-stu-id="04076-121">For example, the implementation of `IControl.Paint` provided by the previous EditBox class can only be invoked by first converting the `EditBox` reference to the `IControl` interface type.</span></span>

[!code-csharp[InterfacesFive](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L71-L74)]

>[!div class="step-by-step"]
><span data-ttu-id="04076-122">[Anterior](arrays.md)
>[Próximo](enums.md)</span><span class="sxs-lookup"><span data-stu-id="04076-122">[Previous](arrays.md)
[Next](enums.md)</span></span>
