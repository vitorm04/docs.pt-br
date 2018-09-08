---
title: Designer voltado para extensibilidade
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- extending class libraries
- extensibility with class libraries in .NET Framework
- class library design guidelines [.NET Framework], extensibility
- class library extensibility [.NET Framework]
ms.assetid: 1cdb8740-871a-456c-9bd9-db96ca8d79b3
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9c1690d0cdf1f57eaf0a794d6e71babfa4fa6425
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44199876"
---
# <a name="designing-for-extensibility"></a><span data-ttu-id="6a990-102">Designer voltado para extensibilidade</span><span class="sxs-lookup"><span data-stu-id="6a990-102">Designing for Extensibility</span></span>
<span data-ttu-id="6a990-103">Um aspecto importante da criação de uma estrutura é verificar se que a extensibilidade do framework foi considerada com cuidado.</span><span class="sxs-lookup"><span data-stu-id="6a990-103">One important aspect of designing a framework is making sure the extensibility of the framework has been carefully considered.</span></span> <span data-ttu-id="6a990-104">Isso exige que você compreenda os custos e benefícios associados com vários mecanismos de extensibilidade.</span><span class="sxs-lookup"><span data-stu-id="6a990-104">This requires that you understand the costs and benefits associated with various extensibility mechanisms.</span></span> <span data-ttu-id="6a990-105">Este capítulo ajuda você a decidir qual dos mecanismos de extensibilidade — a criação de subclasses, eventos, os membros virtuais, retornos de chamada e assim por diante — pode lidar melhor com os requisitos de sua estrutura.</span><span class="sxs-lookup"><span data-stu-id="6a990-105">This chapter helps you decide which of the extensibility mechanisms—subclassing, events, virtual members, callbacks, and so on—can best meet the requirements of your framework.</span></span>  
  
 <span data-ttu-id="6a990-106">Há várias maneiras para permitir a extensibilidade em estruturas.</span><span class="sxs-lookup"><span data-stu-id="6a990-106">There are many ways to allow extensibility in frameworks.</span></span> <span data-ttu-id="6a990-107">Eles variam do menos potentes, porém mais baratos para muito eficientes, mas caros.</span><span class="sxs-lookup"><span data-stu-id="6a990-107">They range from less powerful but less costly to very powerful but expensive.</span></span> <span data-ttu-id="6a990-108">Qualquer necessidade de extensibilidade de determinado, você deve escolher o mecanismo de extensibilidade menos dispendioso que atenda aos requisitos.</span><span class="sxs-lookup"><span data-stu-id="6a990-108">For any given extensibility requirement, you should choose the least costly extensibility mechanism that meets the requirements.</span></span> <span data-ttu-id="6a990-109">Tenha em mente que geralmente é possível adicionar mais extensibilidade posteriormente, mas nunca elevá-lo imediatamente sem introduzir alterações significativas.</span><span class="sxs-lookup"><span data-stu-id="6a990-109">Keep in mind that it’s usually possible to add more extensibility later, but you can never take it away without introducing breaking changes.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6a990-110">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="6a990-110">In This Section</span></span>  
 [<span data-ttu-id="6a990-111">Classes não seladas</span><span class="sxs-lookup"><span data-stu-id="6a990-111">Unsealed Classes</span></span>](../../../docs/standard/design-guidelines/unsealed-classes.md)  
 [<span data-ttu-id="6a990-112">Membros protegidos</span><span class="sxs-lookup"><span data-stu-id="6a990-112">Protected Members</span></span>](../../../docs/standard/design-guidelines/protected-members.md)  
 [<span data-ttu-id="6a990-113">Eventos e retornos de chamada</span><span class="sxs-lookup"><span data-stu-id="6a990-113">Events and Callbacks</span></span>](../../../docs/standard/design-guidelines/events-and-callbacks.md)  
 [<span data-ttu-id="6a990-114">Membros virtuais</span><span class="sxs-lookup"><span data-stu-id="6a990-114">Virtual Members</span></span>](../../../docs/standard/design-guidelines/virtual-members.md)  
 [<span data-ttu-id="6a990-115">Abstrações (tipos e interfaces abstratos)</span><span class="sxs-lookup"><span data-stu-id="6a990-115">Abstractions (Abstract Types and Interfaces)</span></span>](../../../docs/standard/design-guidelines/abstractions-abstract-types-and-interfaces.md)  
 [<span data-ttu-id="6a990-116">Classes base para implementar abstrações</span><span class="sxs-lookup"><span data-stu-id="6a990-116">Base Classes for Implementing Abstractions</span></span>](../../../docs/standard/design-guidelines/base-classes-for-implementing-abstractions.md)  
 [<span data-ttu-id="6a990-117">Selar</span><span class="sxs-lookup"><span data-stu-id="6a990-117">Sealing</span></span>](../../../docs/standard/design-guidelines/sealing.md)  
 <span data-ttu-id="6a990-118">*Portions © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*</span><span class="sxs-lookup"><span data-stu-id="6a990-118">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="6a990-119">*Reimpresso com permissão da Pearson Education, Inc. das [Diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicado em 22 de outubro de 2008 por Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="6a990-119">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a990-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6a990-120">See also</span></span>

- [<span data-ttu-id="6a990-121">Diretrizes de design do Framework</span><span class="sxs-lookup"><span data-stu-id="6a990-121">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
