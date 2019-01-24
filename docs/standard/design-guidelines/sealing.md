---
title: Lacrar
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- limiting extensibility
- classes [.NET Framework], sealing
- preventing customization
- sealed classes
ms.assetid: cc42267f-bb7a-427a-845e-df97408528d4
author: KrzysztofCwalina
ms.openlocfilehash: c8aeb5ce3d93755f30bf68732592a08d7af54957
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54646653"
---
# <a name="sealing"></a><span data-ttu-id="0ea17-102">Lacrar</span><span class="sxs-lookup"><span data-stu-id="0ea17-102">Sealing</span></span>
<span data-ttu-id="0ea17-103">Um dos recursos das estruturas orientada a objeto é que os desenvolvedores podem estender e personalizá-los de maneiras não previstas pelos designers do framework.</span><span class="sxs-lookup"><span data-stu-id="0ea17-103">One of the features of object-oriented frameworks is that developers can extend and customize them in ways unanticipated by the framework designers.</span></span> <span data-ttu-id="0ea17-104">Isso é a potência e o perigo de design extensível.</span><span class="sxs-lookup"><span data-stu-id="0ea17-104">This is both the power and danger of extensible design.</span></span> <span data-ttu-id="0ea17-105">Quando você projeta sua estrutura, ele é, portanto, muito importante para projetar cuidadosamente para extensibilidade quando ele for desejado e para limitar a extensibilidade quando é perigoso.</span><span class="sxs-lookup"><span data-stu-id="0ea17-105">When you design your framework, it is, therefore, very important to carefully design for extensibility when it is desired, and to limit extensibility when it is dangerous.</span></span>  
  
 <span data-ttu-id="0ea17-106">Um mecanismo poderoso que impede a extensibilidade é lacrar.</span><span class="sxs-lookup"><span data-stu-id="0ea17-106">A powerful mechanism that prevents extensibility is sealing.</span></span> <span data-ttu-id="0ea17-107">Você pode lacre a classe ou a membros individuais.</span><span class="sxs-lookup"><span data-stu-id="0ea17-107">You can seal either the class or individual members.</span></span> <span data-ttu-id="0ea17-108">Lacrar uma classe impede que os usuários herdando da classe.</span><span class="sxs-lookup"><span data-stu-id="0ea17-108">Sealing a class prevents users from inheriting from the class.</span></span> <span data-ttu-id="0ea17-109">Lacrar um membro impede que os usuários a substituição de um membro específico.</span><span class="sxs-lookup"><span data-stu-id="0ea17-109">Sealing a member prevents users from overriding a particular member.</span></span>  
  
 <span data-ttu-id="0ea17-110">**X DO NOT** lacrar classes sem ter uma boa razão para isso.</span><span class="sxs-lookup"><span data-stu-id="0ea17-110">**X DO NOT** seal classes without having a good reason to do so.</span></span>  
  
 <span data-ttu-id="0ea17-111">Lacrar uma classe, porque você não é possível pensar em um cenário de extensibilidade não é um bom motivo.</span><span class="sxs-lookup"><span data-stu-id="0ea17-111">Sealing a class because you cannot think of an extensibility scenario is not a good reason.</span></span> <span data-ttu-id="0ea17-112">Usuários da estrutura, como herdar de classes por vários motivos nonobvious, como adicionar membros de conveniência.</span><span class="sxs-lookup"><span data-stu-id="0ea17-112">Framework users like to inherit from classes for various nonobvious reasons, like adding convenience members.</span></span> <span data-ttu-id="0ea17-113">Ver [Classes não seladas](../../../docs/standard/design-guidelines/unsealed-classes.md) para obter exemplos dos motivos nonobvious usuários desejam herdar de um tipo.</span><span class="sxs-lookup"><span data-stu-id="0ea17-113">See [Unsealed Classes](../../../docs/standard/design-guidelines/unsealed-classes.md) for examples of nonobvious reasons users want to inherit from a type.</span></span>  
  
 <span data-ttu-id="0ea17-114">Bons motivos para lacrar uma classe incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="0ea17-114">Good reasons for sealing a class include the following:</span></span>  
  
-   <span data-ttu-id="0ea17-115">A classe é uma classe estática.</span><span class="sxs-lookup"><span data-stu-id="0ea17-115">The class is a static class.</span></span> <span data-ttu-id="0ea17-116">Ver [Design de classe estática](../../../docs/standard/design-guidelines/static-class.md).</span><span class="sxs-lookup"><span data-stu-id="0ea17-116">See [Static Class Design](../../../docs/standard/design-guidelines/static-class.md).</span></span>  
  
