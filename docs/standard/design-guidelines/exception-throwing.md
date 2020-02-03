---
title: Gerar exceções
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- exceptions, throwing
- explicitly throwing exceptions
- throwing exceptions, design guidelines
ms.assetid: 5388e02b-52f5-460e-a2b5-eeafe60eeebe
ms.openlocfilehash: 18927d242c2ed957d2bc9f8b481beeed775a4e4e
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741670"
---
# <a name="exception-throwing"></a><span data-ttu-id="7c915-102">Gerar exceções</span><span class="sxs-lookup"><span data-stu-id="7c915-102">Exception Throwing</span></span>
<span data-ttu-id="7c915-103">As diretrizes de lançamento de exceção descritas nesta seção exigem uma boa definição do significado da falha de execução.</span><span class="sxs-lookup"><span data-stu-id="7c915-103">Exception-throwing guidelines described in this section require a good definition of the meaning of execution failure.</span></span> <span data-ttu-id="7c915-104">A falha de execução ocorre sempre que um membro não pode fazer o que foi projetado (o que o nome do membro implica).</span><span class="sxs-lookup"><span data-stu-id="7c915-104">Execution failure occurs whenever a member cannot do what it was designed to do (what the member name implies).</span></span> <span data-ttu-id="7c915-105">Por exemplo, se o método `OpenFile` não puder retornar um identificador de arquivo aberto para o chamador, ele será considerado uma falha de execução.</span><span class="sxs-lookup"><span data-stu-id="7c915-105">For example, if the `OpenFile` method cannot return an opened file handle to the caller, it would be considered an execution failure.</span></span>

 <span data-ttu-id="7c915-106">A maioria dos desenvolvedores se sente confortável com o uso de exceções para erros de uso, como divisão por zero ou referências nulas.</span><span class="sxs-lookup"><span data-stu-id="7c915-106">Most developers have become comfortable with using exceptions for usage errors such as division by zero or null references.</span></span> <span data-ttu-id="7c915-107">Na estrutura, as exceções são usadas para todas as condições de erro, incluindo erros de execução.</span><span class="sxs-lookup"><span data-stu-id="7c915-107">In the Framework, exceptions are used for all error conditions, including execution errors.</span></span>

 <span data-ttu-id="7c915-108">❌ não retornar códigos de erro.</span><span class="sxs-lookup"><span data-stu-id="7c915-108">❌ DO NOT return error codes.</span></span>

 <span data-ttu-id="7c915-109">As exceções são os principais meios de relatar erros em estruturas.</span><span class="sxs-lookup"><span data-stu-id="7c915-109">Exceptions are the primary means of reporting errors in frameworks.</span></span>

 <span data-ttu-id="7c915-110">✔️ as falhas de execução de relatório lançando exceções.</span><span class="sxs-lookup"><span data-stu-id="7c915-110">✔️ DO report execution failures by throwing exceptions.</span></span>

 <span data-ttu-id="7c915-111">✔️ Considere encerrar o processo chamando `System.Environment.FailFast` (recurso .NET Framework 2,0) em vez de lançar uma exceção se o seu código encontrar uma situação em que ela não é segura para execução posterior.</span><span class="sxs-lookup"><span data-stu-id="7c915-111">✔️ CONSIDER terminating the process by calling `System.Environment.FailFast` (.NET Framework 2.0 feature) instead of throwing an exception if your code encounters a situation where it is unsafe for further execution.</span></span>

 <span data-ttu-id="7c915-112">❌ não use exceções para o fluxo normal de controle, se possível.</span><span class="sxs-lookup"><span data-stu-id="7c915-112">❌ DO NOT use exceptions for the normal flow of control, if possible.</span></span>

 <span data-ttu-id="7c915-113">Exceto para falhas do sistema e operações com possíveis condições de corrida, os designers de estrutura devem criar APIs para que os usuários possam escrever código que não gere exceções.</span><span class="sxs-lookup"><span data-stu-id="7c915-113">Except for system failures and operations with potential race conditions, framework designers should design APIs so users can write code that does not throw exceptions.</span></span> <span data-ttu-id="7c915-114">Por exemplo, você pode fornecer uma maneira de verificar as pré-condições antes de chamar um membro para que os usuários possam escrever código que não gere exceções.</span><span class="sxs-lookup"><span data-stu-id="7c915-114">For example, you can provide a way to check preconditions before calling a member so users can write code that does not throw exceptions.</span></span>

 <span data-ttu-id="7c915-115">O membro usado para verificar as pré-condições de outro membro é geralmente chamado de testador, e o membro que realmente faz o trabalho é chamado de doer.</span><span class="sxs-lookup"><span data-stu-id="7c915-115">The member used to check preconditions of another member is often referred to as a tester, and the member that actually does the work is called a doer.</span></span>

 <span data-ttu-id="7c915-116">Há casos em que o padrão do testador-doer pode ter uma sobrecarga de desempenho inaceitável.</span><span class="sxs-lookup"><span data-stu-id="7c915-116">There are cases when the Tester-Doer Pattern can have an unacceptable performance overhead.</span></span> <span data-ttu-id="7c915-117">Nesses casos, o chamado padrão de teste de tentativa-análise deve ser considerado (consulte [exceções e desempenho](../../../docs/standard/design-guidelines/exceptions-and-performance.md) para obter mais informações).</span><span class="sxs-lookup"><span data-stu-id="7c915-117">In such cases, the so-called Try-Parse Pattern should be considered (see [Exceptions and Performance](../../../docs/standard/design-guidelines/exceptions-and-performance.md) for more information).</span></span>

 <span data-ttu-id="7c915-118">✔️ CONSIDERAR as implicações de desempenho do lançamento de exceções.</span><span class="sxs-lookup"><span data-stu-id="7c915-118">✔️ CONSIDER the performance implications of throwing exceptions.</span></span> <span data-ttu-id="7c915-119">As taxas de geração acima de 100 por segundo provavelmente afetarão notavelmente o desempenho da maioria dos aplicativos.</span><span class="sxs-lookup"><span data-stu-id="7c915-119">Throw rates above 100 per second are likely to noticeably impact the performance of most applications.</span></span>

 <span data-ttu-id="7c915-120">✔️ FAZER o documento de todas as exceções geradas por membros que podem ser chamados publicamente devido a uma violação do contrato de membro (em vez de uma falha do sistema) e tratá-los como parte de seu contrato.</span><span class="sxs-lookup"><span data-stu-id="7c915-120">✔️ DO document all exceptions thrown by publicly callable members because of a violation of the member contract (rather than a system failure) and treat them as part of your contract.</span></span>

 <span data-ttu-id="7c915-121">As exceções que fazem parte do contrato não devem ser alteradas de uma versão para a seguinte (isto é, o tipo de exceção não deve ser alterado e novas exceções não devem ser adicionadas).</span><span class="sxs-lookup"><span data-stu-id="7c915-121">Exceptions that are a part of the contract should not change from one version to the next (i.e., exception type should not change, and new exceptions should not be added).</span></span>

 <span data-ttu-id="7c915-122">❌ não têm membros públicos que podem ser acionados ou não com base em alguma opção.</span><span class="sxs-lookup"><span data-stu-id="7c915-122">❌ DO NOT have public members that can either throw or not based on some option.</span></span>

 <span data-ttu-id="7c915-123">❌ não têm membros públicos que retornam exceções como o valor de retorno ou um parâmetro `out`.</span><span class="sxs-lookup"><span data-stu-id="7c915-123">❌ DO NOT have public members that return exceptions as the return value or an `out` parameter.</span></span>

 <span data-ttu-id="7c915-124">Retornar exceções de APIs públicas em vez de lançá-las derrota muitos dos benefícios do relatório de erros baseado em exceção.</span><span class="sxs-lookup"><span data-stu-id="7c915-124">Returning exceptions from public APIs instead of throwing them defeats many of the benefits of exception-based error reporting.</span></span>

 <span data-ttu-id="7c915-125">✔️ Considere o uso de métodos do construtor de exceções.</span><span class="sxs-lookup"><span data-stu-id="7c915-125">✔️ CONSIDER using exception builder methods.</span></span>

 <span data-ttu-id="7c915-126">É comum lançar a mesma exceção de locais diferentes.</span><span class="sxs-lookup"><span data-stu-id="7c915-126">It is common to throw the same exception from different places.</span></span> <span data-ttu-id="7c915-127">Para evitar o excesso de código, use métodos auxiliares que criam exceções e inicializam suas propriedades.</span><span class="sxs-lookup"><span data-stu-id="7c915-127">To avoid code bloat, use helper methods that create exceptions and initialize their properties.</span></span>

 <span data-ttu-id="7c915-128">Além disso, os membros que lançam exceções não estão ficando embutidos.</span><span class="sxs-lookup"><span data-stu-id="7c915-128">Also, members that throw exceptions are not getting inlined.</span></span> <span data-ttu-id="7c915-129">Mover a instrução Throw dentro do construtor pode permitir que o membro seja embutido.</span><span class="sxs-lookup"><span data-stu-id="7c915-129">Moving the throw statement inside the builder might allow the member to be inlined.</span></span>

 <span data-ttu-id="7c915-130">❌ não lançam exceções de blocos de filtro de exceção.</span><span class="sxs-lookup"><span data-stu-id="7c915-130">❌ DO NOT throw exceptions from exception filter blocks.</span></span>

 <span data-ttu-id="7c915-131">Quando um filtro de exceção gera uma exceção, a exceção é capturada pelo CLR e o filtro retorna falso.</span><span class="sxs-lookup"><span data-stu-id="7c915-131">When an exception filter raises an exception, the exception is caught by the CLR, and the filter returns false.</span></span> <span data-ttu-id="7c915-132">Esse comportamento é indistinguíveis do filtro executando e retornando false explicitamente e, portanto, é muito difícil de depurar.</span><span class="sxs-lookup"><span data-stu-id="7c915-132">This behavior is indistinguishable from the filter executing and returning false explicitly and is therefore very difficult to debug.</span></span>

 <span data-ttu-id="7c915-133">❌ evitar gerar exceções explicitamente de blocos finally.</span><span class="sxs-lookup"><span data-stu-id="7c915-133">❌ AVOID explicitly throwing exceptions from finally blocks.</span></span> <span data-ttu-id="7c915-134">Exceções implicitamente geradas resultantes de métodos de chamada que geram são aceitáveis.</span><span class="sxs-lookup"><span data-stu-id="7c915-134">Implicitly thrown exceptions resulting from calling methods that throw are acceptable.</span></span>

 <span data-ttu-id="7c915-135">*Partes © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*</span><span class="sxs-lookup"><span data-stu-id="7c915-135">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="7c915-136">*Reimpresso com permissão da Pearson Education, Inc. das [Diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicado em 22 de outubro de 2008 por Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="7c915-136">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="7c915-137">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7c915-137">See also</span></span>

- [<span data-ttu-id="7c915-138">Diretrizes de design do Framework</span><span class="sxs-lookup"><span data-stu-id="7c915-138">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
- [<span data-ttu-id="7c915-139">Diretrizes de design para exceções</span><span class="sxs-lookup"><span data-stu-id="7c915-139">Design Guidelines for Exceptions</span></span>](../../../docs/standard/design-guidelines/exceptions.md)
