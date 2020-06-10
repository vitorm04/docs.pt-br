---
title: Usar tipos de exceção padrão
description: Leia sobre os tipos de exceção padrão no .NET. Saiba mais sobre o SystemException, o ApplicationException, o ArgumentException, o COMException e muito mais.
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- throwing exceptions, standard types
- catching exceptions
- exceptions, catching
- exceptions, throwing
ms.assetid: ab22ce03-78f9-4dca-8824-c7ed3bdccc27
ms.openlocfilehash: f95529eabd87d9ec7c379b9f790e039e1192ac53
ms.sourcegitcommit: 7137e12f54c4e83a94ae43ec320f8cf59c1772ea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/10/2020
ms.locfileid: "84663051"
---
# <a name="using-standard-exception-types"></a><span data-ttu-id="fab62-104">Usar tipos de exceção padrão</span><span class="sxs-lookup"><span data-stu-id="fab62-104">Using Standard Exception Types</span></span>
<span data-ttu-id="fab62-105">Esta seção descreve as exceções padrão fornecidas pela estrutura e os detalhes de seu uso.</span><span class="sxs-lookup"><span data-stu-id="fab62-105">This section describes the standard exceptions provided by the Framework and the details of their usage.</span></span> <span data-ttu-id="fab62-106">A lista não é, de maneira alguma, completa.</span><span class="sxs-lookup"><span data-stu-id="fab62-106">The list is by no means exhaustive.</span></span> <span data-ttu-id="fab62-107">Consulte a documentação de referência do .NET Framework para uso de outros tipos de exceção de estrutura.</span><span class="sxs-lookup"><span data-stu-id="fab62-107">Please refer to the .NET Framework reference documentation for usage of other Framework exception types.</span></span>

## <a name="exception-and-systemexception"></a><span data-ttu-id="fab62-108">Exception e SystemException</span><span class="sxs-lookup"><span data-stu-id="fab62-108">Exception and SystemException</span></span>
 <span data-ttu-id="fab62-109">❌Não lançar <xref:System.Exception?displayProperty=nameWithType> ou <xref:System.SystemException?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="fab62-109">❌ DO NOT throw <xref:System.Exception?displayProperty=nameWithType> or <xref:System.SystemException?displayProperty=nameWithType>.</span></span>

 <span data-ttu-id="fab62-110">❌Não pegue `System.Exception` nem `System.SystemException` no código de estrutura, a menos que você pretenda relançar.</span><span class="sxs-lookup"><span data-stu-id="fab62-110">❌ DO NOT catch `System.Exception` or `System.SystemException` in framework code, unless you intend to rethrow.</span></span>

 <span data-ttu-id="fab62-111">❌Evite capturar `System.Exception` ou `System.SystemException` , exceto em manipuladores de exceção de nível superior.</span><span class="sxs-lookup"><span data-stu-id="fab62-111">❌ AVOID catching `System.Exception` or `System.SystemException`, except in top-level exception handlers.</span></span>

## <a name="applicationexception"></a><span data-ttu-id="fab62-112">ApplicationException</span><span class="sxs-lookup"><span data-stu-id="fab62-112">ApplicationException</span></span>
 <span data-ttu-id="fab62-113">❌NÃO lançar ou derivar de <xref:System.ApplicationException> .</span><span class="sxs-lookup"><span data-stu-id="fab62-113">❌ DO NOT throw or derive from <xref:System.ApplicationException>.</span></span>

## <a name="invalidoperationexception"></a><span data-ttu-id="fab62-114">InvalidOperationException</span><span class="sxs-lookup"><span data-stu-id="fab62-114">InvalidOperationException</span></span>
 <span data-ttu-id="fab62-115">✔️ gerar um <xref:System.InvalidOperationException> se o objeto estiver em um estado inadequado.</span><span class="sxs-lookup"><span data-stu-id="fab62-115">✔️ DO throw an <xref:System.InvalidOperationException> if the object is in an inappropriate state.</span></span>

