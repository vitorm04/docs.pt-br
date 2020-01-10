---
title: Eventos e retornos de chamada
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- events [.NET Framework], extensibility
- methods [.NET Framework], callback
- callback methods
- callbacks
ms.assetid: 48b55c60-495f-4089-9396-97f9122bba7c
ms.openlocfilehash: 80c16e29f1d8a0653295ebc3cf25be6fb78b7dc9
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709407"
---
# <a name="events-and-callbacks"></a><span data-ttu-id="8ca9b-102">Eventos e retornos de chamada</span><span class="sxs-lookup"><span data-stu-id="8ca9b-102">Events and Callbacks</span></span>
<span data-ttu-id="8ca9b-103">Os retornos de chamada são pontos de extensibilidade que permitem que uma estrutura chame de volta no código do usuário por meio de um delegado.</span><span class="sxs-lookup"><span data-stu-id="8ca9b-103">Callbacks are extensibility points that allow a framework to call back into user code through a delegate.</span></span> <span data-ttu-id="8ca9b-104">Esses delegados são geralmente passados para a estrutura por meio de um parâmetro de um método.</span><span class="sxs-lookup"><span data-stu-id="8ca9b-104">These delegates are usually passed to the framework through a parameter of a method.</span></span>  
  
 <span data-ttu-id="8ca9b-105">Os eventos são um caso especial de retornos de chamada que dão suporte a sintaxe conveniente e consistente para fornecer o delegado (um manipulador de eventos).</span><span class="sxs-lookup"><span data-stu-id="8ca9b-105">Events are a special case of callbacks that supports convenient and consistent syntax for supplying the delegate (an event handler).</span></span> <span data-ttu-id="8ca9b-106">Além disso, a conclusão e os designers de instruções do Visual Studio fornecem ajuda no uso de APIs baseadas em eventos.</span><span class="sxs-lookup"><span data-stu-id="8ca9b-106">In addition, Visual Studio’s statement completion and designers provide help in using event-based APIs.</span></span> <span data-ttu-id="8ca9b-107">(Consulte [design de eventos](../../../docs/standard/design-guidelines/event.md).)</span><span class="sxs-lookup"><span data-stu-id="8ca9b-107">(See [Event Design](../../../docs/standard/design-guidelines/event.md).)</span></span>  
  
 <span data-ttu-id="8ca9b-108">**✓ CONSIDER** usando retornos de chamada para permitir que os usuários forneçam um código personalizado a ser executado pelo framework.</span><span class="sxs-lookup"><span data-stu-id="8ca9b-108">**✓ CONSIDER** using callbacks to allow users to provide custom code to be executed by the framework.</span></span>  
  
 <span data-ttu-id="8ca9b-109">**✓ CONSIDER** usando eventos para permitir que os usuários personalizar o comportamento de uma estrutura sem a necessidade de Noções básicas sobre o design orientado a objeto.</span><span class="sxs-lookup"><span data-stu-id="8ca9b-109">**✓ CONSIDER** using events to allow users to customize the behavior of a framework without the need for understanding object-oriented design.</span></span>  
  
 <span data-ttu-id="8ca9b-110">**✓ DO** eventos prefira retornos de chamada comum, pois eles são mais familiares para uma variedade maior de desenvolvedores e integram-se a conclusão de instrução do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="8ca9b-110">**✓ DO** prefer events over plain callbacks, because they are more familiar to a broader range of developers and are integrated with Visual Studio statement completion.</span></span>  
  
 <span data-ttu-id="8ca9b-111">**X AVOID** usando retornos de chamada nas APIs de desempenho confidenciais.</span><span class="sxs-lookup"><span data-stu-id="8ca9b-111">**X AVOID** using callbacks in performance-sensitive APIs.</span></span>  
  
 <span data-ttu-id="8ca9b-112">**✓ DO** usar o novo `Func<...>`, `Action<...>`, ou `Expression<...>` tipos em vez de delegados personalizados, ao definir APIs com retornos de chamada.</span><span class="sxs-lookup"><span data-stu-id="8ca9b-112">**✓ DO** use the new `Func<...>`, `Action<...>`, or `Expression<...>` types instead of custom delegates, when defining APIs with callbacks.</span></span>  
  
 <span data-ttu-id="8ca9b-113">`Func<...>` e `Action<...>` representam delegados genéricos.</span><span class="sxs-lookup"><span data-stu-id="8ca9b-113">`Func<...>` and `Action<...>` represent generic delegates.</span></span> <span data-ttu-id="8ca9b-114">`Expression<...>` representa as definições de função que podem ser compiladas e, posteriormente, invocadas no tempo de execução, mas também podem ser serializadas e passadas para processos remotos.</span><span class="sxs-lookup"><span data-stu-id="8ca9b-114">`Expression<...>` represents function definitions that can be compiled and subsequently invoked at runtime but can also be serialized and passed to remote processes.</span></span>  
  
 <span data-ttu-id="8ca9b-115">**✓ DO** medir e compreender as implicações de desempenho do uso de `Expression<...>`, em vez de usar `Func<...>` e `Action<...>` delegados.</span><span class="sxs-lookup"><span data-stu-id="8ca9b-115">**✓ DO** measure and understand performance implications of using `Expression<...>`, instead of using `Func<...>` and `Action<...>` delegates.</span></span>  
  
 <span data-ttu-id="8ca9b-116">os tipos de `Expression<...>` estão na maioria dos casos logicamente equivalentes a delegados `Func<...>` e `Action<...>`.</span><span class="sxs-lookup"><span data-stu-id="8ca9b-116">`Expression<...>` types are in most cases logically equivalent to `Func<...>` and `Action<...>` delegates.</span></span> <span data-ttu-id="8ca9b-117">A principal diferença entre eles é que os delegados se destinam a serem usados em cenários de processo local; as expressões são destinadas a casos em que é benéfico e possível avaliar a expressão em um computador ou processo remoto.</span><span class="sxs-lookup"><span data-stu-id="8ca9b-117">The main difference between them is that the delegates are intended to be used in local process scenarios; expressions are intended for cases where it’s beneficial and possible to evaluate the expression in a remote process or machine.</span></span>  
  
 <span data-ttu-id="8ca9b-118">**✓ DO** entender que, ao chamar um delegado, que está executando código arbitrário e que pode ter repercussões de segurança, a exatidão e a compatibilidade.</span><span class="sxs-lookup"><span data-stu-id="8ca9b-118">**✓ DO** understand that by calling a delegate, you are executing arbitrary code and that could have security, correctness, and compatibility repercussions.</span></span>  
  
 <span data-ttu-id="8ca9b-119">*Partes © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*</span><span class="sxs-lookup"><span data-stu-id="8ca9b-119">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="8ca9b-120">*Reimpresso com permissão da Pearson Education, Inc. das [Diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicado em 22 de outubro de 2008 por Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="8ca9b-120">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ca9b-121">Veja também</span><span class="sxs-lookup"><span data-stu-id="8ca9b-121">See also</span></span>

- [<span data-ttu-id="8ca9b-122">Designer voltado para extensibilidade</span><span class="sxs-lookup"><span data-stu-id="8ca9b-122">Designing for Extensibility</span></span>](../../../docs/standard/design-guidelines/designing-for-extensibility.md)
- [<span data-ttu-id="8ca9b-123">Diretrizes de design do Framework</span><span class="sxs-lookup"><span data-stu-id="8ca9b-123">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
