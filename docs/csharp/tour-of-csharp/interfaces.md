---
title: Interfaces em C# - um tour pela linguagem C#
description: As interfaces definem os contratos implementados pelos tipos no C#
keywords: ".NET, csharp, interfaces, herança múltipla, polimorfismo"
author: BillWagner
ms.author: wiwagn
ms.date: 08/10/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: a9bf82f4-efd1-4216-bd34-4ef0fa48c968
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 673ac56f3f5732fcda02d313b6f4273708ae365f
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---

# <a name="interfaces"></a><span data-ttu-id="74d17-104">Interfaces</span><span class="sxs-lookup"><span data-stu-id="74d17-104">Interfaces</span></span>

<span data-ttu-id="74d17-105">Uma ***interface*** define um contrato que pode ser implementado por classes e estruturas.</span><span class="sxs-lookup"><span data-stu-id="74d17-105">An ***interface*** defines a contract that can be implemented by classes and structs.</span></span> <span data-ttu-id="74d17-106">Uma interface pode conter métodos, propriedades, eventos e indexadores.</span><span class="sxs-lookup"><span data-stu-id="74d17-106">An interface can contain methods, properties, events, and indexers.</span></span> <span data-ttu-id="74d17-107">Uma interface não fornece implementações dos membros que define — ela simplesmente especifica os membros que devem ser fornecidos por classes ou estruturas que implementam a interface.</span><span class="sxs-lookup"><span data-stu-id="74d17-107">An interface does not provide implementations of the members it defines—it merely specifies the members that must be supplied by classes or structs that implement the interface.</span></span>

<span data-ttu-id="74d17-108">As interfaces podem empregar a ***herança múltipla***.</span><span class="sxs-lookup"><span data-stu-id="74d17-108">Interfaces may employ ***multiple inheritance***.</span></span> <span data-ttu-id="74d17-109">No exemplo a seguir, a interface `IComboBox` herda de `ITextBox` e `IListBox`.</span><span class="sxs-lookup"><span data-stu-id="74d17-109">In the following example, the interface `IComboBox` inherits from both `ITextBox` and `IListBox`.</span></span>

<span data-ttu-id="74d17-110">[!code-csharp[InterfacesOne](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L5-L17)]</span><span class="sxs-lookup"><span data-stu-id="74d17-110">[!code-csharp[InterfacesOne](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L5-L17)]</span></span>

<span data-ttu-id="74d17-111">Classes e structs podem implementar várias interfaces.</span><span class="sxs-lookup"><span data-stu-id="74d17-111">Classes and structs can implement multiple interfaces.</span></span> <span data-ttu-id="74d17-112">No exemplo a seguir, a classe `EditBox` implementa `IControl` e `IDataBound`.</span><span class="sxs-lookup"><span data-stu-id="74d17-112">In the following example, the class `EditBox` implements both `IControl` and `IDataBound`.</span></span>

<span data-ttu-id="74d17-113">[!code-csharp[InterfacesTwo](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L19-L27)]</span><span class="sxs-lookup"><span data-stu-id="74d17-113">[!code-csharp[InterfacesTwo](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L19-L27)]</span></span>

<span data-ttu-id="74d17-114">Quando uma classe ou struct implementa uma interface específica, as instâncias dessa classe ou struct podem ser convertidas implicitamente para esse tipo de interface.</span><span class="sxs-lookup"><span data-stu-id="74d17-114">When a class or struct implements a particular interface, instances of that class or struct can be implicitly converted to that interface type.</span></span> <span data-ttu-id="74d17-115">Por exemplo</span><span class="sxs-lookup"><span data-stu-id="74d17-115">For example</span></span>

<span data-ttu-id="74d17-116">[!code-csharp[InterfacesThree](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L33-L35)]</span><span class="sxs-lookup"><span data-stu-id="74d17-116">[!code-csharp[InterfacesThree](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L33-L35)]</span></span>

