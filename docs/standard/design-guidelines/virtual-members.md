---
title: Membros virtuais
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- overridable members
- virtual members
- members [.NET Framework], virtual
ms.assetid: 8ff4eb97-0364-43ec-8a02-934b5cd94d19
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b92b648e7886fb0214238e32eacae2870b470340
ms.sourcegitcommit: f513a91160b3fec289dd06646d0d6f81f8fcf910
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46006322"
---
# <a name="virtual-members"></a><span data-ttu-id="8dac5-102">Membros virtuais</span><span class="sxs-lookup"><span data-stu-id="8dac5-102">Virtual Members</span></span>
<span data-ttu-id="8dac5-103">Membros virtuais podem ser substituídos, portanto, alterar o comportamento da subclasse.</span><span class="sxs-lookup"><span data-stu-id="8dac5-103">Virtual members can be overridden, thus changing the behavior of the subclass.</span></span> <span data-ttu-id="8dac5-104">Eles são muito semelhantes aos retornos de chamada em termos de extensibilidade que eles fornecem, mas eles são melhores em termos de desempenho de execução e o consumo de memória.</span><span class="sxs-lookup"><span data-stu-id="8dac5-104">They are quite similar to callbacks in terms of the extensibility they provide, but they are better in terms of execution performance and memory consumption.</span></span> <span data-ttu-id="8dac5-105">Além disso, os membros virtuais se sentir mais naturais em cenários que exigem a criação de um especial de um tipo existente (especialização).</span><span class="sxs-lookup"><span data-stu-id="8dac5-105">Also, virtual members feel more natural in scenarios that require creating a special kind of an existing type (specialization).</span></span>  
  
 <span data-ttu-id="8dac5-106">Membros virtuais executam melhor eventos e retornos de chamada, mas não executam melhor do que métodos não virtuais.</span><span class="sxs-lookup"><span data-stu-id="8dac5-106">Virtual members perform better than callbacks and events, but do not perform better than non-virtual methods.</span></span>  
  
 <span data-ttu-id="8dac5-107">A principal desvantagem de membros virtuais é que o comportamento de um membro virtual só pode ser modificado no momento da compilação.</span><span class="sxs-lookup"><span data-stu-id="8dac5-107">The main disadvantage of virtual members is that the behavior of a virtual member can only be modified at the time of compilation.</span></span> <span data-ttu-id="8dac5-108">O comportamento de um retorno de chamada pode ser modificado no tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="8dac5-108">The behavior of a callback can be modified at runtime.</span></span>  
  
 <span data-ttu-id="8dac5-109">Membros virtuais, assim como os retornos de chamada (e talvez mais do que os retornos de chamada), são caros de criar, testar e manter, porque qualquer chamada para um membro virtual pode ser substituída de forma imprevisível e pode executar código arbitrário.</span><span class="sxs-lookup"><span data-stu-id="8dac5-109">Virtual members, like callbacks (and maybe more than callbacks), are costly to design, test, and maintain because any call to a virtual member can be overridden in unpredictable ways and can execute arbitrary code.</span></span> <span data-ttu-id="8dac5-110">Além disso, muito mais esforço geralmente é necessário para definir claramente o contrato de membros virtuais, portanto, o custo de criação e documentá-los é maior.</span><span class="sxs-lookup"><span data-stu-id="8dac5-110">Also, much more effort is usually required to clearly define the contract of virtual members, so the cost of designing and documenting them is higher.</span></span>  
  
 <span data-ttu-id="8dac5-111">**X DO NOT** tornar membros virtuais, a menos que você tem uma boa razão para isso e você está ciente de todos os custos relacionados à criação, teste e manutenção membros virtuais.</span><span class="sxs-lookup"><span data-stu-id="8dac5-111">**X DO NOT** make members virtual unless you have a good reason to do so and you are aware of all the costs related to designing, testing, and maintaining virtual members.</span></span>  
  
 <span data-ttu-id="8dac5-112">Os membros virtuais serão menos tolerante em termos das alterações que podem ser feitas a eles sem interromper a compatibilidade.</span><span class="sxs-lookup"><span data-stu-id="8dac5-112">Virtual members are less forgiving in terms of changes that can be made to them without breaking compatibility.</span></span> <span data-ttu-id="8dac5-113">Além disso, eles são mais lentos que os membros não-virtual, principalmente porque as chamadas para os membros virtuais não são embutidas.</span><span class="sxs-lookup"><span data-stu-id="8dac5-113">Also, they are slower than non-virtual members, mostly because calls to virtual members are not inlined.</span></span>  
  
 <span data-ttu-id="8dac5-114">**✓ CONSIDER** limitando extensibilidade apenas o que é absolutamente necessário.</span><span class="sxs-lookup"><span data-stu-id="8dac5-114">**✓ CONSIDER** limiting extensibility to only what is absolutely necessary.</span></span>  
  
 <span data-ttu-id="8dac5-115">**✓ DO** prefira acessibilidade protegida acessibilidade pública para membros virtuais.</span><span class="sxs-lookup"><span data-stu-id="8dac5-115">**✓ DO** prefer protected accessibility over public accessibility for virtual members.</span></span> <span data-ttu-id="8dac5-116">Os membros públicos devem fornecer extensibilidade (se necessário) chamando um membro virtual protegida.</span><span class="sxs-lookup"><span data-stu-id="8dac5-116">Public members should provide extensibility (if required) by calling into a protected virtual member.</span></span>  
  
 <span data-ttu-id="8dac5-117">Os membros públicos de uma classe devem fornecer o conjunto certo de funcionalidade para os consumidores diretos dessa classe.</span><span class="sxs-lookup"><span data-stu-id="8dac5-117">The public members of a class should provide the right set of functionality for direct consumers of that class.</span></span> <span data-ttu-id="8dac5-118">Membros virtuais são projetados para ser substituído em subclasses e acessibilidade protegida é uma ótima maneira de definir o escopo de todos os pontos de extensibilidade virtual onde eles podem ser usados.</span><span class="sxs-lookup"><span data-stu-id="8dac5-118">Virtual members are designed to be overridden in subclasses, and protected accessibility is a great way to scope all virtual extensibility points to where they can be used.</span></span>  
  
 <span data-ttu-id="8dac5-119">*Portions © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*</span><span class="sxs-lookup"><span data-stu-id="8dac5-119">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="8dac5-120">*Reimpresso com permissão da Pearson Education, Inc. das [Diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicado em 22 de outubro de 2008 por Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="8dac5-120">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8dac5-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8dac5-121">See also</span></span>

- [<span data-ttu-id="8dac5-122">Diretrizes de design do Framework</span><span class="sxs-lookup"><span data-stu-id="8dac5-122">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
- [<span data-ttu-id="8dac5-123">Designer voltado para extensibilidade</span><span class="sxs-lookup"><span data-stu-id="8dac5-123">Designing for Extensibility</span></span>](../../../docs/standard/design-guidelines/designing-for-extensibility.md)
