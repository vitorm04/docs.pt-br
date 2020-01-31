---
title: Usar tipos de exceção padrão
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- throwing exceptions, standard types
- catching exceptions
- exceptions, catching
- exceptions, throwing
ms.assetid: ab22ce03-78f9-4dca-8824-c7ed3bdccc27
ms.openlocfilehash: 3caa94d9a39966614161e4b19201dcf6065776a2
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743547"
---
# <a name="using-standard-exception-types"></a><span data-ttu-id="4702f-102">Usar tipos de exceção padrão</span><span class="sxs-lookup"><span data-stu-id="4702f-102">Using Standard Exception Types</span></span>
<span data-ttu-id="4702f-103">Esta seção descreve as exceções padrão fornecidas pela estrutura e os detalhes de seu uso.</span><span class="sxs-lookup"><span data-stu-id="4702f-103">This section describes the standard exceptions provided by the Framework and the details of their usage.</span></span> <span data-ttu-id="4702f-104">A lista não é, de maneira alguma, completa.</span><span class="sxs-lookup"><span data-stu-id="4702f-104">The list is by no means exhaustive.</span></span> <span data-ttu-id="4702f-105">Consulte a documentação de referência do .NET Framework para uso de outros tipos de exceção de estrutura.</span><span class="sxs-lookup"><span data-stu-id="4702f-105">Please refer to the .NET Framework reference documentation for usage of other Framework exception types.</span></span>

## <a name="exception-and-systemexception"></a><span data-ttu-id="4702f-106">Exception e SystemException</span><span class="sxs-lookup"><span data-stu-id="4702f-106">Exception and SystemException</span></span>
 <span data-ttu-id="4702f-107">❌ não lança <xref:System.Exception?displayProperty=nameWithType> ou <xref:System.SystemException?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="4702f-107">❌ DO NOT throw <xref:System.Exception?displayProperty=nameWithType> or <xref:System.SystemException?displayProperty=nameWithType>.</span></span>

 <span data-ttu-id="4702f-108">❌ não capturar `System.Exception` ou `System.SystemException` no código do Framework, a menos que você pretenda relançar.</span><span class="sxs-lookup"><span data-stu-id="4702f-108">❌ DO NOT catch `System.Exception` or `System.SystemException` in framework code, unless you intend to rethrow.</span></span>

 <span data-ttu-id="4702f-109">❌ evitar a captura de `System.Exception` ou `System.SystemException`, exceto em manipuladores de exceção de nível superior.</span><span class="sxs-lookup"><span data-stu-id="4702f-109">❌ AVOID catching `System.Exception` or `System.SystemException`, except in top-level exception handlers.</span></span>

## <a name="applicationexception"></a><span data-ttu-id="4702f-110">ApplicationException</span><span class="sxs-lookup"><span data-stu-id="4702f-110">ApplicationException</span></span>
 <span data-ttu-id="4702f-111">❌ não são lançadas ou derivam de <xref:System.ApplicationException>.</span><span class="sxs-lookup"><span data-stu-id="4702f-111">❌ DO NOT throw or derive from <xref:System.ApplicationException>.</span></span>

## <a name="invalidoperationexception"></a><span data-ttu-id="4702f-112">InvalidOperationException</span><span class="sxs-lookup"><span data-stu-id="4702f-112">InvalidOperationException</span></span>
 <span data-ttu-id="4702f-113">✔️ lançar um <xref:System.InvalidOperationException> se o objeto estiver em um estado inadequado.</span><span class="sxs-lookup"><span data-stu-id="4702f-113">✔️ DO throw an <xref:System.InvalidOperationException> if the object is in an inappropriate state.</span></span>

