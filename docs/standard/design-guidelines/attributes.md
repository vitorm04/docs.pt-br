---
title: Atributos
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- attributes [.NET Framework], about
- class library design guidelines [.NET Framework], attributes
ms.assetid: ee0038ef-b247-4747-a650-3c5c5cd58d8b
ms.openlocfilehash: 3c0e1b8c20042c085d4ace996a084cbd464d3b21
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617555"
---
# <a name="attributes"></a><span data-ttu-id="58557-102">Atributos</span><span class="sxs-lookup"><span data-stu-id="58557-102">Attributes</span></span>
<span data-ttu-id="58557-103"><xref:System.Attribute?displayProperty=nameWithType>é uma classe base usada para definir atributos personalizados.</span><span class="sxs-lookup"><span data-stu-id="58557-103"><xref:System.Attribute?displayProperty=nameWithType> is a base class used to define custom attributes.</span></span>

 <span data-ttu-id="58557-104">Atributos são anotações que podem ser adicionadas a elementos de programação, como assemblies, tipos, membros e parâmetros.</span><span class="sxs-lookup"><span data-stu-id="58557-104">Attributes are annotations that can be added to programming elements such as assemblies, types, members, and parameters.</span></span> <span data-ttu-id="58557-105">Eles são armazenados nos metadados do assembly e podem ser acessados em tempo de execução usando as APIs de reflexão.</span><span class="sxs-lookup"><span data-stu-id="58557-105">They are stored in the metadata of the assembly and can be accessed at runtime using the reflection APIs.</span></span> <span data-ttu-id="58557-106">Por exemplo, a estrutura define o <xref:System.ObsoleteAttribute> , que pode ser aplicado a um tipo ou um membro para indicar que o tipo ou o membro foi preterido.</span><span class="sxs-lookup"><span data-stu-id="58557-106">For example, the Framework defines the <xref:System.ObsoleteAttribute>, which can be applied to a type or a member to indicate that the type or member has been deprecated.</span></span>

 <span data-ttu-id="58557-107">Os atributos podem ter uma ou mais propriedades que contêm dados adicionais relacionados ao atributo.</span><span class="sxs-lookup"><span data-stu-id="58557-107">Attributes can have one or more properties that carry additional data related to the attribute.</span></span> <span data-ttu-id="58557-108">Por exemplo, `ObsoleteAttribute` o pode conter informações adicionais sobre a versão na qual um tipo ou um membro foi preterido e a descrição das novas APIs que substituem a API obsoleta.</span><span class="sxs-lookup"><span data-stu-id="58557-108">For example, `ObsoleteAttribute` could carry additional information about the release in which a type or a member got deprecated and the description of the new APIs replacing the obsolete API.</span></span>

 <span data-ttu-id="58557-109">Algumas propriedades de um atributo devem ser especificadas quando o atributo é aplicado.</span><span class="sxs-lookup"><span data-stu-id="58557-109">Some properties of an attribute must be specified when the attribute is applied.</span></span> <span data-ttu-id="58557-110">Eles são chamados de propriedades obrigatórias ou argumentos necessários, pois são representados como parâmetros de Construtor posicionais.</span><span class="sxs-lookup"><span data-stu-id="58557-110">These are referred to as the required properties or required arguments, because they are represented as positional constructor parameters.</span></span> <span data-ttu-id="58557-111">Por exemplo, a <xref:System.Diagnostics.ConditionalAttribute.ConditionString%2A> propriedade de <xref:System.Diagnostics.ConditionalAttribute> é uma propriedade necessária.</span><span class="sxs-lookup"><span data-stu-id="58557-111">For example, the <xref:System.Diagnostics.ConditionalAttribute.ConditionString%2A> property of the <xref:System.Diagnostics.ConditionalAttribute> is a required property.</span></span>

 <span data-ttu-id="58557-112">As propriedades que não precisam necessariamente ser especificadas quando o atributo é aplicado são chamadas de propriedades opcionais (ou argumentos opcionais).</span><span class="sxs-lookup"><span data-stu-id="58557-112">Properties that do not necessarily have to be specified when the attribute is applied are called optional properties (or optional arguments).</span></span> <span data-ttu-id="58557-113">Elas são representadas por propriedades de tabela.</span><span class="sxs-lookup"><span data-stu-id="58557-113">They are represented by settable properties.</span></span> <span data-ttu-id="58557-114">Os compiladores fornecem uma sintaxe especial para definir essas propriedades quando um atributo é aplicado.</span><span class="sxs-lookup"><span data-stu-id="58557-114">Compilers provide special syntax to set these properties when an attribute is applied.</span></span> <span data-ttu-id="58557-115">Por exemplo, a <xref:System.AttributeUsageAttribute.Inherited%2A?displayProperty=nameWithType> propriedade representa um argumento opcional.</span><span class="sxs-lookup"><span data-stu-id="58557-115">For example, the <xref:System.AttributeUsageAttribute.Inherited%2A?displayProperty=nameWithType> property represents an optional argument.</span></span>

 <span data-ttu-id="58557-116">✔️ as classes de atributo personalizado de nome com o sufixo "Attribute".</span><span class="sxs-lookup"><span data-stu-id="58557-116">✔️ DO name custom attribute classes with the suffix "Attribute."</span></span>

 <span data-ttu-id="58557-117">✔️ aplicar o <xref:System.AttributeUsageAttribute> aos atributos personalizados.</span><span class="sxs-lookup"><span data-stu-id="58557-117">✔️ DO apply the <xref:System.AttributeUsageAttribute> to custom attributes.</span></span>

 <span data-ttu-id="58557-118">✔️ fornece propriedades configurável para argumentos opcionais.</span><span class="sxs-lookup"><span data-stu-id="58557-118">✔️ DO provide settable properties for optional arguments.</span></span>

 <span data-ttu-id="58557-119">✔️ fornece propriedades somente obtenção para os argumentos necessários.</span><span class="sxs-lookup"><span data-stu-id="58557-119">✔️ DO provide get-only properties for required arguments.</span></span>

 <span data-ttu-id="58557-120">✔️ fornece parâmetros de construtor para inicializar propriedades correspondentes aos argumentos necessários.</span><span class="sxs-lookup"><span data-stu-id="58557-120">✔️ DO provide constructor parameters to initialize properties corresponding to required arguments.</span></span> <span data-ttu-id="58557-121">Cada parâmetro deve ter o mesmo nome (embora com maiúsculas e minúsculas diferentes) como a propriedade correspondente.</span><span class="sxs-lookup"><span data-stu-id="58557-121">Each parameter should have the same name (although with different casing) as the corresponding property.</span></span>

 <span data-ttu-id="58557-122">❌Evite fornecer parâmetros de construtor para inicializar propriedades correspondentes aos argumentos opcionais.</span><span class="sxs-lookup"><span data-stu-id="58557-122">❌ AVOID providing constructor parameters to initialize properties corresponding to the optional arguments.</span></span>

 <span data-ttu-id="58557-123">Em outras palavras, não têm propriedades que podem ser definidas com um construtor e um setter.</span><span class="sxs-lookup"><span data-stu-id="58557-123">In other words, do not have properties that can be set with both a constructor and a setter.</span></span> <span data-ttu-id="58557-124">Essa diretriz torna muito explícito quais argumentos são opcionais e que são necessários e evita que você tenha duas maneiras de fazer a mesma coisa.</span><span class="sxs-lookup"><span data-stu-id="58557-124">This guideline makes very explicit which arguments are optional and which are required, and avoids having two ways of doing the same thing.</span></span>

 <span data-ttu-id="58557-125">❌EVITE sobrecarregar construtores de atributos personalizados.</span><span class="sxs-lookup"><span data-stu-id="58557-125">❌ AVOID overloading custom attribute constructors.</span></span>

 <span data-ttu-id="58557-126">Ter apenas um construtor se comunica claramente ao usuário quais argumentos são necessários e quais são opcionais.</span><span class="sxs-lookup"><span data-stu-id="58557-126">Having only one constructor clearly communicates to the user which arguments are required and which are optional.</span></span>

 <span data-ttu-id="58557-127">✔️ as classes de atributo personalizado de lacre, se possível.</span><span class="sxs-lookup"><span data-stu-id="58557-127">✔️ DO seal custom attribute classes, if possible.</span></span> <span data-ttu-id="58557-128">Isso torna a pesquisa para o atributo mais rápida.</span><span class="sxs-lookup"><span data-stu-id="58557-128">This makes the look-up for the attribute faster.</span></span>

 <span data-ttu-id="58557-129">*Partes &copy; 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*</span><span class="sxs-lookup"><span data-stu-id="58557-129">*Portions &copy; 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="58557-130">*Reimpresso com permissão da Pearson Education, Inc. das [Diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicado em 22 de outubro de 2008 por Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="58557-130">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="58557-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="58557-131">See also</span></span>

- [<span data-ttu-id="58557-132">Diretrizes de design de estrutura</span><span class="sxs-lookup"><span data-stu-id="58557-132">Framework Design Guidelines</span></span>](index.md)
- [<span data-ttu-id="58557-133">Diretrizes de uso</span><span class="sxs-lookup"><span data-stu-id="58557-133">Usage Guidelines</span></span>](usage-guidelines.md)
