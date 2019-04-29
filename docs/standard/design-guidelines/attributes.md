---
title: Atributos
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- attributes [.NET Framework], about
- class library design guidelines [.NET Framework], attributes
ms.assetid: ee0038ef-b247-4747-a650-3c5c5cd58d8b
author: KrzysztofCwalina
ms.openlocfilehash: 6d4cc6615b7f7346e9c8fc2a7264025f318c8a3d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61785561"
---
# <a name="attributes"></a><span data-ttu-id="25ea5-102">Atributos</span><span class="sxs-lookup"><span data-stu-id="25ea5-102">Attributes</span></span>
<span data-ttu-id="25ea5-103"><xref:System.Attribute?displayProperty=nameWithType> uma classe base é usada para definir atributos personalizados.</span><span class="sxs-lookup"><span data-stu-id="25ea5-103"><xref:System.Attribute?displayProperty=nameWithType> is a base class used to define custom attributes.</span></span>  
  
 <span data-ttu-id="25ea5-104">Os atributos são anotações que podem ser adicionadas aos elementos de programação, como assemblies, tipos, membros e parâmetros.</span><span class="sxs-lookup"><span data-stu-id="25ea5-104">Attributes are annotations that can be added to programming elements such as assemblies, types, members, and parameters.</span></span> <span data-ttu-id="25ea5-105">Eles são armazenados nos metadados do assembly e podem ser acessados no tempo de execução usando as APIs de reflexão.</span><span class="sxs-lookup"><span data-stu-id="25ea5-105">They are stored in the metadata of the assembly and can be accessed at runtime using the reflection APIs.</span></span> <span data-ttu-id="25ea5-106">Por exemplo, o Framework define o <xref:System.ObsoleteAttribute>, que pode ser aplicada a um tipo ou membro para indicar que o tipo ou membro foi preterido.</span><span class="sxs-lookup"><span data-stu-id="25ea5-106">For example, the Framework defines the <xref:System.ObsoleteAttribute>, which can be applied to a type or a member to indicate that the type or member has been deprecated.</span></span>  
  
 <span data-ttu-id="25ea5-107">Atributos podem ter uma ou mais propriedades que contêm dados adicionais relacionados ao atributo.</span><span class="sxs-lookup"><span data-stu-id="25ea5-107">Attributes can have one or more properties that carry additional data related to the attribute.</span></span> <span data-ttu-id="25ea5-108">Por exemplo, `ObsoleteAttribute` poderia conter informações adicionais sobre a versão em que um tipo ou membro foi preterido e a descrição das novas APIs, substituindo a API obsoleta.</span><span class="sxs-lookup"><span data-stu-id="25ea5-108">For example, `ObsoleteAttribute` could carry additional information about the release in which a type or a member got deprecated and the description of the new APIs replacing the obsolete API.</span></span>  
  
 <span data-ttu-id="25ea5-109">Algumas propriedades de um atributo devem ser especificadas quando o atributo é aplicado.</span><span class="sxs-lookup"><span data-stu-id="25ea5-109">Some properties of an attribute must be specified when the attribute is applied.</span></span> <span data-ttu-id="25ea5-110">Eles são chamados das propriedades necessárias ou os argumentos necessários, porque eles são representados como parâmetros posicionais de construtor.</span><span class="sxs-lookup"><span data-stu-id="25ea5-110">These are referred to as the required properties or required arguments, because they are represented as positional constructor parameters.</span></span> <span data-ttu-id="25ea5-111">Por exemplo, o <xref:System.Diagnostics.ConditionalAttribute.ConditionString%2A> propriedade do <xref:System.Diagnostics.ConditionalAttribute> é uma propriedade necessária.</span><span class="sxs-lookup"><span data-stu-id="25ea5-111">For example, the <xref:System.Diagnostics.ConditionalAttribute.ConditionString%2A> property of the <xref:System.Diagnostics.ConditionalAttribute> is a required property.</span></span>  
  
 <span data-ttu-id="25ea5-112">As propriedades que não necessariamente precisam ser especificado quando o atributo é aplicado são chamadas propriedades opcionais (ou argumentos opcionais).</span><span class="sxs-lookup"><span data-stu-id="25ea5-112">Properties that do not necessarily have to be specified when the attribute is applied are called optional properties (or optional arguments).</span></span> <span data-ttu-id="25ea5-113">Eles são representados por propriedades configuráveis.</span><span class="sxs-lookup"><span data-stu-id="25ea5-113">They are represented by settable properties.</span></span> <span data-ttu-id="25ea5-114">Compiladores fornecem uma sintaxe especial para definir essas propriedades quando um atributo é aplicado.</span><span class="sxs-lookup"><span data-stu-id="25ea5-114">Compilers provide special syntax to set these properties when an attribute is applied.</span></span> <span data-ttu-id="25ea5-115">Por exemplo, o <xref:System.AttributeUsageAttribute.Inherited%2A?displayProperty=nameWithType> propriedade representa um argumento opcional.</span><span class="sxs-lookup"><span data-stu-id="25ea5-115">For example, the <xref:System.AttributeUsageAttribute.Inherited%2A?displayProperty=nameWithType> property represents an optional argument.</span></span>  
  
 <span data-ttu-id="25ea5-116">**✓ DO** nome classes de atributos personalizados com o sufixo "Atributo".</span><span class="sxs-lookup"><span data-stu-id="25ea5-116">**✓ DO** name custom attribute classes with the suffix "Attribute."</span></span>  
  
 <span data-ttu-id="25ea5-117">**✓ DO** se aplicam a <xref:System.AttributeUsageAttribute> para os atributos personalizados.</span><span class="sxs-lookup"><span data-stu-id="25ea5-117">**✓ DO** apply the <xref:System.AttributeUsageAttribute> to custom attributes.</span></span>  
  
 <span data-ttu-id="25ea5-118">**✓ DO** fornecem propriedades configuráveis para argumentos opcionais.</span><span class="sxs-lookup"><span data-stu-id="25ea5-118">**✓ DO** provide settable properties for optional arguments.</span></span>  
  
 <span data-ttu-id="25ea5-119">**✓ DO** fornecem propriedades somente obtenção para os argumentos necessários.</span><span class="sxs-lookup"><span data-stu-id="25ea5-119">**✓ DO** provide get-only properties for required arguments.</span></span>  
  
 <span data-ttu-id="25ea5-120">**✓ DO** fornecer parâmetros de construtor para inicializar propriedades correspondentes para os argumentos necessários.</span><span class="sxs-lookup"><span data-stu-id="25ea5-120">**✓ DO** provide constructor parameters to initialize properties corresponding to required arguments.</span></span> <span data-ttu-id="25ea5-121">Cada parâmetro deve ter o mesmo nome (embora com maiusculas e minúsculas diferentes) como a propriedade correspondente.</span><span class="sxs-lookup"><span data-stu-id="25ea5-121">Each parameter should have the same name (although with different casing) as the corresponding property.</span></span>  
  
 <span data-ttu-id="25ea5-122">**X AVOID** fornecendo os parâmetros do construtor para inicializar propriedades correspondentes para os argumentos opcionais.</span><span class="sxs-lookup"><span data-stu-id="25ea5-122">**X AVOID** providing constructor parameters to initialize properties corresponding to the optional arguments.</span></span>  
  
 <span data-ttu-id="25ea5-123">Em outras palavras, não têm propriedades que podem ser definidas com um construtor e um setter.</span><span class="sxs-lookup"><span data-stu-id="25ea5-123">In other words, do not have properties that can be set with both a constructor and a setter.</span></span> <span data-ttu-id="25ea5-124">Essa diretriz torna bastante explícito quais argumentos são opcionais e que são necessário e evita a necessidade de duas maneiras de fazer a mesma coisa.</span><span class="sxs-lookup"><span data-stu-id="25ea5-124">This guideline makes very explicit which arguments are optional and which are required, and avoids having two ways of doing the same thing.</span></span>  
  
 <span data-ttu-id="25ea5-125">**X AVOID** sobrecarga construtores de atributo personalizado.</span><span class="sxs-lookup"><span data-stu-id="25ea5-125">**X AVOID** overloading custom attribute constructors.</span></span>  
  
 <span data-ttu-id="25ea5-126">Ter apenas um construtor claramente comunica-se para o usuário quais argumentos são necessários e opcionais.</span><span class="sxs-lookup"><span data-stu-id="25ea5-126">Having only one constructor clearly communicates to the user which arguments are required and which are optional.</span></span>  
  
 <span data-ttu-id="25ea5-127">**✓ DO** lacrar classes de atributo personalizado, se possível.</span><span class="sxs-lookup"><span data-stu-id="25ea5-127">**✓ DO** seal custom attribute classes, if possible.</span></span> <span data-ttu-id="25ea5-128">Isso torna a pesquisa para o atributo mais rápida.</span><span class="sxs-lookup"><span data-stu-id="25ea5-128">This makes the look-up for the attribute faster.</span></span>  
  
 <span data-ttu-id="25ea5-129">*Portions © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*</span><span class="sxs-lookup"><span data-stu-id="25ea5-129">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="25ea5-130">*Reimpresso com permissão da Pearson Education, Inc. de [as diretrizes de Design do Framework: As convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicados 22 de outubro de 2008 pela Addison-Wesley Professional, como parte da série de desenvolvimento do Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="25ea5-130">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25ea5-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="25ea5-131">See also</span></span>

- [<span data-ttu-id="25ea5-132">Diretrizes de design do Framework</span><span class="sxs-lookup"><span data-stu-id="25ea5-132">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
- [<span data-ttu-id="25ea5-133">Diretrizes de uso</span><span class="sxs-lookup"><span data-stu-id="25ea5-133">Usage Guidelines</span></span>](../../../docs/standard/design-guidelines/usage-guidelines.md)
