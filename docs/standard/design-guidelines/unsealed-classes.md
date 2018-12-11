---
title: Classes não seladas
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- classes [.NET Framework], unsealed
- unsealed classes
- inheritance, classes
ms.assetid: 9a3bd505-90f5-4053-9f0d-3cf5fa3d3ebf
author: KrzysztofCwalina
ms.openlocfilehash: 8d7b1500506ec73a0d33d5352756cb85039358e5
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53153222"
---
# <a name="unsealed-classes"></a><span data-ttu-id="3ab99-102">Classes não seladas</span><span class="sxs-lookup"><span data-stu-id="3ab99-102">Unsealed Classes</span></span>
<span data-ttu-id="3ab99-103">Classes sealed não podem ser herdadas de, e evitar a extensibilidade.</span><span class="sxs-lookup"><span data-stu-id="3ab99-103">Sealed classes cannot be inherited from, and they prevent extensibility.</span></span> <span data-ttu-id="3ab99-104">Em contraste, as classes que podem ser herdadas de são chamadas classes não seladas.</span><span class="sxs-lookup"><span data-stu-id="3ab99-104">In contrast, classes that can be inherited from are called unsealed classes.</span></span>  
  
 <span data-ttu-id="3ab99-105">**✓ CONSIDER** usar classes não lacradas sem nenhum adicionado membros virtuais ou protegidos como uma ótima maneira de fornecer mais barato ainda muito mais valioso extensibilidade para uma estrutura.</span><span class="sxs-lookup"><span data-stu-id="3ab99-105">**✓ CONSIDER** using unsealed classes with no added virtual or protected members as a great way to provide inexpensive yet much appreciated extensibility to a framework.</span></span>  
  
 <span data-ttu-id="3ab99-106">Os desenvolvedores geralmente desejam herdar de classes não seladas para adicionar membros de conveniência, como construtores personalizados, novos métodos ou sobrecargas de método.</span><span class="sxs-lookup"><span data-stu-id="3ab99-106">Developers often want to inherit from unsealed classes so as to add convenience members such as custom constructors, new methods, or method overloads.</span></span> <span data-ttu-id="3ab99-107">Por exemplo, `System.Messaging.MessageQueue` é sem lacre e, portanto, permite que os usuários criem filas personalizadas esse padrão para um caminho de fila particular ou adicione métodos personalizados que simplificam a API para cenários específicos.</span><span class="sxs-lookup"><span data-stu-id="3ab99-107">For example,  `System.Messaging.MessageQueue` is unsealed and thus allows users to create custom queues that default to a particular queue path or to add custom methods that simplify the API for specific scenarios.</span></span>  
  
 <span data-ttu-id="3ab99-108">As classes são sem lacre por padrão em linguagens de programação mais e isso também é o padrão recomendado para a maioria das classes em estruturas.</span><span class="sxs-lookup"><span data-stu-id="3ab99-108">Classes are unsealed by default in most programming languages, and this is also the recommended default for most classes in frameworks.</span></span> <span data-ttu-id="3ab99-109">A extensibilidade proporcionada pelo tipos sem lacre é muito apreciados por usuários da estrutura e muito barato para fornecer devido a custos relativamente baixo de teste associados a tipos sem lacre.</span><span class="sxs-lookup"><span data-stu-id="3ab99-109">The extensibility afforded by unsealed types is much appreciated by framework users and quite inexpensive to provide because of relatively low test costs associated with unsealed types.</span></span>  
  
 <span data-ttu-id="3ab99-110">*Portions © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*</span><span class="sxs-lookup"><span data-stu-id="3ab99-110">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="3ab99-111">*Reimpresso com permissão da Pearson Education, Inc. de [as diretrizes de Design do Framework: As convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicados 22 de outubro de 2008 pela Addison-Wesley Professional, como parte da série de desenvolvimento do Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="3ab99-111">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ab99-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3ab99-112">See also</span></span>

- [<span data-ttu-id="3ab99-113">Diretrizes de design do Framework</span><span class="sxs-lookup"><span data-stu-id="3ab99-113">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
- [<span data-ttu-id="3ab99-114">Designer voltado para extensibilidade</span><span class="sxs-lookup"><span data-stu-id="3ab99-114">Designing for Extensibility</span></span>](../../../docs/standard/design-guidelines/designing-for-extensibility.md)  
- [<span data-ttu-id="3ab99-115">Selar</span><span class="sxs-lookup"><span data-stu-id="3ab99-115">Sealing</span></span>](../../../docs/standard/design-guidelines/sealing.md)
