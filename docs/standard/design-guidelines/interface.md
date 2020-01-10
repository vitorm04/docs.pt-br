---
title: Design de interface
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- interfaces [.NET Framework], design guidelines
- type design guidelines, interfaces
- class library design guidelines [.NET Framework], interfaces
ms.assetid: a016bd18-6710-4358-9438-9f190a295392
ms.openlocfilehash: 06b2e0d281314f3bd6346a7dbbd8bb56928fe58b
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709290"
---
# <a name="interface-design"></a><span data-ttu-id="1b3a8-102">Design de interface</span><span class="sxs-lookup"><span data-stu-id="1b3a8-102">Interface Design</span></span>
<span data-ttu-id="1b3a8-103">Embora a maioria das APIs seja melhor modelada com classes e estruturas, há casos em que as interfaces são mais apropriadas ou são a única opção.</span><span class="sxs-lookup"><span data-stu-id="1b3a8-103">Although most APIs are best modeled using classes and structs, there are cases in which interfaces are more appropriate or are the only option.</span></span>  
  
 <span data-ttu-id="1b3a8-104">O CLR não dá suporte a várias heranças (ou seja, classes CLR não podem herdar de mais de uma classe base), mas permite que os tipos implementem uma ou mais interfaces além de herdar de uma classe base.</span><span class="sxs-lookup"><span data-stu-id="1b3a8-104">The CLR does not support multiple inheritance (i.e., CLR classes cannot inherit from more than one base class), but it does allow types to implement one or more interfaces in addition to inheriting from a base class.</span></span> <span data-ttu-id="1b3a8-105">Portanto, as interfaces são geralmente usadas para atingir o efeito de várias heranças.</span><span class="sxs-lookup"><span data-stu-id="1b3a8-105">Therefore, interfaces are often used to achieve the effect of multiple inheritance.</span></span> <span data-ttu-id="1b3a8-106">Por exemplo, <xref:System.IDisposable> é uma interface que permite que os tipos ofereçam suporte a Disposability independente de qualquer outra hierarquia de herança na qual desejam participar.</span><span class="sxs-lookup"><span data-stu-id="1b3a8-106">For example, <xref:System.IDisposable> is an interface that allows types to support disposability independent of any other inheritance hierarchy in which they want to participate.</span></span>  
  
 <span data-ttu-id="1b3a8-107">A outra situação na qual a definição de uma interface é apropriada é a criação de uma interface comum que pode ser suportada por vários tipos, incluindo alguns tipos de valor.</span><span class="sxs-lookup"><span data-stu-id="1b3a8-107">The other situation in which defining an interface is appropriate is in creating a common interface that can be supported by several types, including some value types.</span></span> <span data-ttu-id="1b3a8-108">Tipos de valor não podem herdar de tipos diferentes de <xref:System.ValueType>, mas podem implementar interfaces, portanto, usar uma interface é a única opção para fornecer um tipo de base comum.</span><span class="sxs-lookup"><span data-stu-id="1b3a8-108">Value types cannot inherit from types other than <xref:System.ValueType>, but they can implement interfaces, so using an interface is the only option in order to provide a common base type.</span></span>  
  
 <span data-ttu-id="1b3a8-109">**✓ DO** definir uma interface, se você precisar de algum API comuns para serem suportados por um conjunto de tipos que inclui os tipos de valor.</span><span class="sxs-lookup"><span data-stu-id="1b3a8-109">**✓ DO** define an interface if you need some common API to be supported by a set of types that includes value types.</span></span>  
  
 <span data-ttu-id="1b3a8-110">**✓ CONSIDER** define uma interface, se você precisar oferecer suporte a sua funcionalidade em tipos que herdam já algum outro tipo.</span><span class="sxs-lookup"><span data-stu-id="1b3a8-110">**✓ CONSIDER** defining an interface if you need to support its functionality on types that already inherit from some other type.</span></span>  
  
 <span data-ttu-id="1b3a8-111">**X AVOID** usando as interfaces do marcador (interfaces com nenhum membro).</span><span class="sxs-lookup"><span data-stu-id="1b3a8-111">**X AVOID** using marker interfaces (interfaces with no members).</span></span>  
  
 <span data-ttu-id="1b3a8-112">Se você precisar marcar uma classe como tendo uma característica específica (marcador), em geral, use um atributo personalizado em vez de uma interface.</span><span class="sxs-lookup"><span data-stu-id="1b3a8-112">If you need to mark a class as having a specific characteristic (marker), in general, use a custom attribute rather than an interface.</span></span>  
  
 <span data-ttu-id="1b3a8-113">**✓ DO** fornecer pelo menos um tipo que é uma implementação de uma interface.</span><span class="sxs-lookup"><span data-stu-id="1b3a8-113">**✓ DO** provide at least one type that is an implementation of an interface.</span></span>  
  
 <span data-ttu-id="1b3a8-114">Isso ajuda a validar o design da interface.</span><span class="sxs-lookup"><span data-stu-id="1b3a8-114">Doing this helps to validate the design of the interface.</span></span> <span data-ttu-id="1b3a8-115">Por exemplo, <xref:System.Collections.Generic.List%601> é uma implementação da interface <xref:System.Collections.Generic.IList%601>.</span><span class="sxs-lookup"><span data-stu-id="1b3a8-115">For example, <xref:System.Collections.Generic.List%601> is an implementation of the <xref:System.Collections.Generic.IList%601> interface.</span></span>  
  
 <span data-ttu-id="1b3a8-116">**✓ DO** fornecer pelo menos uma API que consome cada interface que você definir (um método de interface como um parâmetro ou uma propriedade digitada como a interface).</span><span class="sxs-lookup"><span data-stu-id="1b3a8-116">**✓ DO** provide at least one API that consumes each interface you define (a method taking the interface as a parameter or a property typed as the interface).</span></span>  
  
 <span data-ttu-id="1b3a8-117">Isso ajuda a validar o design da interface.</span><span class="sxs-lookup"><span data-stu-id="1b3a8-117">Doing this helps to validate the interface design.</span></span> <span data-ttu-id="1b3a8-118">Por exemplo, <xref:System.Collections.Generic.List%601.Sort%2A?displayProperty=nameWithType> consome a interface <xref:System.Collections.Generic.IComparer%601?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="1b3a8-118">For example, <xref:System.Collections.Generic.List%601.Sort%2A?displayProperty=nameWithType> consumes the <xref:System.Collections.Generic.IComparer%601?displayProperty=nameWithType> interface.</span></span>  
  
 <span data-ttu-id="1b3a8-119">**X DO NOT** adicionar membros a uma interface que tiver enviado anteriormente.</span><span class="sxs-lookup"><span data-stu-id="1b3a8-119">**X DO NOT** add members to an interface that has previously shipped.</span></span>  
  
 <span data-ttu-id="1b3a8-120">Isso interromperia as implementações da interface.</span><span class="sxs-lookup"><span data-stu-id="1b3a8-120">Doing so would break implementations of the interface.</span></span> <span data-ttu-id="1b3a8-121">Você deve criar uma nova interface para evitar problemas de controle de versão.</span><span class="sxs-lookup"><span data-stu-id="1b3a8-121">You should create a new interface in order to avoid versioning problems.</span></span>  
  
 <span data-ttu-id="1b3a8-122">Exceto pelas situações descritas nestas diretrizes, você deve, em geral, escolher classes em vez de interfaces em projetando bibliotecas reutilizáveis de código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="1b3a8-122">Except for the situations described in these guidelines, you should, in general, choose classes rather than interfaces in designing managed code reusable libraries.</span></span>  
  
 <span data-ttu-id="1b3a8-123">*Partes © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*</span><span class="sxs-lookup"><span data-stu-id="1b3a8-123">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="1b3a8-124">*Reimpresso com permissão da Pearson Education, Inc. das [Diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicado em 22 de outubro de 2008 por Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="1b3a8-124">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b3a8-125">Veja também</span><span class="sxs-lookup"><span data-stu-id="1b3a8-125">See also</span></span>

- [<span data-ttu-id="1b3a8-126">Diretrizes de Design de tipo</span><span class="sxs-lookup"><span data-stu-id="1b3a8-126">Type Design Guidelines</span></span>](../../../docs/standard/design-guidelines/type.md)
- [<span data-ttu-id="1b3a8-127">Diretrizes de design do Framework</span><span class="sxs-lookup"><span data-stu-id="1b3a8-127">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
