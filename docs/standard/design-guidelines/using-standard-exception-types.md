---
title: "Usando tipos de exceção padrão"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- throwing exceptions, standard types
- catching exceptions
- exceptions, catching
- exceptions, throwing
ms.assetid: ab22ce03-78f9-4dca-8824-c7ed3bdccc27
caps.latest.revision: "17"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 91cd9a03ad1acf61681ecfad0edb061802c4362c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="using-standard-exception-types"></a><span data-ttu-id="a1764-102">Usando tipos de exceção padrão</span><span class="sxs-lookup"><span data-stu-id="a1764-102">Using Standard Exception Types</span></span>
<span data-ttu-id="a1764-103">Esta seção descreve as exceções padrão fornecidas pela estrutura e os detalhes de uso.</span><span class="sxs-lookup"><span data-stu-id="a1764-103">This section describes the standard exceptions provided by the Framework and the details of their usage.</span></span> <span data-ttu-id="a1764-104">A lista não é exaustiva.</span><span class="sxs-lookup"><span data-stu-id="a1764-104">The list is by no means exhaustive.</span></span> <span data-ttu-id="a1764-105">Consulte a documentação de referência do .NET Framework para o uso de outros tipos de exceção do Framework.</span><span class="sxs-lookup"><span data-stu-id="a1764-105">Please refer to the .NET Framework reference documentation for usage of other Framework exception types.</span></span>  
  
## <a name="exception-and-systemexception"></a><span data-ttu-id="a1764-106">Exceção e SystemException</span><span class="sxs-lookup"><span data-stu-id="a1764-106">Exception and SystemException</span></span>  
 <span data-ttu-id="a1764-107">**X não** gerar <xref:System.Exception?displayProperty=nameWithType> ou <xref:System.SystemException?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="a1764-107">**X DO NOT** throw <xref:System.Exception?displayProperty=nameWithType> or <xref:System.SystemException?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="a1764-108">**X não** catch `System.Exception` ou `System.SystemException` no código do framework, a menos que você pretende relançar.</span><span class="sxs-lookup"><span data-stu-id="a1764-108">**X DO NOT** catch `System.Exception` or `System.SystemException` in framework code, unless you intend to rethrow.</span></span>  
  
 <span data-ttu-id="a1764-109">**X Evite** capturando `System.Exception` ou `System.SystemException`, exceto em manipuladores de exceção de nível superior.</span><span class="sxs-lookup"><span data-stu-id="a1764-109">**X AVOID** catching `System.Exception` or `System.SystemException`, except in top-level exception handlers.</span></span>  
  
## <a name="applicationexception"></a><span data-ttu-id="a1764-110">ApplicationException</span><span class="sxs-lookup"><span data-stu-id="a1764-110">ApplicationException</span></span>  
 <span data-ttu-id="a1764-111">**X não** lançar ou derivam de <xref:System.ApplicationException>.</span><span class="sxs-lookup"><span data-stu-id="a1764-111">**X DO NOT** throw or derive from <xref:System.ApplicationException>.</span></span>  
  
## <a name="invalidoperationexception"></a><span data-ttu-id="a1764-112">InvalidOperationException</span><span class="sxs-lookup"><span data-stu-id="a1764-112">InvalidOperationException</span></span>  
 <span data-ttu-id="a1764-113">**FAZER ✓** lançar um <xref:System.InvalidOperationException> se o objeto está em um estado inadequado.</span><span class="sxs-lookup"><span data-stu-id="a1764-113">**✓ DO** throw an <xref:System.InvalidOperationException> if the object is in an inappropriate state.</span></span>  
  
