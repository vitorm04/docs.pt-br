---
title: Selar
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- limiting extensibility
- classes [.NET Framework], sealing
- preventing customization
- sealed classes
ms.assetid: cc42267f-bb7a-427a-845e-df97408528d4
ms.openlocfilehash: a54c68efb4ac114fe0e5a5712eca877bef35c103
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290104"
---
# <a name="sealing"></a><span data-ttu-id="3770a-102">Selar</span><span class="sxs-lookup"><span data-stu-id="3770a-102">Sealing</span></span>
<span data-ttu-id="3770a-103">Um dos recursos das estruturas orientadas a objeto é que os desenvolvedores podem estendê-las e personalizá-las de maneiras inesperadas pelos designers de estrutura.</span><span class="sxs-lookup"><span data-stu-id="3770a-103">One of the features of object-oriented frameworks is that developers can extend and customize them in ways unanticipated by the framework designers.</span></span> <span data-ttu-id="3770a-104">Essa é a potência e o perigo do design extensível.</span><span class="sxs-lookup"><span data-stu-id="3770a-104">This is both the power and danger of extensible design.</span></span> <span data-ttu-id="3770a-105">Quando você projeta sua estrutura, é, portanto, muito importante projetar cuidadosamente a extensibilidade quando desejado e limitar a extensibilidade quando for perigoso.</span><span class="sxs-lookup"><span data-stu-id="3770a-105">When you design your framework, it is, therefore, very important to carefully design for extensibility when it is desired, and to limit extensibility when it is dangerous.</span></span>

 <span data-ttu-id="3770a-106">Um mecanismo poderoso que impede a extensibilidade esteja lacrando.</span><span class="sxs-lookup"><span data-stu-id="3770a-106">A powerful mechanism that prevents extensibility is sealing.</span></span> <span data-ttu-id="3770a-107">Você pode lacrar a classe ou membros individuais.</span><span class="sxs-lookup"><span data-stu-id="3770a-107">You can seal either the class or individual members.</span></span> <span data-ttu-id="3770a-108">Lacrar uma classe impede que os usuários herdem da classe.</span><span class="sxs-lookup"><span data-stu-id="3770a-108">Sealing a class prevents users from inheriting from the class.</span></span> <span data-ttu-id="3770a-109">Lacrar um membro impede que os usuários substituam um membro específico.</span><span class="sxs-lookup"><span data-stu-id="3770a-109">Sealing a member prevents users from overriding a particular member.</span></span>

 <span data-ttu-id="3770a-110">❌Não lacre as classes sem ter um bom motivo para fazer isso.</span><span class="sxs-lookup"><span data-stu-id="3770a-110">❌ DO NOT seal classes without having a good reason to do so.</span></span>

 <span data-ttu-id="3770a-111">Lacrar uma classe porque você não pode imaginar um cenário de extensibilidade não é um bom motivo.</span><span class="sxs-lookup"><span data-stu-id="3770a-111">Sealing a class because you cannot think of an extensibility scenario is not a good reason.</span></span> <span data-ttu-id="3770a-112">Os usuários do Framework gostam de herdar de classes por vários motivos não óbvios, como adicionar membros de conveniência.</span><span class="sxs-lookup"><span data-stu-id="3770a-112">Framework users like to inherit from classes for various nonobvious reasons, like adding convenience members.</span></span> <span data-ttu-id="3770a-113">Veja [classes sem lacre](unsealed-classes.md) para obter exemplos de motivos não óbvios que os usuários desejam herdar de um tipo.</span><span class="sxs-lookup"><span data-stu-id="3770a-113">See [Unsealed Classes](unsealed-classes.md) for examples of nonobvious reasons users want to inherit from a type.</span></span>

 <span data-ttu-id="3770a-114">Os bons motivos para lacrar uma classe incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="3770a-114">Good reasons for sealing a class include the following:</span></span>

- <span data-ttu-id="3770a-115">A classe é uma classe estática.</span><span class="sxs-lookup"><span data-stu-id="3770a-115">The class is a static class.</span></span> <span data-ttu-id="3770a-116">Consulte [design de classe estática](static-class.md).</span><span class="sxs-lookup"><span data-stu-id="3770a-116">See [Static Class Design](static-class.md).</span></span>

