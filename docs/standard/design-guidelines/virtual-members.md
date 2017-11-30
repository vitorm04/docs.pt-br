---
title: Membros virtuais
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- overridable members
- virtual members
- members [.NET Framework], virtual
ms.assetid: 8ff4eb97-0364-43ec-8a02-934b5cd94d19
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 56838fc4c1c1e7cb8723beee3f0e6b23515d43f0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="virtual-members"></a><span data-ttu-id="536bb-102">Membros virtuais</span><span class="sxs-lookup"><span data-stu-id="536bb-102">Virtual Members</span></span>
<span data-ttu-id="536bb-103">Membros virtuais podem ser substituídos, portanto, alterar o comportamento da subclasse.</span><span class="sxs-lookup"><span data-stu-id="536bb-103">Virtual members can be overridden, thus changing the behavior of the subclass.</span></span> <span data-ttu-id="536bb-104">Eles são bastante semelhantes para retornos de chamada em termos de extensibilidade que eles fornecem, mas eles são melhores em termos de desempenho de execução e o consumo de memória.</span><span class="sxs-lookup"><span data-stu-id="536bb-104">They are quite similar to callbacks in terms of the extensibility they provide, but they are better in terms of execution performance and memory consumption.</span></span> <span data-ttu-id="536bb-105">Além disso, os membros virtuais achar mais naturais em cenários que exigem a criação especial de tipo de um tipo existente (especialização).</span><span class="sxs-lookup"><span data-stu-id="536bb-105">Also, virtual members feel more natural in scenarios that require creating a special kind of an existing type (specialization).</span></span>  
  
 <span data-ttu-id="536bb-106">Membros virtuais têm desempenho melhor que eventos e retornos de chamada, mas não executar melhor métodos não virtuais.</span><span class="sxs-lookup"><span data-stu-id="536bb-106">Virtual members perform better than callbacks and events, but do not perform better than non-virtual methods.</span></span>  
  
 <span data-ttu-id="536bb-107">A principal desvantagem de membros virtuais é que o comportamento de um membro virtual só pode ser modificado no momento da compilação.</span><span class="sxs-lookup"><span data-stu-id="536bb-107">The main disadvantage of virtual members is that the behavior of a virtual member can only be modified at the time of compilation.</span></span> <span data-ttu-id="536bb-108">O comportamento de um retorno de chamada pode ser modificado no tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="536bb-108">The behavior of a callback can be modified at runtime.</span></span>  
  
 <span data-ttu-id="536bb-109">Membros virtuais, como retornos de chamada (e talvez mais de retornos de chamada), são caros criar, testar e manter, porque qualquer chamada para um membro virtual pode ser substituída de forma imprevisível e pode executar código arbitrário.</span><span class="sxs-lookup"><span data-stu-id="536bb-109">Virtual members, like callbacks (and maybe more than callbacks), are costly to design, test, and maintain because any call to a virtual member can be overridden in unpredictable ways and can execute arbitrary code.</span></span> <span data-ttu-id="536bb-110">Além disso, muito mais esforço geralmente é necessário definir claramente o contrato de membros virtuais, portanto, o custo de projetar e documentá-los é maior.</span><span class="sxs-lookup"><span data-stu-id="536bb-110">Also, much more effort is usually required to clearly define the contract of virtual members, so the cost of designing and documenting them is higher.</span></span>  
  
 <span data-ttu-id="536bb-111">**X não** tornar membros virtuais, a menos que você tem uma boa razão para isso e você está ciente de todos os custos relacionados à criação, teste e manutenção membros virtuais.</span><span class="sxs-lookup"><span data-stu-id="536bb-111">**X DO NOT** make members virtual unless you have a good reason to do so and you are aware of all the costs related to designing, testing, and maintaining virtual members.</span></span>  
  
 <span data-ttu-id="536bb-112">Membros virtuais são menos tolerante com em termos de alterações que podem ser feitas a eles sem perder a compatibilidade.</span><span class="sxs-lookup"><span data-stu-id="536bb-112">Virtual members are less forgiving in terms of changes that can be made to them without breaking compatibility.</span></span> <span data-ttu-id="536bb-113">Além disso, eles são mais lentos do que os membros não virtual, principalmente como chamadas para membros virtuais não são embutidas.</span><span class="sxs-lookup"><span data-stu-id="536bb-113">Also, they are slower than non-virtual members, mostly because calls to virtual members are not inlined.</span></span>  
  
 <span data-ttu-id="536bb-114">**✓ CONSIDERE** limitando extensibilidade apenas o que é absolutamente necessário.</span><span class="sxs-lookup"><span data-stu-id="536bb-114">**✓ CONSIDER** limiting extensibility to only what is absolutely necessary.</span></span>  
  
 <span data-ttu-id="536bb-115">**FAZER ✓** prefira acessibilidade protegida acessibilidade pública para membros virtuais.</span><span class="sxs-lookup"><span data-stu-id="536bb-115">**✓ DO** prefer protected accessibility over public accessibility for virtual members.</span></span> <span data-ttu-id="536bb-116">Membros públicos devem fornecer extensibilidade (se necessário) por chamar um membro virtual protegido.</span><span class="sxs-lookup"><span data-stu-id="536bb-116">Public members should provide extensibility (if required) by calling into a protected virtual member.</span></span>  
  
 <span data-ttu-id="536bb-117">Os membros públicos de uma classe devem fornecer o conjunto certo de funcionalidade para consumidores diretos dessa classe.</span><span class="sxs-lookup"><span data-stu-id="536bb-117">The public members of a class should provide the right set of functionality for direct consumers of that class.</span></span> <span data-ttu-id="536bb-118">Membros virtuais são projetados para ser substituído em subclasses e acessibilidade protegida é uma ótima maneira de definir o escopo de todos os pontos de extensibilidade virtual onde eles podem ser usados.</span><span class="sxs-lookup"><span data-stu-id="536bb-118">Virtual members are designed to be overridden in subclasses, and protected accessibility is a great way to scope all virtual extensibility points to where they can be used.</span></span>  
  
 <span data-ttu-id="536bb-119">*Partes © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*</span><span class="sxs-lookup"><span data-stu-id="536bb-119">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="536bb-120">*Reimpressas pela permissão de Pearson educação, Inc. de [diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicados 22 de outubro de 2008, Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="536bb-120">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="536bb-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="536bb-121">See Also</span></span>  
 [<span data-ttu-id="536bb-122">Diretrizes de design do Framework</span><span class="sxs-lookup"><span data-stu-id="536bb-122">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
 [<span data-ttu-id="536bb-123">Criação de extensibilidade</span><span class="sxs-lookup"><span data-stu-id="536bb-123">Designing for Extensibility</span></span>](../../../docs/standard/design-guidelines/designing-for-extensibility.md)