## <a name="argumentexception-argumentnullexception-and-argumentoutofrangeexception"></a><span data-ttu-id="a1764-114">ArgumentException ArgumentNullException e ArgumentOutOfRangeException</span><span class="sxs-lookup"><span data-stu-id="a1764-114">ArgumentException, ArgumentNullException, and ArgumentOutOfRangeException</span></span>  
 <span data-ttu-id="a1764-115">**FAZER ✓** gerar <xref:System.ArgumentException> ou um de seus subtipos se argumentos inválidos são passados para um membro.</span><span class="sxs-lookup"><span data-stu-id="a1764-115">**✓ DO** throw <xref:System.ArgumentException> or one of its subtypes if bad arguments are passed to a member.</span></span> <span data-ttu-id="a1764-116">Prefira o tipo de exceção mais derivado, se aplicável.</span><span class="sxs-lookup"><span data-stu-id="a1764-116">Prefer the most derived exception type, if applicable.</span></span>  
  
 <span data-ttu-id="a1764-117">**FAZER ✓** definir o `ParamName` propriedade ao lançar uma destas subclasses de `ArgumentException`.</span><span class="sxs-lookup"><span data-stu-id="a1764-117">**✓ DO** set the `ParamName` property when throwing one of the subclasses of `ArgumentException`.</span></span>  
  
 <span data-ttu-id="a1764-118">Esta propriedade representa o nome do parâmetro que causou a exceção seja lançada.</span><span class="sxs-lookup"><span data-stu-id="a1764-118">This property represents the name of the parameter that caused the exception to be thrown.</span></span> <span data-ttu-id="a1764-119">Observe que a propriedade pode ser definida usando uma das sobrecargas de construtor.</span><span class="sxs-lookup"><span data-stu-id="a1764-119">Note that the property can be set using one of the constructor overloads.</span></span>  
  
 <span data-ttu-id="a1764-120">**FAZER ✓** usar `value` para o nome do parâmetro de valor implícito de setters de propriedade.</span><span class="sxs-lookup"><span data-stu-id="a1764-120">**✓ DO** use `value` for the name of the implicit value parameter of property setters.</span></span>  
  
## <a name="nullreferenceexception-indexoutofrangeexception-and-accessviolationexception"></a><span data-ttu-id="a1764-121">NullReferenceException IndexOutOfRangeException e AccessViolationException</span><span class="sxs-lookup"><span data-stu-id="a1764-121">NullReferenceException, IndexOutOfRangeException, and AccessViolationException</span></span>  
 <span data-ttu-id="a1764-122">**X não** permitir que APIs publicamente que pode ser chamado explicitamente ou implicitamente gerar <xref:System.NullReferenceException>, <xref:System.AccessViolationException>, ou <xref:System.IndexOutOfRangeException>.</span><span class="sxs-lookup"><span data-stu-id="a1764-122">**X DO NOT** allow publicly callable APIs to explicitly or implicitly throw <xref:System.NullReferenceException>, <xref:System.AccessViolationException>, or <xref:System.IndexOutOfRangeException>.</span></span> <span data-ttu-id="a1764-123">Essas exceções são reservadas e gerada pelo mecanismo de execução e, na que maioria dos casos indicar um bug.</span><span class="sxs-lookup"><span data-stu-id="a1764-123">These exceptions are reserved and thrown by the execution engine and in most cases indicate a bug.</span></span>  
  
 <span data-ttu-id="a1764-124">Fazer a verificação para evitar gerar essas exceções de argumento.</span><span class="sxs-lookup"><span data-stu-id="a1764-124">Do argument checking to avoid throwing these exceptions.</span></span> <span data-ttu-id="a1764-125">Gerar essas exceções expõe detalhes de implementação do seu método que pode ser alterado ao longo do tempo.</span><span class="sxs-lookup"><span data-stu-id="a1764-125">Throwing these exceptions exposes implementation details of your method that might change over time.</span></span>  
  
