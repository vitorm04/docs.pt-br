---
title: Diretrizes de nomenclatura
description: Nesta visão geral, leia sobre as convenções de nomenclatura a serem usadas no desenvolvimento da estrutura. Acesse artigos que abordam a capitalização, nomenclatura geral e outras diretrizes.
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- names [.NET Framework], about naming guidelines
- naming guidelines [.NET Framework]
- class library design guidelines [.NET Framework], names
- formatting [.NET Framework], names
- identifiers, class library element names
- names [.NET Framework]
- format naming guidelines [.NET Framework]
ms.assetid: fc076d66-9b5f-42d3-aa65-61d970c794a3
ms.openlocfilehash: fbcf5ef5eb02a5e45b5c981b4247ffe1c9c2631b
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/05/2020
ms.locfileid: "84447141"
---
# <a name="naming-guidelines"></a><span data-ttu-id="8c5d8-104">Diretrizes de nomenclatura</span><span class="sxs-lookup"><span data-stu-id="8c5d8-104">Naming Guidelines</span></span>
<span data-ttu-id="8c5d8-105">Seguir um conjunto consistente de convenções de nomenclatura no desenvolvimento de uma estrutura pode ser uma grande contribuição para a usabilidade da estrutura.</span><span class="sxs-lookup"><span data-stu-id="8c5d8-105">Following a consistent set of naming conventions in the development of a framework can be a major contribution to the framework’s usability.</span></span> <span data-ttu-id="8c5d8-106">Ele permite que a estrutura seja usada por muitos desenvolvedores em projetos muito separados.</span><span class="sxs-lookup"><span data-stu-id="8c5d8-106">It allows the framework to be used by many developers on widely separated projects.</span></span> <span data-ttu-id="8c5d8-107">Além da consistência do formulário, os nomes dos elementos da estrutura devem ser facilmente compreendidos e devem transmitir a função de cada elemento.</span><span class="sxs-lookup"><span data-stu-id="8c5d8-107">Beyond consistency of form, names of framework elements must be easily understood and must convey the function of each element.</span></span>  
  
 <span data-ttu-id="8c5d8-108">O objetivo deste capítulo é fornecer um conjunto consistente de convenções de nomenclatura que resulte em nomes que fazem sentido imediato para os desenvolvedores.</span><span class="sxs-lookup"><span data-stu-id="8c5d8-108">The goal of this chapter is to provide a consistent set of naming conventions that results in names that make immediate sense to developers.</span></span>  
  
 <span data-ttu-id="8c5d8-109">Embora a adoção dessas convenções de nomenclatura como diretrizes gerais de desenvolvimento de código resulte em nomes mais consistentes em todo o seu código, você só é necessário aplicá-las a APIs que são divulgadas publicamente (tipos e membros públicos ou protegidos e interfaces implementadas explicitamente).</span><span class="sxs-lookup"><span data-stu-id="8c5d8-109">Although adopting these naming conventions as general code development guidelines would result in more consistent naming throughout your code, you are required only to apply them to APIs that are publicly exposed (public or protected types and members, and explicitly implemented interfaces).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8c5d8-110">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="8c5d8-110">In This Section</span></span>  
 [<span data-ttu-id="8c5d8-111">Convenções de capitalização</span><span class="sxs-lookup"><span data-stu-id="8c5d8-111">Capitalization Conventions</span></span>](capitalization-conventions.md)  
 [<span data-ttu-id="8c5d8-112">Convenções de nomenclatura gerais</span><span class="sxs-lookup"><span data-stu-id="8c5d8-112">General Naming Conventions</span></span>](general-naming-conventions.md)  
 [<span data-ttu-id="8c5d8-113">Nomes de assemblies e DLLs</span><span class="sxs-lookup"><span data-stu-id="8c5d8-113">Names of Assemblies and DLLs</span></span>](names-of-assemblies-and-dlls.md)  
 [<span data-ttu-id="8c5d8-114">Nomes de namespaces</span><span class="sxs-lookup"><span data-stu-id="8c5d8-114">Names of Namespaces</span></span>](names-of-namespaces.md)  
 [<span data-ttu-id="8c5d8-115">Nomes de classes, estruturas e interfaces</span><span class="sxs-lookup"><span data-stu-id="8c5d8-115">Names of Classes, Structs, and Interfaces</span></span>](names-of-classes-structs-and-interfaces.md)  
 [<span data-ttu-id="8c5d8-116">Nomes dos membros do tipo</span><span class="sxs-lookup"><span data-stu-id="8c5d8-116">Names of Type Members</span></span>](names-of-type-members.md)  
 [<span data-ttu-id="8c5d8-117">Parâmetros de nomenclatura</span><span class="sxs-lookup"><span data-stu-id="8c5d8-117">Naming Parameters</span></span>](naming-parameters.md)  
 [<span data-ttu-id="8c5d8-118">Nomeando recursos</span><span class="sxs-lookup"><span data-stu-id="8c5d8-118">Naming Resources</span></span>](naming-resources.md)  
 <span data-ttu-id="8c5d8-119">*Partes © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*</span><span class="sxs-lookup"><span data-stu-id="8c5d8-119">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="8c5d8-120">*Reimpresso com permissão da Pearson Education, Inc. das [Diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicado em 22 de outubro de 2008 por Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="8c5d8-120">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c5d8-121">Confira também</span><span class="sxs-lookup"><span data-stu-id="8c5d8-121">See also</span></span>

- [<span data-ttu-id="8c5d8-122">Diretrizes de design de estrutura</span><span class="sxs-lookup"><span data-stu-id="8c5d8-122">Framework Design Guidelines</span></span>](index.md)