## <a name="argumentexception-argumentnullexception-and-argumentoutofrangeexception"></a><span data-ttu-id="4702f-114">ArgumentException, ArgumentNullException e ArgumentOutOfRangeException</span><span class="sxs-lookup"><span data-stu-id="4702f-114">ArgumentException, ArgumentNullException, and ArgumentOutOfRangeException</span></span>
 <span data-ttu-id="4702f-115">✔️ gerar <xref:System.ArgumentException> ou um de seus subtipos se argumentos inválidos forem passados para um membro.</span><span class="sxs-lookup"><span data-stu-id="4702f-115">✔️ DO throw <xref:System.ArgumentException> or one of its subtypes if bad arguments are passed to a member.</span></span> <span data-ttu-id="4702f-116">Prefira o tipo de exceção mais derivada, se aplicável.</span><span class="sxs-lookup"><span data-stu-id="4702f-116">Prefer the most derived exception type, if applicable.</span></span>

 <span data-ttu-id="4702f-117">✔️ Defina a propriedade `ParamName` ao lançar uma das subclasses de `ArgumentException`.</span><span class="sxs-lookup"><span data-stu-id="4702f-117">✔️ DO set the `ParamName` property when throwing one of the subclasses of `ArgumentException`.</span></span>

 <span data-ttu-id="4702f-118">Essa propriedade representa o nome do parâmetro que causou a geração da exceção.</span><span class="sxs-lookup"><span data-stu-id="4702f-118">This property represents the name of the parameter that caused the exception to be thrown.</span></span> <span data-ttu-id="4702f-119">Observe que a propriedade pode ser definida usando uma das sobrecargas do construtor.</span><span class="sxs-lookup"><span data-stu-id="4702f-119">Note that the property can be set using one of the constructor overloads.</span></span>

 <span data-ttu-id="4702f-120">✔️ Use `value` para o nome do parâmetro de valor implícito dos setters de propriedade.</span><span class="sxs-lookup"><span data-stu-id="4702f-120">✔️ DO use `value` for the name of the implicit value parameter of property setters.</span></span>

## <a name="nullreferenceexception-indexoutofrangeexception-and-accessviolationexception"></a><span data-ttu-id="4702f-121">NullReferenceException, IndexOutOfRangeException e AccessViolationException</span><span class="sxs-lookup"><span data-stu-id="4702f-121">NullReferenceException, IndexOutOfRangeException, and AccessViolationException</span></span>
 <span data-ttu-id="4702f-122">❌ não permitem que APIs que podem ser acessadas publicamente lancem <xref:System.NullReferenceException>, <xref:System.AccessViolationException>ou <xref:System.IndexOutOfRangeException>de forma explícita ou implícita.</span><span class="sxs-lookup"><span data-stu-id="4702f-122">❌ DO NOT allow publicly callable APIs to explicitly or implicitly throw <xref:System.NullReferenceException>, <xref:System.AccessViolationException>, or <xref:System.IndexOutOfRangeException>.</span></span> <span data-ttu-id="4702f-123">Essas exceções são reservadas e geradas pelo mecanismo de execução e, na maioria dos casos, indicam um bug.</span><span class="sxs-lookup"><span data-stu-id="4702f-123">These exceptions are reserved and thrown by the execution engine and in most cases indicate a bug.</span></span>

 <span data-ttu-id="4702f-124">Faça a verificação de argumento para evitar lançar essas exceções.</span><span class="sxs-lookup"><span data-stu-id="4702f-124">Do argument checking to avoid throwing these exceptions.</span></span> <span data-ttu-id="4702f-125">Lançar essas exceções expõe os detalhes de implementação do método que pode mudar ao longo do tempo.</span><span class="sxs-lookup"><span data-stu-id="4702f-125">Throwing these exceptions exposes implementation details of your method that might change over time.</span></span>

