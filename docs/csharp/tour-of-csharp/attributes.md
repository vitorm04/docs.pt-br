---
title: Atributos em C# - um tour pela linguagem C#
description: Saiba mais sobre a programação declarativa usando atributos no C#
keywords: .NET, csharp
author: BillWagner
ms.author: wiwagn
ms.date: 08/10/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 753bcfe2-7ddd-4487-9513-ba70937fc8e9
ms.openlocfilehash: 6878a408ef892ee47a03bfa04f736b9bf9671696
ms.sourcegitcommit: bbde43da655ae7bea1977f7af7345eb87bd7fd5f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/21/2017
---
# <a name="attributes"></a><span data-ttu-id="00372-104">Atributos</span><span class="sxs-lookup"><span data-stu-id="00372-104">Attributes</span></span>

<span data-ttu-id="00372-105">Tipos, membros e outras entidades em um programa C# dão suporte a modificadores que controlam determinados aspectos de seu comportamento.</span><span class="sxs-lookup"><span data-stu-id="00372-105">Types, members, and other entities in a C# program support modifiers that control certain aspects of their behavior.</span></span> <span data-ttu-id="00372-106">Por exemplo, a acessibilidade de um método é controlada usando os modificadores `public`, `protected`, `internal` e `private`.</span><span class="sxs-lookup"><span data-stu-id="00372-106">For example, the accessibility of a method is controlled using the `public`, `protected`, `internal`, and `private` modifiers.</span></span> <span data-ttu-id="00372-107">O C# generaliza essa funcionalidade, de modo que os tipos definidos pelo usuário de informações declarativas podem ser anexados a entidades de programa e recuperados no tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="00372-107">C# generalizes this capability such that user-defined types of declarative information can be attached to program entities and retrieved at run-time.</span></span> <span data-ttu-id="00372-108">Os programas especificam essas informações declarativas adicionais, definindo e usando os ***atributos***.</span><span class="sxs-lookup"><span data-stu-id="00372-108">Programs specify this additional declarative information by defining and using ***attributes***.</span></span>

<span data-ttu-id="00372-109">O exemplo a seguir declara um atributo `HelpAttribute` que pode ser colocado em entidades de programa para fornecem links para a documentação associada.</span><span class="sxs-lookup"><span data-stu-id="00372-109">The following example declares a `HelpAttribute` attribute that can be placed on program entities to provide links to their associated documentation.</span></span>

[!code-csharp[AttributeDefined](../../../samples/snippets/csharp/tour/attributes/Program.cs#L3-L20)]

<span data-ttu-id="00372-110">Todas as classes de atributo derivam da classe base <xref:System.Attribute> fornecida pela biblioteca padrão.</span><span class="sxs-lookup"><span data-stu-id="00372-110">All attribute classes derive from the <xref:System.Attribute> base class provided by the standard library.</span></span> <span data-ttu-id="00372-111">Os atributos podem ser aplicados, fornecendo seu nome, junto com quaisquer argumentos, dentro dos colchetes pouco antes da declaração associada.</span><span class="sxs-lookup"><span data-stu-id="00372-111">Attributes can be applied by giving their name, along with any arguments, inside square brackets just before the associated declaration.</span></span> <span data-ttu-id="00372-112">Se o nome de um atributo termina em `Attribute`, essa parte do nome pode ser omitida quando o atributo é referenciado.</span><span class="sxs-lookup"><span data-stu-id="00372-112">If an attribute’s name ends in `Attribute`, that part of the name can be omitted when the attribute is referenced.</span></span> <span data-ttu-id="00372-113">Por exemplo, o atributo `HelpAttribute` pode ser usado da seguinte maneira.</span><span class="sxs-lookup"><span data-stu-id="00372-113">For example, the `HelpAttribute` attribute can be used as follows.</span></span>

[!code-csharp[AttributeApplied](../../../samples/snippets/csharp/tour/attributes/Program.cs#L22-L28)]

<span data-ttu-id="00372-114">Este exemplo anexa um `HelpAttribute` à classe `Widget`.</span><span class="sxs-lookup"><span data-stu-id="00372-114">This example attaches a `HelpAttribute` to the `Widget` class.</span></span> <span data-ttu-id="00372-115">Ele adiciona outro `HelpAttribute` ao método `Display` na classe.</span><span class="sxs-lookup"><span data-stu-id="00372-115">It adds another `HelpAttribute` to the `Display` method in the class.</span></span> <span data-ttu-id="00372-116">Os construtores públicos de uma classe de atributo controlam as informações que devem ser fornecidas quando o atributo é anexado a uma entidade de programa.</span><span class="sxs-lookup"><span data-stu-id="00372-116">The public constructors of an attribute class control the information that must be provided when the attribute is attached to a program entity.</span></span> <span data-ttu-id="00372-117">As informações adicionais podem ser fornecidas ao referenciar propriedades públicas de leitura-gravação da classe de atributo (como a referência anterior à propriedade `Topic`).</span><span class="sxs-lookup"><span data-stu-id="00372-117">Additional information can be provided by referencing public read-write properties of the attribute class (such as the reference to the `Topic` property previously).</span></span>

<span data-ttu-id="00372-118">Quando um atributo específico for solicitado por meio de reflexão, o construtor para a classe de atributo será invocado com as informações fornecidas na origem do programa e a instância do atributo resultante será retornada.</span><span class="sxs-lookup"><span data-stu-id="00372-118">When a particular attribute is requested through reflection, the constructor for the attribute class is invoked with the information provided in the program source, and the resulting attribute instance is returned.</span></span> <span data-ttu-id="00372-119">Se forem fornecidas informações adicionais por meio de propriedades, essas propriedades serão definidas para os valores fornecidos antes que a instância do atributo seja retornada.</span><span class="sxs-lookup"><span data-stu-id="00372-119">If additional information was provided through properties, those properties are set to the given values before the attribute instance is returned.</span></span>

>[!div class="step-by-step"]
[<span data-ttu-id="00372-120">Anterior</span><span class="sxs-lookup"><span data-stu-id="00372-120">Previous</span></span>](delegates.md)
