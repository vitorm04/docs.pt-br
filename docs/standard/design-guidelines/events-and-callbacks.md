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
ms.openlocfilehash: ad7774fd197db80ce84b3b8a5baa4e9ee06b6cef
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289792"
---
# <a name="events-and-callbacks"></a><span data-ttu-id="336da-102">Eventos e retornos de chamada</span><span class="sxs-lookup"><span data-stu-id="336da-102">Events and Callbacks</span></span>
<span data-ttu-id="336da-103">Os retornos de chamada são pontos de extensibilidade que permitem que uma estrutura chame de volta no código do usuário por meio de um delegado.</span><span class="sxs-lookup"><span data-stu-id="336da-103">Callbacks are extensibility points that allow a framework to call back into user code through a delegate.</span></span> <span data-ttu-id="336da-104">Esses delegados são geralmente passados para a estrutura por meio de um parâmetro de um método.</span><span class="sxs-lookup"><span data-stu-id="336da-104">These delegates are usually passed to the framework through a parameter of a method.</span></span>

 <span data-ttu-id="336da-105">Os eventos são um caso especial de retornos de chamada que dão suporte a sintaxe conveniente e consistente para fornecer o delegado (um manipulador de eventos).</span><span class="sxs-lookup"><span data-stu-id="336da-105">Events are a special case of callbacks that supports convenient and consistent syntax for supplying the delegate (an event handler).</span></span> <span data-ttu-id="336da-106">Além disso, a conclusão e os designers de instruções do Visual Studio fornecem ajuda no uso de APIs baseadas em eventos.</span><span class="sxs-lookup"><span data-stu-id="336da-106">In addition, Visual Studio’s statement completion and designers provide help in using event-based APIs.</span></span> <span data-ttu-id="336da-107">(Consulte [design de eventos](event.md).)</span><span class="sxs-lookup"><span data-stu-id="336da-107">(See [Event Design](event.md).)</span></span>

 <span data-ttu-id="336da-108">✔️ Considere o uso de retornos de chamada para permitir que os usuários forneçam código personalizado a ser executado pela estrutura.</span><span class="sxs-lookup"><span data-stu-id="336da-108">✔️ CONSIDER using callbacks to allow users to provide custom code to be executed by the framework.</span></span>

 <span data-ttu-id="336da-109">✔️ Considere o uso de eventos para permitir que os usuários personalizem o comportamento de uma estrutura sem a necessidade de entender o design orientado a objeto.</span><span class="sxs-lookup"><span data-stu-id="336da-109">✔️ CONSIDER using events to allow users to customize the behavior of a framework without the need for understanding object-oriented design.</span></span>

 <span data-ttu-id="336da-110">✔️ preferem eventos em retornos de chamada simples, pois eles são mais familiares para uma gama mais ampla de desenvolvedores e são integrados com a conclusão da instrução do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="336da-110">✔️ DO prefer events over plain callbacks, because they are more familiar to a broader range of developers and are integrated with Visual Studio statement completion.</span></span>

 <span data-ttu-id="336da-111">❌Evite usar retornos de chamada em APIs sensíveis ao desempenho.</span><span class="sxs-lookup"><span data-stu-id="336da-111">❌ AVOID using callbacks in performance-sensitive APIs.</span></span>

 <span data-ttu-id="336da-112">✔️ usar os novos `Func<...>` tipos, `Action<...>` , ou `Expression<...>` em vez de delegados personalizados, ao definir APIs com retornos de chamada.</span><span class="sxs-lookup"><span data-stu-id="336da-112">✔️ DO use the new `Func<...>`, `Action<...>`, or `Expression<...>` types instead of custom delegates, when defining APIs with callbacks.</span></span>

 <span data-ttu-id="336da-113">`Func<...>`e `Action<...>` representam delegados genéricos.</span><span class="sxs-lookup"><span data-stu-id="336da-113">`Func<...>` and `Action<...>` represent generic delegates.</span></span> <span data-ttu-id="336da-114">`Expression<...>`representa definições de função que podem ser compiladas e, posteriormente, invocadas em tempo de execução, mas também podem ser serializadas e passadas para processos remotos.</span><span class="sxs-lookup"><span data-stu-id="336da-114">`Expression<...>` represents function definitions that can be compiled and subsequently invoked at run time but can also be serialized and passed to remote processes.</span></span>

 <span data-ttu-id="336da-115">✔️ medir e entender as implicações de desempenho do uso do `Expression<...>` , em vez de usar o `Func<...>` e os `Action<...>` delegados.</span><span class="sxs-lookup"><span data-stu-id="336da-115">✔️ DO measure and understand performance implications of using `Expression<...>`, instead of using `Func<...>` and `Action<...>` delegates.</span></span>

 <span data-ttu-id="336da-116">`Expression<...>`os tipos estão na maioria dos casos logicamente equivalentes a `Func<...>` e `Action<...>` delegados.</span><span class="sxs-lookup"><span data-stu-id="336da-116">`Expression<...>` types are in most cases logically equivalent to `Func<...>` and `Action<...>` delegates.</span></span> <span data-ttu-id="336da-117">A principal diferença entre eles é que os delegados se destinam a serem usados em cenários de processo local; as expressões são destinadas a casos em que é benéfico e possível avaliar a expressão em um computador ou processo remoto.</span><span class="sxs-lookup"><span data-stu-id="336da-117">The main difference between them is that the delegates are intended to be used in local process scenarios; expressions are intended for cases where it’s beneficial and possible to evaluate the expression in a remote process or machine.</span></span>

 <span data-ttu-id="336da-118">✔️ entender que ao chamar um delegado, você está executando código arbitrário e pode ter repercussões de segurança, exatidão e compatibilidade.</span><span class="sxs-lookup"><span data-stu-id="336da-118">✔️ DO understand that by calling a delegate, you are executing arbitrary code and that could have security, correctness, and compatibility repercussions.</span></span>

 <span data-ttu-id="336da-119">*Partes © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*</span><span class="sxs-lookup"><span data-stu-id="336da-119">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="336da-120">*Reimpresso com permissão da Pearson Education, Inc. das [Diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicado em 22 de outubro de 2008 por Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="336da-120">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="336da-121">Veja também</span><span class="sxs-lookup"><span data-stu-id="336da-121">See also</span></span>

- [<span data-ttu-id="336da-122">Designer voltado para extensibilidade</span><span class="sxs-lookup"><span data-stu-id="336da-122">Designing for Extensibility</span></span>](designing-for-extensibility.md)
- [<span data-ttu-id="336da-123">Diretrizes de design de estrutura</span><span class="sxs-lookup"><span data-stu-id="336da-123">Framework Design Guidelines</span></span>](index.md)
