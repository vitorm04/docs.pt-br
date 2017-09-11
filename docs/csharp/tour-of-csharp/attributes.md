---
title: Atributos em C# - um tour pela linguagem C#
description: "Saiba mais sobre a programação declarativa usando atributos no C#"
keywords: .NET, csharp
author: BillWagner
ms.author: wiwagn
ms.date: 08/10/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 753bcfe2-7ddd-4487-9513-ba70937fc8e9
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 5f290b2cb7074d0b442d5971e5e08a0f6cac55ac
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---

# <a name="attributes"></a><span data-ttu-id="6c8ae-104">Atributos</span><span class="sxs-lookup"><span data-stu-id="6c8ae-104">Attributes</span></span>

<span data-ttu-id="6c8ae-105">Tipos, membros e outras entidades em um programa C# dão suporte a modificadores que controlam determinados aspectos de seu comportamento.</span><span class="sxs-lookup"><span data-stu-id="6c8ae-105">Types, members, and other entities in a C# program support modifiers that control certain aspects of their behavior.</span></span> <span data-ttu-id="6c8ae-106">Por exemplo, a acessibilidade de um método é controlada usando os modificadores `public`, `protected`, `internal` e `private`.</span><span class="sxs-lookup"><span data-stu-id="6c8ae-106">For example, the accessibility of a method is controlled using the `public`, `protected`, `internal`, and `private` modifiers.</span></span> <span data-ttu-id="6c8ae-107">O C# generaliza essa funcionalidade, de modo que os tipos definidos pelo usuário de informações declarativas podem ser anexados a entidades de programa e recuperados no tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="6c8ae-107">C# generalizes this capability such that user-defined types of declarative information can be attached to program entities and retrieved at run-time.</span></span> <span data-ttu-id="6c8ae-108">Os programas especificam essas informações declarativas adicionais, definindo e usando os ***atributos***.</span><span class="sxs-lookup"><span data-stu-id="6c8ae-108">Programs specify this additional declarative information by defining and using ***attributes***.</span></span>

<span data-ttu-id="6c8ae-109">O exemplo a seguir declara um atributo `HelpAttribute` que pode ser colocado em entidades de programa para fornecem links para a documentação associada.</span><span class="sxs-lookup"><span data-stu-id="6c8ae-109">The following example declares a `HelpAttribute` attribute that can be placed on program entities to provide links to their associated documentation.</span></span>

<span data-ttu-id="6c8ae-110">[!code-csharp[AttributeDefined](../../../samples/snippets/csharp/tour/attributes/Program.cs#L3-L20)]</span><span class="sxs-lookup"><span data-stu-id="6c8ae-110">[!code-csharp[AttributeDefined](../../../samples/snippets/csharp/tour/attributes/Program.cs#L3-L20)]</span></span>

<span data-ttu-id="6c8ae-111">Todas as classes de atributo derivam da classe base @System.Attribute fornecida pela biblioteca padrão.</span><span class="sxs-lookup"><span data-stu-id="6c8ae-111">All attribute classes derive from the @System.Attribute base class provided by the standard library.</span></span> <span data-ttu-id="6c8ae-112">Os atributos podem ser aplicados, fornecendo seu nome, junto com quaisquer argumentos, dentro dos colchetes pouco antes da declaração associada.</span><span class="sxs-lookup"><span data-stu-id="6c8ae-112">Attributes can be applied by giving their name, along with any arguments, inside square brackets just before the associated declaration.</span></span> <span data-ttu-id="6c8ae-113">Se o nome de um atributo termina em `Attribute`, essa parte do nome pode ser omitida quando o atributo é referenciado.</span><span class="sxs-lookup"><span data-stu-id="6c8ae-113">If an attribute’s name ends in `Attribute`, that part of the name can be omitted when the attribute is referenced.</span></span> <span data-ttu-id="6c8ae-114">Por exemplo, o atributo `HelpAttribute` pode ser usado da seguinte maneira.</span><span class="sxs-lookup"><span data-stu-id="6c8ae-114">For example, the `HelpAttribute` attribute can be used as follows.</span></span>

<span data-ttu-id="6c8ae-115">[!code-csharp[AttributeApplied](../../../samples/snippets/csharp/tour/attributes/Program.cs#L22-L28)]</span><span class="sxs-lookup"><span data-stu-id="6c8ae-115">[!code-csharp[AttributeApplied](../../../samples/snippets/csharp/tour/attributes/Program.cs#L22-L28)]</span></span>

<span data-ttu-id="6c8ae-116">Este exemplo anexa um `HelpAttribute` à classe `Widget`.</span><span class="sxs-lookup"><span data-stu-id="6c8ae-116">This example attaches a `HelpAttribute` to the `Widget` class.</span></span> <span data-ttu-id="6c8ae-117">Ele adiciona outro `HelpAttribute` ao método `Display` na classe.</span><span class="sxs-lookup"><span data-stu-id="6c8ae-117">It adds another `HelpAttribute` to the `Display` method in the class.</span></span> <span data-ttu-id="6c8ae-118">Os construtores públicos de uma classe de atributo controlam as informações que devem ser fornecidas quando o atributo é anexado a uma entidade de programa.</span><span class="sxs-lookup"><span data-stu-id="6c8ae-118">The public constructors of an attribute class control the information that must be provided when the attribute is attached to a program entity.</span></span> <span data-ttu-id="6c8ae-119">As informações adicionais podem ser fornecidas ao referenciar propriedades públicas de leitura-gravação da classe de atributo (como a referência anterior à propriedade `Topic`).</span><span class="sxs-lookup"><span data-stu-id="6c8ae-119">Additional information can be provided by referencing public read-write properties of the attribute class (such as the reference to the `Topic` property previously).</span></span>

<span data-ttu-id="6c8ae-120">Quando um atributo específico for solicitado por meio de reflexão, o construtor para a classe de atributo será invocado com as informações fornecidas na origem do programa e a instância do atributo resultante será retornada.</span><span class="sxs-lookup"><span data-stu-id="6c8ae-120">When a particular attribute is requested through reflection, the constructor for the attribute class is invoked with the information provided in the program source, and the resulting attribute instance is returned.</span></span> <span data-ttu-id="6c8ae-121">Se forem fornecidas informações adicionais por meio de propriedades, essas propriedades serão definidas para os valores fornecidos antes que a instância do atributo seja retornada.</span><span class="sxs-lookup"><span data-stu-id="6c8ae-121">If additional information was provided through properties, those properties are set to the given values before the attribute instance is returned.</span></span>

>[!div class="step-by-step"]
[<span data-ttu-id="6c8ae-122">Anterior</span><span class="sxs-lookup"><span data-stu-id="6c8ae-122">Previous</span></span>](delegates.md)

