---
title: Abstrações (tipos abstratos e Interfaces)
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- interfaces [.NET Framework], abstract
- abstract interfaces [.NET Framework]
- abstract types [.NET Framework]
- types [.NET Framework], abstract
ms.assetid: 0a632bc7-9b03-44ee-8842-c82f88672a45
caps.latest.revision: 10
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 2628758891d629400603c51d12ece33df0e1ff1c
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2018
---
# <a name="abstractions-abstract-types-and-interfaces"></a><span data-ttu-id="90957-102">Abstrações (tipos abstratos e Interfaces)</span><span class="sxs-lookup"><span data-stu-id="90957-102">Abstractions (Abstract Types and Interfaces)</span></span>
<span data-ttu-id="90957-103">Uma abstração é um tipo que descreve um contrato, mas não fornece uma implementação completa do contrato.</span><span class="sxs-lookup"><span data-stu-id="90957-103">An abstraction is a type that describes a contract but does not provide a full implementation of the contract.</span></span> <span data-ttu-id="90957-104">Abstrações geralmente são implementadas como interfaces ou classes abstratas e entram com um conjunto bem definido de documentação de referência que descreve a semântica necessária dos tipos de implementação do contrato.</span><span class="sxs-lookup"><span data-stu-id="90957-104">Abstractions are usually implemented as abstract classes or interfaces, and they come with a well-defined set of reference documentation describing the required semantics of the types implementing the contract.</span></span> <span data-ttu-id="90957-105">Algumas das abstrações mais importantes no .NET Framework incluem <xref:System.IO.Stream>, <xref:System.Collections.Generic.IEnumerable%601>, e <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="90957-105">Some of the most important abstractions in the .NET Framework include <xref:System.IO.Stream>, <xref:System.Collections.Generic.IEnumerable%601>, and <xref:System.Object>.</span></span>  
  
 <span data-ttu-id="90957-106">Você pode estender estruturas de implementação de um tipo concreto que dá suporte ao contrato de uma abstração e usando esse tipo concreto com estrutura APIs consumo (operando em) a abstração.</span><span class="sxs-lookup"><span data-stu-id="90957-106">You can extend frameworks by implementing a concrete type that supports the contract of an abstraction and using this concrete type with framework APIs consuming (operating on) the abstraction.</span></span>  
  
 <span data-ttu-id="90957-107">Uma abstração significativa e útil que é capaz de suportar o teste de tempo é muito difícil de design.</span><span class="sxs-lookup"><span data-stu-id="90957-107">A meaningful and useful abstraction that is able to withstand the test of time is very difficult to design.</span></span> <span data-ttu-id="90957-108">A dificuldade principal está obtendo o conjunto certo de membros, não mais e menos não.</span><span class="sxs-lookup"><span data-stu-id="90957-108">The main difficulty is getting the right set of members, no more and no fewer.</span></span> <span data-ttu-id="90957-109">Se uma abstração tem muitos membros, será difícil ou impossível mesmo implementar.</span><span class="sxs-lookup"><span data-stu-id="90957-109">If an abstraction has too many members, it becomes difficult or even impossible to implement.</span></span> <span data-ttu-id="90957-110">Se ela tiver muito poucos membros para a funcionalidade prometido, torna-se inúteis em muitos cenários interessantes.</span><span class="sxs-lookup"><span data-stu-id="90957-110">If it has too few members for the promised functionality, it becomes useless in many interesting scenarios.</span></span>  
  
 <span data-ttu-id="90957-111">Muitos abstrações em uma estrutura também afetam usabilidade do framework.</span><span class="sxs-lookup"><span data-stu-id="90957-111">Too many abstractions in a framework also negatively affect usability of the framework.</span></span> <span data-ttu-id="90957-112">Geralmente é muito difícil de entender uma abstração sem entender como ele se encaixa maior das implementações concretas e as APIs que operam na abstração.</span><span class="sxs-lookup"><span data-stu-id="90957-112">It is often quite difficult to understand an abstraction without understanding how it fits into the larger picture of the concrete implementations and the APIs operating on the abstraction.</span></span> <span data-ttu-id="90957-113">Além disso, os nomes das abstrações e seus membros são necessariamente abstratos, que geralmente torna criptografadas e não-receptiva sem primeiro entender o contexto mais amplo de uso.</span><span class="sxs-lookup"><span data-stu-id="90957-113">Also, names of abstractions and their members are necessarily abstract, which often makes them cryptic and unapproachable without first understanding the broader context of their usage.</span></span>  
  
 <span data-ttu-id="90957-114">No entanto, abstrações fornecem extensibilidade extremamente eficiente que geralmente não podem corresponder a outros mecanismos de extensibilidade.</span><span class="sxs-lookup"><span data-stu-id="90957-114">However, abstractions provide extremely powerful extensibility that the other extensibility mechanisms cannot often match.</span></span> <span data-ttu-id="90957-115">Eles são a essência de vários padrões de arquitetura, como plug-ins, inversão de controle (IoC), pipelines e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="90957-115">They are at the core of many architectural patterns, such as plug-ins, inversion of control (IoC), pipelines, and so on.</span></span> <span data-ttu-id="90957-116">Eles também são extremamente importantes para a capacidade de teste de estruturas.</span><span class="sxs-lookup"><span data-stu-id="90957-116">They are also extremely important for testability of frameworks.</span></span> <span data-ttu-id="90957-117">BOM abstrações possibilitam o stub dependências intensa para fins de teste de unidade.</span><span class="sxs-lookup"><span data-stu-id="90957-117">Good abstractions make it possible to stub out heavy dependencies for the purpose of unit testing.</span></span> <span data-ttu-id="90957-118">Em resumo, as abstrações são responsáveis pela riqueza procurada a estruturas moderna e orientada a objeto.</span><span class="sxs-lookup"><span data-stu-id="90957-118">In summary, abstractions are responsible for the sought-after richness of the modern object-oriented frameworks.</span></span>  
  
 <span data-ttu-id="90957-119">**X não** fornecem abstrações, a menos que eles são testados com o desenvolvimento de várias implementações concretas e APIs, as abstrações de consumo.</span><span class="sxs-lookup"><span data-stu-id="90957-119">**X DO NOT** provide abstractions unless they are tested by developing several concrete implementations and APIs consuming the abstractions.</span></span>  
  
 <span data-ttu-id="90957-120">**FAZER ✓** escolha cuidadosamente entre uma classe abstrata e uma interface ao projetar uma abstração.</span><span class="sxs-lookup"><span data-stu-id="90957-120">**✓ DO** choose carefully between an abstract class and an interface when designing an abstraction.</span></span>  
  
 <span data-ttu-id="90957-121">**✓ CONSIDERE** fornecendo testes de referência para implementações concretas das abstrações.</span><span class="sxs-lookup"><span data-stu-id="90957-121">**✓ CONSIDER** providing reference tests for concrete implementations of abstractions.</span></span> <span data-ttu-id="90957-122">Esses testes devem permitir que os usuários testar se suas implementações implementam corretamente o contrato.</span><span class="sxs-lookup"><span data-stu-id="90957-122">Such tests should allow users to test whether their implementations correctly implement the contract.</span></span>  
  
 <span data-ttu-id="90957-123">*Portions © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*</span><span class="sxs-lookup"><span data-stu-id="90957-123">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="90957-124">*Reimpressas pela permissão de Pearson educação, Inc. de [diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicados 22 de outubro de 2008, Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="90957-124">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90957-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="90957-125">See Also</span></span>  
 [<span data-ttu-id="90957-126">Diretrizes de design do Framework</span><span class="sxs-lookup"><span data-stu-id="90957-126">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
 [<span data-ttu-id="90957-127">Designer voltado para extensibilidade</span><span class="sxs-lookup"><span data-stu-id="90957-127">Designing for Extensibility</span></span>](../../../docs/standard/design-guidelines/designing-for-extensibility.md)
