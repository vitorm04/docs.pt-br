---
title: "Lançando exceções"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- exceptions, throwing
- explicitly throwing exceptions
- throwing exceptions, design guidelines
ms.assetid: 5388e02b-52f5-460e-a2b5-eeafe60eeebe
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b1aa0eaccc26e1bd7cc6b78953dc0a782b2f952e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="exception-throwing"></a><span data-ttu-id="639b3-102">Lançando exceções</span><span class="sxs-lookup"><span data-stu-id="639b3-102">Exception Throwing</span></span>
<span data-ttu-id="639b3-103">Lançando exceções diretrizes descritas nesta seção exigem uma definição válida do significado da falha de execução.</span><span class="sxs-lookup"><span data-stu-id="639b3-103">Exception-throwing guidelines described in this section require a good definition of the meaning of execution failure.</span></span> <span data-ttu-id="639b3-104">Falha na execução ocorre sempre que um membro não é possível fazer o que ele foi projetado para fazer (o que o nome de membro implica).</span><span class="sxs-lookup"><span data-stu-id="639b3-104">Execution failure occurs whenever a member cannot do what it was designed to do (what the member name implies).</span></span> <span data-ttu-id="639b3-105">Por exemplo, se o `OpenFile` método não pode retornar um identificador de arquivo aberto ao chamador, ele será considerado uma falha na execução.</span><span class="sxs-lookup"><span data-stu-id="639b3-105">For example, if the `OpenFile` method cannot return an opened file handle to the caller, it would be considered an execution failure.</span></span>  
  
 <span data-ttu-id="639b3-106">A maioria dos desenvolvedores tornaram-se familiarizado com o uso de exceções para erros de uso como a divisão por zero ou referências nulas.</span><span class="sxs-lookup"><span data-stu-id="639b3-106">Most developers have become comfortable with using exceptions for usage errors such as division by zero or null references.</span></span> <span data-ttu-id="639b3-107">Na estrutura, as exceções são usadas para todas as condições de erro, incluindo erros de execução.</span><span class="sxs-lookup"><span data-stu-id="639b3-107">In the Framework, exceptions are used for all error conditions, including execution errors.</span></span>  
  
 <span data-ttu-id="639b3-108">**X não** retornar códigos de erro.</span><span class="sxs-lookup"><span data-stu-id="639b3-108">**X DO NOT** return error codes.</span></span>  
  
 <span data-ttu-id="639b3-109">As exceções são o principal meio de relatório de erros em estruturas.</span><span class="sxs-lookup"><span data-stu-id="639b3-109">Exceptions are the primary means of reporting errors in frameworks.</span></span>  
  
 <span data-ttu-id="639b3-110">**FAZER ✓** falhas de execução de relatório por Lançando exceções.</span><span class="sxs-lookup"><span data-stu-id="639b3-110">**✓ DO** report execution failures by throwing exceptions.</span></span>  
  
 <span data-ttu-id="639b3-111">**✓ CONSIDERE** finalizando o processo chamando `System.Environment.FailFast` (recurso do .NET Framework 2.0) em vez de gerar uma exceção se o seu código encontrar uma situação em que não é seguro para execução ainda mais.</span><span class="sxs-lookup"><span data-stu-id="639b3-111">**✓ CONSIDER** terminating the process by calling `System.Environment.FailFast` (.NET Framework 2.0 feature) instead of throwing an exception if your code encounters a situation where it is unsafe for further execution.</span></span>  
  
 <span data-ttu-id="639b3-112">**X não** use exceções para o fluxo normal de controle, se possível.</span><span class="sxs-lookup"><span data-stu-id="639b3-112">**X DO NOT** use exceptions for the normal flow of control, if possible.</span></span>  
  
 <span data-ttu-id="639b3-113">Exceto para operações com condições de corrida potenciais e falhas de sistema, designers de estrutura devem projetar APIs para que os usuários podem gravar código que não lançam exceções.</span><span class="sxs-lookup"><span data-stu-id="639b3-113">Except for system failures and operations with potential race conditions, framework designers should design APIs so users can write code that does not throw exceptions.</span></span> <span data-ttu-id="639b3-114">Por exemplo, você pode fornecer uma maneira de verificar pré-condições antes de chamar um membro para que os usuários podem gravar código que não lançam exceções.</span><span class="sxs-lookup"><span data-stu-id="639b3-114">For example, you can provide a way to check preconditions before calling a member so users can write code that does not throw exceptions.</span></span>  
  
 <span data-ttu-id="639b3-115">O membro usado para verificar as pré-condições de outro membro é conhecido como um testador e o membro que realmente executa o trabalho é chamado um mal-intencionado.</span><span class="sxs-lookup"><span data-stu-id="639b3-115">The member used to check preconditions of another member is often referred to as a tester, and the member that actually does the work is called a doer.</span></span>  
  
 <span data-ttu-id="639b3-116">Há casos em que o padrão de testador mal-intencionado pode ter uma sobrecarga de desempenho inaceitável.</span><span class="sxs-lookup"><span data-stu-id="639b3-116">There are cases when the Tester-Doer Pattern can have an unacceptable performance overhead.</span></span> <span data-ttu-id="639b3-117">Nesses casos, o padrão de análise de tente chamados devem ser considerado (consulte [exceções e desempenho](../../../docs/standard/design-guidelines/exceptions-and-performance.md) para obter mais informações).</span><span class="sxs-lookup"><span data-stu-id="639b3-117">In such cases, the so-called Try-Parse Pattern should be considered (see [Exceptions and Performance](../../../docs/standard/design-guidelines/exceptions-and-performance.md) for more information).</span></span>  
  
 <span data-ttu-id="639b3-118">**✓ CONSIDERE** as implicações de desempenho de Lançando exceções.</span><span class="sxs-lookup"><span data-stu-id="639b3-118">**✓ CONSIDER** the performance implications of throwing exceptions.</span></span> <span data-ttu-id="639b3-119">As taxas de throw acima de 100 por segundo estão provavelmente visivelmente afetar o desempenho da maioria dos aplicativos.</span><span class="sxs-lookup"><span data-stu-id="639b3-119">Throw rates above 100 per second are likely to noticeably impact the performance of most applications.</span></span>  
  
 <span data-ttu-id="639b3-120">**FAZER ✓** documento todas as exceções lançadas por membros publicamente acessível devido a uma violação do membro (em vez de uma falha do sistema) do contrato e tratá-los como parte de seu contrato.</span><span class="sxs-lookup"><span data-stu-id="639b3-120">**✓ DO** document all exceptions thrown by publicly callable members because of a violation of the member contract (rather than a system failure) and treat them as part of your contract.</span></span>  
  
 <span data-ttu-id="639b3-121">Exceções que fazem parte do contrato não devem alterar de uma versão para a próxima (ou seja, não deve alterar o tipo de exceção e não devem ser adicionadas novas exceções).</span><span class="sxs-lookup"><span data-stu-id="639b3-121">Exceptions that are a part of the contract should not change from one version to the next (i.e., exception type should not change, and new exceptions should not be added).</span></span>  
  
 <span data-ttu-id="639b3-122">**X não** tem membros públicos que podem ou throw ou não com base em alguma opção.</span><span class="sxs-lookup"><span data-stu-id="639b3-122">**X DO NOT** have public members that can either throw or not based on some option.</span></span>  
  
 <span data-ttu-id="639b3-123">**X não** tem membros públicos que retornam exceções como o valor de retorno ou um `out` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="639b3-123">**X DO NOT** have public members that return exceptions as the return value or an `out` parameter.</span></span>  
  
 <span data-ttu-id="639b3-124">Retornando exceções de APIs públicas, em vez de lançá-las anula a muitos dos benefícios do relatório de erros com base em exceções.</span><span class="sxs-lookup"><span data-stu-id="639b3-124">Returning exceptions from public APIs instead of throwing them defeats many of the benefits of exception-based error reporting.</span></span>  
  
 <span data-ttu-id="639b3-125">**✓ CONSIDERE** usando métodos de construtor de exceção.</span><span class="sxs-lookup"><span data-stu-id="639b3-125">**✓ CONSIDER** using exception builder methods.</span></span>  
  
 <span data-ttu-id="639b3-126">É comum para lançar a mesma exceção de diferentes locais.</span><span class="sxs-lookup"><span data-stu-id="639b3-126">It is common to throw the same exception from different places.</span></span> <span data-ttu-id="639b3-127">Para evitar inchaço de código, use os métodos auxiliares que criar exceções e inicializam suas propriedades.</span><span class="sxs-lookup"><span data-stu-id="639b3-127">To avoid code bloat, use helper methods that create exceptions and initialize their properties.</span></span>  
  
 <span data-ttu-id="639b3-128">Além disso, os membros que lançam exceções não estão obtendo embutida.</span><span class="sxs-lookup"><span data-stu-id="639b3-128">Also, members that throw exceptions are not getting inlined.</span></span> <span data-ttu-id="639b3-129">Movendo a instrução throw dentro de construtor pode permitir que o membro a ser embutido.</span><span class="sxs-lookup"><span data-stu-id="639b3-129">Moving the throw statement inside the builder might allow the member to be inlined.</span></span>  
  
 <span data-ttu-id="639b3-130">**X não** lançam exceções em blocos de filtro de exceção.</span><span class="sxs-lookup"><span data-stu-id="639b3-130">**X DO NOT** throw exceptions from exception filter blocks.</span></span>  
  
 <span data-ttu-id="639b3-131">Quando um filtro de exceção gera uma exceção, a exceção é capturada pelo CLR e o filtro retorna false.</span><span class="sxs-lookup"><span data-stu-id="639b3-131">When an exception filter raises an exception, the exception is caught by the CLR, and the filter returns false.</span></span> <span data-ttu-id="639b3-132">Esse comportamento não é possível distinguir do filtro de execução e retornar false explicitamente e, portanto, é muito difícil de depurar.</span><span class="sxs-lookup"><span data-stu-id="639b3-132">This behavior is indistinguishable from the filter executing and returning false explicitly and is therefore very difficult to debug.</span></span>  
  
 <span data-ttu-id="639b3-133">**X Evite** explicitamente Lançando exceções a partir de blocos finally.</span><span class="sxs-lookup"><span data-stu-id="639b3-133">**X AVOID** explicitly throwing exceptions from finally blocks.</span></span> <span data-ttu-id="639b3-134">Exceções implicitamente geradas resultante da chamada de métodos que lançam são aceitáveis.</span><span class="sxs-lookup"><span data-stu-id="639b3-134">Implicitly thrown exceptions resulting from calling methods that throw are acceptable.</span></span>  
  
 <span data-ttu-id="639b3-135">*Partes © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*</span><span class="sxs-lookup"><span data-stu-id="639b3-135">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="639b3-136">*Reimpressas pela permissão de Pearson educação, Inc. de [diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicados 22 de outubro de 2008, Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="639b3-136">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="639b3-137">Consulte também</span><span class="sxs-lookup"><span data-stu-id="639b3-137">See Also</span></span>  
 [<span data-ttu-id="639b3-138">Diretrizes de design do Framework</span><span class="sxs-lookup"><span data-stu-id="639b3-138">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
 [<span data-ttu-id="639b3-139">Diretrizes de design para exceções</span><span class="sxs-lookup"><span data-stu-id="639b3-139">Design Guidelines for Exceptions</span></span>](../../../docs/standard/design-guidelines/exceptions.md)