## <a name="stackoverflowexception"></a><span data-ttu-id="a1764-126">StackOverflowException</span><span class="sxs-lookup"><span data-stu-id="a1764-126">StackOverflowException</span></span>  
 <span data-ttu-id="a1764-127">**X não** lançar explicitamente <xref:System.StackOverflowException>.</span><span class="sxs-lookup"><span data-stu-id="a1764-127">**X DO NOT** explicitly throw <xref:System.StackOverflowException>.</span></span> <span data-ttu-id="a1764-128">A exceção deve ser explicitamente lançada apenas pelo CLR.</span><span class="sxs-lookup"><span data-stu-id="a1764-128">The exception should be explicitly thrown only by the CLR.</span></span>  
  
 <span data-ttu-id="a1764-129">**X não** catch `StackOverflowException`.</span><span class="sxs-lookup"><span data-stu-id="a1764-129">**X DO NOT** catch `StackOverflowException`.</span></span>  
  
 <span data-ttu-id="a1764-130">É quase impossível escrever código gerenciado que permaneça consistente na presença de estouro de pilha arbitrário.</span><span class="sxs-lookup"><span data-stu-id="a1764-130">It is almost impossible to write managed code that remains consistent in the presence of arbitrary stack overflows.</span></span> <span data-ttu-id="a1764-131">As partes não gerenciadas do CLR permanecem consistentes usando testes para mover o estouro de pilha para locais bem definidos, em vez recuando de estouro de pilha arbitrário.</span><span class="sxs-lookup"><span data-stu-id="a1764-131">The unmanaged parts of the CLR remain consistent by using probes to move stack overflows to well-defined places rather than by backing out from arbitrary stack overflows.</span></span>  
  
## <a name="outofmemoryexception"></a><span data-ttu-id="a1764-132">OutOfMemoryException</span><span class="sxs-lookup"><span data-stu-id="a1764-132">OutOfMemoryException</span></span>  
 <span data-ttu-id="a1764-133">**X não** lançar explicitamente <xref:System.OutOfMemoryException>.</span><span class="sxs-lookup"><span data-stu-id="a1764-133">**X DO NOT** explicitly throw <xref:System.OutOfMemoryException>.</span></span> <span data-ttu-id="a1764-134">Essa exceção é lançada apenas pela infraestrutura do CLR.</span><span class="sxs-lookup"><span data-stu-id="a1764-134">This exception is to be thrown only by the CLR infrastructure.</span></span>  
  
## <a name="comexception-sehexception-and-executionengineexception"></a><span data-ttu-id="a1764-135">ComException SEHException e ExecutionEngineException</span><span class="sxs-lookup"><span data-stu-id="a1764-135">ComException, SEHException, and ExecutionEngineException</span></span>  
 <span data-ttu-id="a1764-136">**X não** lançar explicitamente <xref:System.Runtime.InteropServices.COMException>, <xref:System.ExecutionEngineException>, e <xref:System.Runtime.InteropServices.SEHException>.</span><span class="sxs-lookup"><span data-stu-id="a1764-136">**X DO NOT** explicitly throw <xref:System.Runtime.InteropServices.COMException>,  <xref:System.ExecutionEngineException>, and <xref:System.Runtime.InteropServices.SEHException>.</span></span> <span data-ttu-id="a1764-137">Essas exceções devem ser lançada apenas pela infraestrutura do CLR.</span><span class="sxs-lookup"><span data-stu-id="a1764-137">These exceptions are to be thrown only by the CLR infrastructure.</span></span>  
  
 <span data-ttu-id="a1764-138">*Partes © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*</span><span class="sxs-lookup"><span data-stu-id="a1764-138">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="a1764-139">*Reimpressas pela permissão de Pearson educação, Inc. de [diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicados 22 de outubro de 2008, Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="a1764-139">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1764-140">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a1764-140">See Also</span></span>  
 [<span data-ttu-id="a1764-141">Diretrizes de design do Framework</span><span class="sxs-lookup"><span data-stu-id="a1764-141">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
 [<span data-ttu-id="a1764-142">Diretrizes de design para exceções</span><span class="sxs-lookup"><span data-stu-id="a1764-142">Design Guidelines for Exceptions</span></span>](../../../docs/standard/design-guidelines/exceptions.md)
