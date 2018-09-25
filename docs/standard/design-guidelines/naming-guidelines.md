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
ms.openlocfilehash: 70888e068782add5ebe5ae1c7da3bdee842faea8
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47070208"
---
# <a name="naming-guidelines"></a><span data-ttu-id="17331-102">Diretrizes de nomenclatura</span><span class="sxs-lookup"><span data-stu-id="17331-102">Naming Guidelines</span></span>
<span data-ttu-id="17331-103">Um conjunto consistente de convenções de nomenclatura no desenvolvimento de uma estrutura a seguir pode ser uma contribuição importante para facilidade de uso da estrutura.</span><span class="sxs-lookup"><span data-stu-id="17331-103">Following a consistent set of naming conventions in the development of a framework can be a major contribution to the framework’s usability.</span></span> <span data-ttu-id="17331-104">Ele permite que a estrutura a ser usado por muitos desenvolvedores em projetos amplamente separados.</span><span class="sxs-lookup"><span data-stu-id="17331-104">It allows the framework to be used by many developers on widely separated projects.</span></span> <span data-ttu-id="17331-105">Além da consistência do formulário, os nomes de elementos de estrutura devem ser compreendidos com facilidade e devem transmitir a função de cada elemento.</span><span class="sxs-lookup"><span data-stu-id="17331-105">Beyond consistency of form, names of framework elements must be easily understood and must convey the function of each element.</span></span>  
  
 <span data-ttu-id="17331-106">O objetivo deste capítulo é fornecer um conjunto consistente de convenções de nomenclatura que resulta em nomes que façam sentido imediato para desenvolvedores.</span><span class="sxs-lookup"><span data-stu-id="17331-106">The goal of this chapter is to provide a consistent set of naming conventions that results in names that make immediate sense to developers.</span></span>  
  
 <span data-ttu-id="17331-107">Embora a adotar estas convenções de nomenclatura como diretrizes de desenvolvimento de código geral resultaria na nomenclatura mais consistente em todo o código, é necessário apenas aplicá-las às APIs que são expostas publicamente (públicos ou protegidos de tipos e membros, e implementado explicitamente interfaces).</span><span class="sxs-lookup"><span data-stu-id="17331-107">Although adopting these naming conventions as general code development guidelines would result in more consistent naming throughout your code, you are required only to apply them to APIs that are publicly exposed (public or protected types and members, and explicitly implemented interfaces).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="17331-108">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="17331-108">In This Section</span></span>  
 [<span data-ttu-id="17331-109">Convenções de maiúsculas e minúsculas</span><span class="sxs-lookup"><span data-stu-id="17331-109">Capitalization Conventions</span></span>](../../../docs/standard/design-guidelines/capitalization-conventions.md)  
 [<span data-ttu-id="17331-110">Convenções de nomenclatura gerais</span><span class="sxs-lookup"><span data-stu-id="17331-110">General Naming Conventions</span></span>](../../../docs/standard/design-guidelines/general-naming-conventions.md)  
 [<span data-ttu-id="17331-111">Nomes de Assemblies e DLLs</span><span class="sxs-lookup"><span data-stu-id="17331-111">Names of Assemblies and DLLs</span></span>](../../../docs/standard/design-guidelines/names-of-assemblies-and-dlls.md)  
 [<span data-ttu-id="17331-112">Nomes de namespaces</span><span class="sxs-lookup"><span data-stu-id="17331-112">Names of Namespaces</span></span>](../../../docs/standard/design-guidelines/names-of-namespaces.md)  
 [<span data-ttu-id="17331-113">Nomes de classes, structs e interfaces</span><span class="sxs-lookup"><span data-stu-id="17331-113">Names of Classes, Structs, and Interfaces</span></span>](../../../docs/standard/design-guidelines/names-of-classes-structs-and-interfaces.md)  
 [<span data-ttu-id="17331-114">Nomes de membros de tipo</span><span class="sxs-lookup"><span data-stu-id="17331-114">Names of Type Members</span></span>](../../../docs/standard/design-guidelines/names-of-type-members.md)  
 [<span data-ttu-id="17331-115">Parâmetros de nomeação</span><span class="sxs-lookup"><span data-stu-id="17331-115">Naming Parameters</span></span>](../../../docs/standard/design-guidelines/naming-parameters.md)  
 [<span data-ttu-id="17331-116">Recursos de nomenclatura</span><span class="sxs-lookup"><span data-stu-id="17331-116">Naming Resources</span></span>](../../../docs/standard/design-guidelines/naming-resources.md)  
 <span data-ttu-id="17331-117">*Portions © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*</span><span class="sxs-lookup"><span data-stu-id="17331-117">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="17331-118">*Reimpresso com permissão da Pearson Education, Inc. das [Diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicado em 22 de outubro de 2008 por Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="17331-118">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17331-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="17331-119">See also</span></span>

- [<span data-ttu-id="17331-120">Diretrizes de design do Framework</span><span class="sxs-lookup"><span data-stu-id="17331-120">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