## <a name="stackoverflowexception"></a><span data-ttu-id="4702f-126">StackOverflowException</span><span class="sxs-lookup"><span data-stu-id="4702f-126">StackOverflowException</span></span>
 <span data-ttu-id="4702f-127">❌ não lançam <xref:System.StackOverflowException>explicitamente.</span><span class="sxs-lookup"><span data-stu-id="4702f-127">❌ DO NOT explicitly throw <xref:System.StackOverflowException>.</span></span> <span data-ttu-id="4702f-128">A exceção deve ser gerada explicitamente apenas pelo CLR.</span><span class="sxs-lookup"><span data-stu-id="4702f-128">The exception should be explicitly thrown only by the CLR.</span></span>

 <span data-ttu-id="4702f-129">❌ não capturar `StackOverflowException`.</span><span class="sxs-lookup"><span data-stu-id="4702f-129">❌ DO NOT catch `StackOverflowException`.</span></span>

 <span data-ttu-id="4702f-130">É quase impossível escrever código gerenciado que permaneça consistente na presença de estouros de pilha arbitrários.</span><span class="sxs-lookup"><span data-stu-id="4702f-130">It is almost impossible to write managed code that remains consistent in the presence of arbitrary stack overflows.</span></span> <span data-ttu-id="4702f-131">As partes não gerenciadas do CLR permanecem consistentes com o uso de investigações para mover estouros de pilha para locais bem definidos em vez de fazer backup de estouros de pilha arbitrários.</span><span class="sxs-lookup"><span data-stu-id="4702f-131">The unmanaged parts of the CLR remain consistent by using probes to move stack overflows to well-defined places rather than by backing out from arbitrary stack overflows.</span></span>

## <a name="outofmemoryexception"></a><span data-ttu-id="4702f-132">{1&gt;OutOfMemoryException&lt;1}</span><span class="sxs-lookup"><span data-stu-id="4702f-132">OutOfMemoryException</span></span>
 <span data-ttu-id="4702f-133">❌ não lançam <xref:System.OutOfMemoryException>explicitamente.</span><span class="sxs-lookup"><span data-stu-id="4702f-133">❌ DO NOT explicitly throw <xref:System.OutOfMemoryException>.</span></span> <span data-ttu-id="4702f-134">Essa exceção deve ser lançada apenas pela infraestrutura do CLR.</span><span class="sxs-lookup"><span data-stu-id="4702f-134">This exception is to be thrown only by the CLR infrastructure.</span></span>

## <a name="comexception-sehexception-and-executionengineexception"></a><span data-ttu-id="4702f-135">COMException, SEHException e ExecutionEngineException</span><span class="sxs-lookup"><span data-stu-id="4702f-135">ComException, SEHException, and ExecutionEngineException</span></span>
 <span data-ttu-id="4702f-136">❌ não lançam explicitamente <xref:System.Runtime.InteropServices.COMException>, <xref:System.ExecutionEngineException>e <xref:System.Runtime.InteropServices.SEHException>.</span><span class="sxs-lookup"><span data-stu-id="4702f-136">❌ DO NOT explicitly throw <xref:System.Runtime.InteropServices.COMException>,  <xref:System.ExecutionEngineException>, and <xref:System.Runtime.InteropServices.SEHException>.</span></span> <span data-ttu-id="4702f-137">Essas exceções devem ser lançadas apenas pela infraestrutura do CLR.</span><span class="sxs-lookup"><span data-stu-id="4702f-137">These exceptions are to be thrown only by the CLR infrastructure.</span></span>

 <span data-ttu-id="4702f-138">*Partes © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*</span><span class="sxs-lookup"><span data-stu-id="4702f-138">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="4702f-139">*Reimpresso com permissão da Pearson Education, Inc. das [Diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicado em 22 de outubro de 2008 por Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="4702f-139">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="4702f-140">Veja também</span><span class="sxs-lookup"><span data-stu-id="4702f-140">See also</span></span>

- [<span data-ttu-id="4702f-141">Diretrizes de design do Framework</span><span class="sxs-lookup"><span data-stu-id="4702f-141">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
- [<span data-ttu-id="4702f-142">Diretrizes de design para exceções</span><span class="sxs-lookup"><span data-stu-id="4702f-142">Design Guidelines for Exceptions</span></span>](../../../docs/standard/design-guidelines/exceptions.md)
