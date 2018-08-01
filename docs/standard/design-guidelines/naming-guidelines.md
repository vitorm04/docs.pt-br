---
title: Diretrizes de nomenclatura
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 53ffb641d3e507a937c304725b3c8590d046338e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33572964"
---
# <a name="naming-guidelines"></a><span data-ttu-id="dd90e-102">Diretrizes de nomenclatura</span><span class="sxs-lookup"><span data-stu-id="dd90e-102">Naming Guidelines</span></span>
<span data-ttu-id="dd90e-103">Um conjunto de convenções de nomenclatura no desenvolvimento de uma estrutura consistente a seguir pode ser uma contribuição principais a usabilidade do framework.</span><span class="sxs-lookup"><span data-stu-id="dd90e-103">Following a consistent set of naming conventions in the development of a framework can be a major contribution to the framework’s usability.</span></span> <span data-ttu-id="dd90e-104">Ele permite que a estrutura a ser usada por muitos desenvolvedores em projetos amplamente separados.</span><span class="sxs-lookup"><span data-stu-id="dd90e-104">It allows the framework to be used by many developers on widely separated projects.</span></span> <span data-ttu-id="dd90e-105">Além da consistência do formulário, nomes de elementos do framework devem ser facilmente compreendidos e devem transmitir a função de cada elemento.</span><span class="sxs-lookup"><span data-stu-id="dd90e-105">Beyond consistency of form, names of framework elements must be easily understood and must convey the function of each element.</span></span>  
  
 <span data-ttu-id="dd90e-106">O objetivo deste capítulo é fornecer um conjunto de convenções de nomenclatura consistente que resulta em nomes que fazem sentido imediato para desenvolvedores.</span><span class="sxs-lookup"><span data-stu-id="dd90e-106">The goal of this chapter is to provide a consistent set of naming conventions that results in names that make immediate sense to developers.</span></span>  
  
 <span data-ttu-id="dd90e-107">Embora adotando estas convenções de nomenclatura como diretrizes de desenvolvimento de código geral resultaria na nomeação mais consistente em todo o código, é necessário apenas para aplicá-las a APIs que são expostos publicamente (públicos ou protegidos tipos e membros, e implementado explicitamente interfaces).</span><span class="sxs-lookup"><span data-stu-id="dd90e-107">Although adopting these naming conventions as general code development guidelines would result in more consistent naming throughout your code, you are required only to apply them to APIs that are publicly exposed (public or protected types and members, and explicitly implemented interfaces).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="dd90e-108">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="dd90e-108">In This Section</span></span>  
 [<span data-ttu-id="dd90e-109">Convenções de maiúsculas e minúsculas</span><span class="sxs-lookup"><span data-stu-id="dd90e-109">Capitalization Conventions</span></span>](../../../docs/standard/design-guidelines/capitalization-conventions.md)  
 [<span data-ttu-id="dd90e-110">Convenções de nomenclatura gerais</span><span class="sxs-lookup"><span data-stu-id="dd90e-110">General Naming Conventions</span></span>](../../../docs/standard/design-guidelines/general-naming-conventions.md)  
 [<span data-ttu-id="dd90e-111">Nomes de Assemblies e DLLs</span><span class="sxs-lookup"><span data-stu-id="dd90e-111">Names of Assemblies and DLLs</span></span>](../../../docs/standard/design-guidelines/names-of-assemblies-and-dlls.md)  
 [<span data-ttu-id="dd90e-112">Nomes de namespaces</span><span class="sxs-lookup"><span data-stu-id="dd90e-112">Names of Namespaces</span></span>](../../../docs/standard/design-guidelines/names-of-namespaces.md)  
 [<span data-ttu-id="dd90e-113">Nomes de classes, structs e interfaces</span><span class="sxs-lookup"><span data-stu-id="dd90e-113">Names of Classes, Structs, and Interfaces</span></span>](../../../docs/standard/design-guidelines/names-of-classes-structs-and-interfaces.md)  
 [<span data-ttu-id="dd90e-114">Nomes de membros de tipo</span><span class="sxs-lookup"><span data-stu-id="dd90e-114">Names of Type Members</span></span>](../../../docs/standard/design-guidelines/names-of-type-members.md)  
 [<span data-ttu-id="dd90e-115">Parâmetros de nomeação</span><span class="sxs-lookup"><span data-stu-id="dd90e-115">Naming Parameters</span></span>](../../../docs/standard/design-guidelines/naming-parameters.md)  
 [<span data-ttu-id="dd90e-116">Recursos de nomenclatura</span><span class="sxs-lookup"><span data-stu-id="dd90e-116">Naming Resources</span></span>](../../../docs/standard/design-guidelines/naming-resources.md)  
 <span data-ttu-id="dd90e-117">*Portions © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*</span><span class="sxs-lookup"><span data-stu-id="dd90e-117">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="dd90e-118">*Reimpressas pela permissão de Pearson educação, Inc. de [diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicados 22 de outubro de 2008, Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="dd90e-118">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd90e-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="dd90e-119">See Also</span></span>  
 [<span data-ttu-id="dd90e-120">Diretrizes de design do Framework</span><span class="sxs-lookup"><span data-stu-id="dd90e-120">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