<span data-ttu-id="74d17-117">Em casos nos quais uma instância não é conhecida por ser estática para implementar uma interface específica, é possível usar conversões de tipo dinâmico.</span><span class="sxs-lookup"><span data-stu-id="74d17-117">In cases where an instance is not statically known to implement a particular interface, dynamic type casts can be used.</span></span> <span data-ttu-id="74d17-118">Por exemplo, as instruções a seguir usam conversões de tipo dinâmico para obter as implementações de interface de `IControl` e `IDataBound` do objeto.</span><span class="sxs-lookup"><span data-stu-id="74d17-118">For example, the following statements use dynamic type casts to obtain an object’s `IControl` and `IDataBound` interface implementations.</span></span> <span data-ttu-id="74d17-119">Como o tipo de tempo de execução real do objeto é `EditBox`, as conversões são bem-sucedidas.</span><span class="sxs-lookup"><span data-stu-id="74d17-119">Because the run-time actual type of the object is `EditBox`, the casts succeed.</span></span>

<span data-ttu-id="74d17-120">[!code-csharp[InterfacesFour](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L40-L42)]</span><span class="sxs-lookup"><span data-stu-id="74d17-120">[!code-csharp[InterfacesFour](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L40-L42)]</span></span>

<span data-ttu-id="74d17-121">Na classe `EditBox` anterior, o método `Paint` da interface `IControl` e o método `Bind` da interface `IDataBound` são implementados usando membros públicos.</span><span class="sxs-lookup"><span data-stu-id="74d17-121">In the previous `EditBox` class, the `Paint` method from the `IControl` interface and the `Bind` method from the `IDataBound` interface are implemented using public members.</span></span> <span data-ttu-id="74d17-122">C# também oferece suporte explícito a ***implementações de membros de interface***, permitindo que a classe ou struct evite tornar os membros públicos.</span><span class="sxs-lookup"><span data-stu-id="74d17-122">C# also supports explicit ***interface member implementations***, enabling the class or struct to avoid making the members public.</span></span> <span data-ttu-id="74d17-123">Uma implementação de membro de interface explícita é escrita usando o nome do membro de interface totalmente qualificado.</span><span class="sxs-lookup"><span data-stu-id="74d17-123">An explicit interface member implementation is written using the fully qualified interface member name.</span></span> <span data-ttu-id="74d17-124">Por exemplo, a classe `EditBox` pode implementar os métodos `IControl.Paint` e `IDataBound.Bind` usando implementações de membros de interface explícita da seguinte maneira.</span><span class="sxs-lookup"><span data-stu-id="74d17-124">For example, the `EditBox` class could implement the `IControl.Paint` and `IDataBound.Bind` methods using explicit interface member implementations as follows.</span></span>

<span data-ttu-id="74d17-125">[!code-csharp[InterfacesFive](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L60-L64)]</span><span class="sxs-lookup"><span data-stu-id="74d17-125">[!code-csharp[InterfacesFive](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L60-L64)]</span></span>

<span data-ttu-id="74d17-126">Os membros de interface explícita só podem ser acessados por meio do tipo de interface.</span><span class="sxs-lookup"><span data-stu-id="74d17-126">Explicit interface members can only be accessed via the interface type.</span></span> <span data-ttu-id="74d17-127">Por exemplo, a implementação de `IControl.Paint` fornecida pela classe EditBox anterior só pode ser chamada convertendo primeiro a referência `EditBox` ao tipo de interface `IControl`.</span><span class="sxs-lookup"><span data-stu-id="74d17-127">For example, the implementation of `IControl.Paint` provided by the previous EditBox class can only be invoked by first converting the `EditBox` reference to the `IControl` interface type.</span></span>

<span data-ttu-id="74d17-128">[!code-csharp[InterfacesFive](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L71-L74)]</span><span class="sxs-lookup"><span data-stu-id="74d17-128">[!code-csharp[InterfacesFive](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L71-L74)]</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="74d17-129">[Anterior](arrays.md)
[Próximo](enums.md)</span><span class="sxs-lookup"><span data-stu-id="74d17-129">[Previous](arrays.md)
[Next](enums.md)</span></span>