## <a name="argumentexception-argumentnullexception-and-argumentoutofrangeexception"></a><span data-ttu-id="fab62-116">ArgumentException, ArgumentNullException e ArgumentOutOfRangeException</span><span class="sxs-lookup"><span data-stu-id="fab62-116">ArgumentException, ArgumentNullException, and ArgumentOutOfRangeException</span></span>
 <span data-ttu-id="fab62-117">✔️ gerar <xref:System.ArgumentException> ou um de seus subtipos se argumentos inválidos forem passados para um membro.</span><span class="sxs-lookup"><span data-stu-id="fab62-117">✔️ DO throw <xref:System.ArgumentException> or one of its subtypes if bad arguments are passed to a member.</span></span> <span data-ttu-id="fab62-118">Prefira o tipo de exceção mais derivada, se aplicável.</span><span class="sxs-lookup"><span data-stu-id="fab62-118">Prefer the most derived exception type, if applicable.</span></span>

 <span data-ttu-id="fab62-119">✔️ definir a `ParamName` propriedade ao lançar uma das subclasses de `ArgumentException` .</span><span class="sxs-lookup"><span data-stu-id="fab62-119">✔️ DO set the `ParamName` property when throwing one of the subclasses of `ArgumentException`.</span></span>

 <span data-ttu-id="fab62-120">Essa propriedade representa o nome do parâmetro que causou a geração da exceção.</span><span class="sxs-lookup"><span data-stu-id="fab62-120">This property represents the name of the parameter that caused the exception to be thrown.</span></span> <span data-ttu-id="fab62-121">Observe que a propriedade pode ser definida usando uma das sobrecargas do construtor.</span><span class="sxs-lookup"><span data-stu-id="fab62-121">Note that the property can be set using one of the constructor overloads.</span></span>

 <span data-ttu-id="fab62-122">✔️ Use `value` para o nome do parâmetro de valor implícito dos setters de propriedade.</span><span class="sxs-lookup"><span data-stu-id="fab62-122">✔️ DO use `value` for the name of the implicit value parameter of property setters.</span></span>

## <a name="nullreferenceexception-indexoutofrangeexception-and-accessviolationexception"></a><span data-ttu-id="fab62-123">NullReferenceException, IndexOutOfRangeException e AccessViolationException</span><span class="sxs-lookup"><span data-stu-id="fab62-123">NullReferenceException, IndexOutOfRangeException, and AccessViolationException</span></span>
 <span data-ttu-id="fab62-124">❌Não permita que as APIs que podem ser chamadas publicamente lancem <xref:System.NullReferenceException> , <xref:System.AccessViolationException> , ou <xref:System.IndexOutOfRangeException> .</span><span class="sxs-lookup"><span data-stu-id="fab62-124">❌ DO NOT allow publicly callable APIs to explicitly or implicitly throw <xref:System.NullReferenceException>, <xref:System.AccessViolationException>, or <xref:System.IndexOutOfRangeException>.</span></span> <span data-ttu-id="fab62-125">Essas exceções são reservadas e geradas pelo mecanismo de execução e, na maioria dos casos, indicam um bug.</span><span class="sxs-lookup"><span data-stu-id="fab62-125">These exceptions are reserved and thrown by the execution engine and in most cases indicate a bug.</span></span>

 <span data-ttu-id="fab62-126">Faça a verificação de argumento para evitar lançar essas exceções.</span><span class="sxs-lookup"><span data-stu-id="fab62-126">Do argument checking to avoid throwing these exceptions.</span></span> <span data-ttu-id="fab62-127">Lançar essas exceções expõe os detalhes de implementação do método que pode mudar ao longo do tempo.</span><span class="sxs-lookup"><span data-stu-id="fab62-127">Throwing these exceptions exposes implementation details of your method that might change over time.</span></span>

