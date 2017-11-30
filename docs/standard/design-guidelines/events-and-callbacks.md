---
title: Eventos e retornos de chamada
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- events [.NET Framework], extensibility
- methods [.NET Framework], callback
- callback methods
- callbacks
ms.assetid: 48b55c60-495f-4089-9396-97f9122bba7c
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 217e9eae3540e0a20afd0888d24803285d6352b4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="events-and-callbacks"></a><span data-ttu-id="be01f-102">Eventos e retornos de chamada</span><span class="sxs-lookup"><span data-stu-id="be01f-102">Events and Callbacks</span></span>
<span data-ttu-id="be01f-103">Retornos de chamada são os pontos de extensibilidade que permitem que uma estrutura de retorno de chamada no código de usuário por meio de um representante.</span><span class="sxs-lookup"><span data-stu-id="be01f-103">Callbacks are extensibility points that allow a framework to call back into user code through a delegate.</span></span> <span data-ttu-id="be01f-104">Esses representantes geralmente são passados para o framework por meio de um parâmetro de um método.</span><span class="sxs-lookup"><span data-stu-id="be01f-104">These delegates are usually passed to the framework through a parameter of a method.</span></span>  
  
 <span data-ttu-id="be01f-105">Os eventos são um caso especial de retornos de chamada que dá suporte à sintaxe consistente e conveniente para fornecer o delegado (um manipulador de eventos).</span><span class="sxs-lookup"><span data-stu-id="be01f-105">Events are a special case of callbacks that supports convenient and consistent syntax for supplying the delegate (an event handler).</span></span> <span data-ttu-id="be01f-106">Além disso, a conclusão de instrução e designers de Visual Studio fornecem ajuda usando APIs com base em eventos.</span><span class="sxs-lookup"><span data-stu-id="be01f-106">In addition, Visual Studio’s statement completion and designers provide help in using event-based APIs.</span></span> <span data-ttu-id="be01f-107">(Consulte [evento Design](../../../docs/standard/design-guidelines/event.md).)</span><span class="sxs-lookup"><span data-stu-id="be01f-107">(See [Event Design](../../../docs/standard/design-guidelines/event.md).)</span></span>  
  
 <span data-ttu-id="be01f-108">**✓ CONSIDERE** usando retornos de chamada para permitir que os usuários forneçam um código personalizado a ser executado pelo framework.</span><span class="sxs-lookup"><span data-stu-id="be01f-108">**✓ CONSIDER** using callbacks to allow users to provide custom code to be executed by the framework.</span></span>  
  
 <span data-ttu-id="be01f-109">**✓ CONSIDERE** usando eventos para permitir que os usuários personalizar o comportamento de uma estrutura sem a necessidade de Noções básicas sobre o design orientado a objeto.</span><span class="sxs-lookup"><span data-stu-id="be01f-109">**✓ CONSIDER** using events to allow users to customize the behavior of a framework without the need for understanding object-oriented design.</span></span>  
  
 <span data-ttu-id="be01f-110">**FAZER ✓** eventos prefira retornos de chamada comum, pois eles são mais familiares para uma variedade maior de desenvolvedores e integram-se a conclusão de instrução do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="be01f-110">**✓ DO** prefer events over plain callbacks, because they are more familiar to a broader range of developers and are integrated with Visual Studio statement completion.</span></span>  
  
 <span data-ttu-id="be01f-111">**X Evite** usando retornos de chamada nas APIs de desempenho confidenciais.</span><span class="sxs-lookup"><span data-stu-id="be01f-111">**X AVOID** using callbacks in performance-sensitive APIs.</span></span>  
  
 <span data-ttu-id="be01f-112">**FAZER ✓** usar o novo `Func<...>`, `Action<...>`, ou `Expression<...>` tipos em vez de delegados personalizados, ao definir APIs com retornos de chamada.</span><span class="sxs-lookup"><span data-stu-id="be01f-112">**✓ DO** use the new `Func<...>`, `Action<...>`, or `Expression<...>` types instead of custom delegates, when defining APIs with callbacks.</span></span>  
  
 <span data-ttu-id="be01f-113">`Func<...>`e `Action<...>` representar delegados genéricos.</span><span class="sxs-lookup"><span data-stu-id="be01f-113">`Func<...>` and `Action<...>` represent generic delegates.</span></span> <span data-ttu-id="be01f-114">`Expression<...>`representa as definições de função que podem ser compiladas e subsequentemente invocadas em tempo de execução, mas também ser serializadas e passadas para processos remotos.</span><span class="sxs-lookup"><span data-stu-id="be01f-114">`Expression<...>` represents function definitions that can be compiled and subsequently invoked at runtime but can also be serialized and passed to remote processes.</span></span>  
  
 <span data-ttu-id="be01f-115">**FAZER ✓** medir e compreender as implicações de desempenho do uso de `Expression<...>`, em vez de usar `Func<...>` e `Action<...>` delegados.</span><span class="sxs-lookup"><span data-stu-id="be01f-115">**✓ DO** measure and understand performance implications of using `Expression<...>`, instead of using `Func<...>` and `Action<...>` delegates.</span></span>  
  
 <span data-ttu-id="be01f-116">`Expression<...>`tipos são na maioria dos casos logicamente equivalente à `Func<...>` e `Action<...>` delegados.</span><span class="sxs-lookup"><span data-stu-id="be01f-116">`Expression<...>` types are in most cases logically equivalent to `Func<...>` and `Action<...>` delegates.</span></span> <span data-ttu-id="be01f-117">A principal diferença entre eles é que os delegados destinam-se a ser usado em cenários de processo local; expressões são voltadas para casos onde é possível avaliar a expressão em um computador ou um processo remoto e útil.</span><span class="sxs-lookup"><span data-stu-id="be01f-117">The main difference between them is that the delegates are intended to be used in local process scenarios; expressions are intended for cases where it’s beneficial and possible to evaluate the expression in a remote process or machine.</span></span>  
  
 <span data-ttu-id="be01f-118">**FAZER ✓** entender que, ao chamar um delegado, que está executando código arbitrário e que pode ter repercussões de segurança, a exatidão e a compatibilidade.</span><span class="sxs-lookup"><span data-stu-id="be01f-118">**✓ DO** understand that by calling a delegate, you are executing arbitrary code and that could have security, correctness, and compatibility repercussions.</span></span>  
  
 <span data-ttu-id="be01f-119">*Partes © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*</span><span class="sxs-lookup"><span data-stu-id="be01f-119">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="be01f-120">*Reimpressas pela permissão de Pearson educação, Inc. de [diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicados 22 de outubro de 2008, Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="be01f-120">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be01f-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="be01f-121">See Also</span></span>  
 [<span data-ttu-id="be01f-122">Criação de extensibilidade</span><span class="sxs-lookup"><span data-stu-id="be01f-122">Designing for Extensibility</span></span>](../../../docs/standard/design-guidelines/designing-for-extensibility.md)  
 [<span data-ttu-id="be01f-123">Diretrizes de design do Framework</span><span class="sxs-lookup"><span data-stu-id="be01f-123">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