-   <span data-ttu-id="0ea17-117">A classe armazena os segredos confidenciais de segurança em membros protegidos herdados.</span><span class="sxs-lookup"><span data-stu-id="0ea17-117">The class stores security-sensitive secrets in inherited protected members.</span></span>  
  
-   <span data-ttu-id="0ea17-118">A classe herda muitos membros virtuais e o custo de lacrá-los individualmente seria superam os benefícios de deixar a classe sem lacre.</span><span class="sxs-lookup"><span data-stu-id="0ea17-118">The class inherits many virtual members and the cost of sealing them individually would outweigh the benefits of leaving the class unsealed.</span></span>  
  
-   <span data-ttu-id="0ea17-119">A classe é um atributo que requer tempo de execução muito rápida pesquisa.</span><span class="sxs-lookup"><span data-stu-id="0ea17-119">The class is an attribute that requires very fast runtime look-up.</span></span> <span data-ttu-id="0ea17-120">Atributos lacrados têm um pouco mais altos níveis de desempenho que aqueles sem lacre.</span><span class="sxs-lookup"><span data-stu-id="0ea17-120">Sealed attributes have slightly higher performance levels than unsealed ones.</span></span> <span data-ttu-id="0ea17-121">ver [atributos](../../../docs/standard/design-guidelines/attributes.md).</span><span class="sxs-lookup"><span data-stu-id="0ea17-121">See [Attributes](../../../docs/standard/design-guidelines/attributes.md).</span></span>  
  
 <span data-ttu-id="0ea17-122">**X DO NOT** declarar membros virtuais ou protegidos em tipos lacrados.</span><span class="sxs-lookup"><span data-stu-id="0ea17-122">**X DO NOT** declare protected or virtual members on sealed types.</span></span>  
  
 <span data-ttu-id="0ea17-123">Por definição, tipos lacrados não podem ser herdados de.</span><span class="sxs-lookup"><span data-stu-id="0ea17-123">By definition, sealed types cannot be inherited from.</span></span> <span data-ttu-id="0ea17-124">Isso significa que membros protegidos em tipos lacrados não podem ser chamados e métodos virtuais em tipos lacrados não podem ser substituídos.</span><span class="sxs-lookup"><span data-stu-id="0ea17-124">This means that protected members on sealed types cannot be called, and virtual methods on sealed types cannot be overridden.</span></span>  
  
 <span data-ttu-id="0ea17-125">**✓ CONSIDER** lacrar membros que você substituir.</span><span class="sxs-lookup"><span data-stu-id="0ea17-125">**✓ CONSIDER** sealing members that you override.</span></span>  
  
 <span data-ttu-id="0ea17-126">Problemas que podem resultar de introduzir membros virtuais (discutidos [membros virtuais](../../../docs/standard/design-guidelines/virtual-members.md)) se aplicam a substituições Além disso, embora a um nível um pouco menor.</span><span class="sxs-lookup"><span data-stu-id="0ea17-126">Problems that can result from introducing virtual members (discussed in [Virtual Members](../../../docs/standard/design-guidelines/virtual-members.md)) apply to overrides as well, although to a slightly lesser degree.</span></span> <span data-ttu-id="0ea17-127">Selando uma substituição protege você contra esses problemas a partir desse ponto na hierarquia de herança.</span><span class="sxs-lookup"><span data-stu-id="0ea17-127">Sealing an override shields you from these problems starting from that point in the inheritance hierarchy.</span></span>  
  
 <span data-ttu-id="0ea17-128">*Portions © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*</span><span class="sxs-lookup"><span data-stu-id="0ea17-128">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="0ea17-129">*Reimpresso com permissão da Pearson Education, Inc. de [as diretrizes de Design do Framework: As convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicados 22 de outubro de 2008 pela Addison-Wesley Professional, como parte da série de desenvolvimento do Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="0ea17-129">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ea17-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0ea17-130">See also</span></span>

- [<span data-ttu-id="0ea17-131">Diretrizes de design do Framework</span><span class="sxs-lookup"><span data-stu-id="0ea17-131">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
- [<span data-ttu-id="0ea17-132">Designer voltado para extensibilidade</span><span class="sxs-lookup"><span data-stu-id="0ea17-132">Designing for Extensibility</span></span>](../../../docs/standard/design-guidelines/designing-for-extensibility.md)
- [<span data-ttu-id="0ea17-133">Classes não seladas</span><span class="sxs-lookup"><span data-stu-id="0ea17-133">Unsealed Classes</span></span>](../../../docs/standard/design-guidelines/unsealed-classes.md)
