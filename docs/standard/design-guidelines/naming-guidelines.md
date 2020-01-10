---
title: Nomeando diretivas
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
ms.openlocfilehash: ad98c0f3b02bdc81e6348493b4e0a02f9cb20ed4
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709186"
---
# <a name="naming-guidelines"></a><span data-ttu-id="2c3b1-102">Nomeando diretivas</span><span class="sxs-lookup"><span data-stu-id="2c3b1-102">Naming Guidelines</span></span>
<span data-ttu-id="2c3b1-103">Seguir um conjunto consistente de convenções de nomenclatura no desenvolvimento de uma estrutura pode ser uma grande contribuição para a usabilidade da estrutura.</span><span class="sxs-lookup"><span data-stu-id="2c3b1-103">Following a consistent set of naming conventions in the development of a framework can be a major contribution to the framework’s usability.</span></span> <span data-ttu-id="2c3b1-104">Ele permite que a estrutura seja usada por muitos desenvolvedores em projetos muito separados.</span><span class="sxs-lookup"><span data-stu-id="2c3b1-104">It allows the framework to be used by many developers on widely separated projects.</span></span> <span data-ttu-id="2c3b1-105">Além da consistência do formulário, os nomes dos elementos da estrutura devem ser facilmente compreendidos e devem transmitir a função de cada elemento.</span><span class="sxs-lookup"><span data-stu-id="2c3b1-105">Beyond consistency of form, names of framework elements must be easily understood and must convey the function of each element.</span></span>  
  
 <span data-ttu-id="2c3b1-106">O objetivo deste capítulo é fornecer um conjunto consistente de convenções de nomenclatura que resulte em nomes que fazem sentido imediato para os desenvolvedores.</span><span class="sxs-lookup"><span data-stu-id="2c3b1-106">The goal of this chapter is to provide a consistent set of naming conventions that results in names that make immediate sense to developers.</span></span>  
  
 <span data-ttu-id="2c3b1-107">Embora a adoção dessas convenções de nomenclatura como diretrizes gerais de desenvolvimento de código resulte em nomes mais consistentes em todo o seu código, você só é necessário aplicá-las a APIs que são divulgadas publicamente (Membros e tipos públicos ou protegidos e interfaces implementadas explicitamente).</span><span class="sxs-lookup"><span data-stu-id="2c3b1-107">Although adopting these naming conventions as general code development guidelines would result in more consistent naming throughout your code, you are required only to apply them to APIs that are publicly exposed (public or protected types and members, and explicitly implemented interfaces).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2c3b1-108">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="2c3b1-108">In This Section</span></span>  
 [<span data-ttu-id="2c3b1-109">Convenções de maiúsculas e minúsculas</span><span class="sxs-lookup"><span data-stu-id="2c3b1-109">Capitalization Conventions</span></span>](../../../docs/standard/design-guidelines/capitalization-conventions.md)  
 [<span data-ttu-id="2c3b1-110">Convenções de nomenclatura gerais</span><span class="sxs-lookup"><span data-stu-id="2c3b1-110">General Naming Conventions</span></span>](../../../docs/standard/design-guidelines/general-naming-conventions.md)  
 [<span data-ttu-id="2c3b1-111">Nomes de Assemblies e DLLs</span><span class="sxs-lookup"><span data-stu-id="2c3b1-111">Names of Assemblies and DLLs</span></span>](../../../docs/standard/design-guidelines/names-of-assemblies-and-dlls.md)  
 [<span data-ttu-id="2c3b1-112">Nomes de namespaces</span><span class="sxs-lookup"><span data-stu-id="2c3b1-112">Names of Namespaces</span></span>](../../../docs/standard/design-guidelines/names-of-namespaces.md)  
 [<span data-ttu-id="2c3b1-113">Nomes de classes, structs e interfaces</span><span class="sxs-lookup"><span data-stu-id="2c3b1-113">Names of Classes, Structs, and Interfaces</span></span>](../../../docs/standard/design-guidelines/names-of-classes-structs-and-interfaces.md)  
 [<span data-ttu-id="2c3b1-114">Nomes de membros de tipo</span><span class="sxs-lookup"><span data-stu-id="2c3b1-114">Names of Type Members</span></span>](../../../docs/standard/design-guidelines/names-of-type-members.md)  
 [<span data-ttu-id="2c3b1-115">Parâmetros de nomeação</span><span class="sxs-lookup"><span data-stu-id="2c3b1-115">Naming Parameters</span></span>](../../../docs/standard/design-guidelines/naming-parameters.md)  
 [<span data-ttu-id="2c3b1-116">Recursos de nomenclatura</span><span class="sxs-lookup"><span data-stu-id="2c3b1-116">Naming Resources</span></span>](../../../docs/standard/design-guidelines/naming-resources.md)  
 <span data-ttu-id="2c3b1-117">*Partes © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*</span><span class="sxs-lookup"><span data-stu-id="2c3b1-117">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="2c3b1-118">*Reimpresso com permissão da Pearson Education, Inc. das [Diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicado em 22 de outubro de 2008 por Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="2c3b1-118">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c3b1-119">Veja também</span><span class="sxs-lookup"><span data-stu-id="2c3b1-119">See also</span></span>

- [<span data-ttu-id="2c3b1-120">Diretrizes de design do Framework</span><span class="sxs-lookup"><span data-stu-id="2c3b1-120">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