- <span data-ttu-id="3770a-117">A classe armazena segredos sensíveis à segurança em membros protegidos herdados.</span><span class="sxs-lookup"><span data-stu-id="3770a-117">The class stores security-sensitive secrets in inherited protected members.</span></span>

- <span data-ttu-id="3770a-118">A classe herda muitos membros virtuais e o custo de lacre deles individualmente superaria os benefícios de deixar a classe sem lacre.</span><span class="sxs-lookup"><span data-stu-id="3770a-118">The class inherits many virtual members and the cost of sealing them individually would outweigh the benefits of leaving the class unsealed.</span></span>

- <span data-ttu-id="3770a-119">A classe é um atributo que requer pesquisa de tempo de execução muito rápida.</span><span class="sxs-lookup"><span data-stu-id="3770a-119">The class is an attribute that requires very fast runtime look-up.</span></span> <span data-ttu-id="3770a-120">Os atributos lacrados têm níveis de desempenho ligeiramente mais altos do que os sem lacre.</span><span class="sxs-lookup"><span data-stu-id="3770a-120">Sealed attributes have slightly higher performance levels than unsealed ones.</span></span> <span data-ttu-id="3770a-121">Consulte [atributos](attributes.md).</span><span class="sxs-lookup"><span data-stu-id="3770a-121">See [Attributes](attributes.md).</span></span>

 <span data-ttu-id="3770a-122">❌Não declare membros protegidos ou virtuais em tipos lacrados.</span><span class="sxs-lookup"><span data-stu-id="3770a-122">❌ DO NOT declare protected or virtual members on sealed types.</span></span>

 <span data-ttu-id="3770a-123">Por definição, os tipos lacrados não podem ser herdados de.</span><span class="sxs-lookup"><span data-stu-id="3770a-123">By definition, sealed types cannot be inherited from.</span></span> <span data-ttu-id="3770a-124">Isso significa que membros protegidos em tipos lacrados não podem ser chamados, e métodos virtuais em tipos lacrados não podem ser substituídos.</span><span class="sxs-lookup"><span data-stu-id="3770a-124">This means that protected members on sealed types cannot be called, and virtual methods on sealed types cannot be overridden.</span></span>

 <span data-ttu-id="3770a-125">✔️ Considere lacrar os membros que você substitui.</span><span class="sxs-lookup"><span data-stu-id="3770a-125">✔️ CONSIDER sealing members that you override.</span></span>

 <span data-ttu-id="3770a-126">Problemas que podem resultar da introdução de membros virtuais (discutidos em [Membros virtuais](virtual-members.md)) também se aplicam a substituições, embora a um grau um pouco menor.</span><span class="sxs-lookup"><span data-stu-id="3770a-126">Problems that can result from introducing virtual members (discussed in [Virtual Members](virtual-members.md)) apply to overrides as well, although to a slightly lesser degree.</span></span> <span data-ttu-id="3770a-127">Lacrar uma substituição protege você contra esses problemas começando do ponto na hierarquia de herança.</span><span class="sxs-lookup"><span data-stu-id="3770a-127">Sealing an override shields you from these problems starting from that point in the inheritance hierarchy.</span></span>

 <span data-ttu-id="3770a-128">*Partes © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*</span><span class="sxs-lookup"><span data-stu-id="3770a-128">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="3770a-129">*Reimpresso com permissão da Pearson Education, Inc. das [Diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicado em 22 de outubro de 2008 por Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="3770a-129">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="3770a-130">Veja também</span><span class="sxs-lookup"><span data-stu-id="3770a-130">See also</span></span>

- [<span data-ttu-id="3770a-131">Diretrizes de design de estrutura</span><span class="sxs-lookup"><span data-stu-id="3770a-131">Framework Design Guidelines</span></span>](index.md)
- [<span data-ttu-id="3770a-132">Designer voltado para extensibilidade</span><span class="sxs-lookup"><span data-stu-id="3770a-132">Designing for Extensibility</span></span>](designing-for-extensibility.md)
- [<span data-ttu-id="3770a-133">Classes sem lacre</span><span class="sxs-lookup"><span data-stu-id="3770a-133">Unsealed Classes</span></span>](unsealed-classes.md)