## <a name="stackoverflowexception"></a><span data-ttu-id="fab62-128">StackOverflowException</span><span class="sxs-lookup"><span data-stu-id="fab62-128">StackOverflowException</span></span>
 <span data-ttu-id="fab62-129">❌Não lance explicitamente <xref:System.StackOverflowException> .</span><span class="sxs-lookup"><span data-stu-id="fab62-129">❌ DO NOT explicitly throw <xref:System.StackOverflowException>.</span></span> <span data-ttu-id="fab62-130">A exceção deve ser gerada explicitamente apenas pelo CLR.</span><span class="sxs-lookup"><span data-stu-id="fab62-130">The exception should be explicitly thrown only by the CLR.</span></span>

 <span data-ttu-id="fab62-131">❌Não Catch `StackOverflowException` .</span><span class="sxs-lookup"><span data-stu-id="fab62-131">❌ DO NOT catch `StackOverflowException`.</span></span>

 <span data-ttu-id="fab62-132">É quase impossível escrever código gerenciado que permaneça consistente na presença de estouros de pilha arbitrários.</span><span class="sxs-lookup"><span data-stu-id="fab62-132">It is almost impossible to write managed code that remains consistent in the presence of arbitrary stack overflows.</span></span> <span data-ttu-id="fab62-133">As partes não gerenciadas do CLR permanecem consistentes com o uso de investigações para mover estouros de pilha para locais bem definidos em vez de fazer backup de estouros de pilha arbitrários.</span><span class="sxs-lookup"><span data-stu-id="fab62-133">The unmanaged parts of the CLR remain consistent by using probes to move stack overflows to well-defined places rather than by backing out from arbitrary stack overflows.</span></span>

## <a name="outofmemoryexception"></a><span data-ttu-id="fab62-134">OutOfMemoryException</span><span class="sxs-lookup"><span data-stu-id="fab62-134">OutOfMemoryException</span></span>
 <span data-ttu-id="fab62-135">❌Não lance explicitamente <xref:System.OutOfMemoryException> .</span><span class="sxs-lookup"><span data-stu-id="fab62-135">❌ DO NOT explicitly throw <xref:System.OutOfMemoryException>.</span></span> <span data-ttu-id="fab62-136">Essa exceção deve ser lançada apenas pela infraestrutura do CLR.</span><span class="sxs-lookup"><span data-stu-id="fab62-136">This exception is to be thrown only by the CLR infrastructure.</span></span>

## <a name="comexception-sehexception-and-executionengineexception"></a><span data-ttu-id="fab62-137">COMException, SEHException e ExecutionEngineException</span><span class="sxs-lookup"><span data-stu-id="fab62-137">ComException, SEHException, and ExecutionEngineException</span></span>
 <span data-ttu-id="fab62-138">❌Não lance explicitamente <xref:System.Runtime.InteropServices.COMException> , <xref:System.ExecutionEngineException> , e <xref:System.Runtime.InteropServices.SEHException> .</span><span class="sxs-lookup"><span data-stu-id="fab62-138">❌ DO NOT explicitly throw <xref:System.Runtime.InteropServices.COMException>,  <xref:System.ExecutionEngineException>, and <xref:System.Runtime.InteropServices.SEHException>.</span></span> <span data-ttu-id="fab62-139">Essas exceções devem ser lançadas apenas pela infraestrutura do CLR.</span><span class="sxs-lookup"><span data-stu-id="fab62-139">These exceptions are to be thrown only by the CLR infrastructure.</span></span>

 <span data-ttu-id="fab62-140">*Partes © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*</span><span class="sxs-lookup"><span data-stu-id="fab62-140">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="fab62-141">*Reimpresso com permissão da Pearson Education, Inc. das [Diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicado em 22 de outubro de 2008 por Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="fab62-141">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="fab62-142">Confira também</span><span class="sxs-lookup"><span data-stu-id="fab62-142">See also</span></span>

- [<span data-ttu-id="fab62-143">Diretrizes de design de estrutura</span><span class="sxs-lookup"><span data-stu-id="fab62-143">Framework Design Guidelines</span></span>](index.md)
- [<span data-ttu-id="fab62-144">Diretrizes de design para exceções</span><span class="sxs-lookup"><span data-stu-id="fab62-144">Design Guidelines for Exceptions</span></span>](exceptions.md)
