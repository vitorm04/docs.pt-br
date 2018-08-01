---
title: Usando tipos de exceção padrão
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- throwing exceptions, standard types
- catching exceptions
- exceptions, catching
- exceptions, throwing
ms.assetid: ab22ce03-78f9-4dca-8824-c7ed3bdccc27
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 81e4047c171e3a58f335821d64390432524b25df
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33574589"
---
# <a name="using-standard-exception-types"></a><span data-ttu-id="d0c2d-102">Usando tipos de exceção padrão</span><span class="sxs-lookup"><span data-stu-id="d0c2d-102">Using Standard Exception Types</span></span>
<span data-ttu-id="d0c2d-103">Esta seção descreve as exceções padrão fornecidas pela estrutura e os detalhes de uso.</span><span class="sxs-lookup"><span data-stu-id="d0c2d-103">This section describes the standard exceptions provided by the Framework and the details of their usage.</span></span> <span data-ttu-id="d0c2d-104">A lista não é exaustiva.</span><span class="sxs-lookup"><span data-stu-id="d0c2d-104">The list is by no means exhaustive.</span></span> <span data-ttu-id="d0c2d-105">Consulte a documentação de referência do .NET Framework para o uso de outros tipos de exceção do Framework.</span><span class="sxs-lookup"><span data-stu-id="d0c2d-105">Please refer to the .NET Framework reference documentation for usage of other Framework exception types.</span></span>  
  
## <a name="exception-and-systemexception"></a><span data-ttu-id="d0c2d-106">Exceção e SystemException</span><span class="sxs-lookup"><span data-stu-id="d0c2d-106">Exception and SystemException</span></span>  
 <span data-ttu-id="d0c2d-107">**X DO NOT** gerar <xref:System.Exception?displayProperty=nameWithType> ou <xref:System.SystemException?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="d0c2d-107">**X DO NOT** throw <xref:System.Exception?displayProperty=nameWithType> or <xref:System.SystemException?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="d0c2d-108">**X DO NOT** catch `System.Exception` ou `System.SystemException` no código do framework, a menos que você pretende relançar.</span><span class="sxs-lookup"><span data-stu-id="d0c2d-108">**X DO NOT** catch `System.Exception` or `System.SystemException` in framework code, unless you intend to rethrow.</span></span>  
  
 <span data-ttu-id="d0c2d-109">**X AVOID** capturando `System.Exception` ou `System.SystemException`, exceto em manipuladores de exceção de nível superior.</span><span class="sxs-lookup"><span data-stu-id="d0c2d-109">**X AVOID** catching `System.Exception` or `System.SystemException`, except in top-level exception handlers.</span></span>  
  
## <a name="applicationexception"></a><span data-ttu-id="d0c2d-110">ApplicationException</span><span class="sxs-lookup"><span data-stu-id="d0c2d-110">ApplicationException</span></span>  
 <span data-ttu-id="d0c2d-111">**X DO NOT** lançar ou derivam de <xref:System.ApplicationException>.</span><span class="sxs-lookup"><span data-stu-id="d0c2d-111">**X DO NOT** throw or derive from <xref:System.ApplicationException>.</span></span>  
  
## <a name="invalidoperationexception"></a><span data-ttu-id="d0c2d-112">InvalidOperationException</span><span class="sxs-lookup"><span data-stu-id="d0c2d-112">InvalidOperationException</span></span>  
 <span data-ttu-id="d0c2d-113">**✓ DO** lançar um <xref:System.InvalidOperationException> se o objeto está em um estado inadequado.</span><span class="sxs-lookup"><span data-stu-id="d0c2d-113">**✓ DO** throw an <xref:System.InvalidOperationException> if the object is in an inappropriate state.</span></span>  
  
## <a name="argumentexception-argumentnullexception-and-argumentoutofrangeexception"></a><span data-ttu-id="d0c2d-114">ArgumentException ArgumentNullException e ArgumentOutOfRangeException</span><span class="sxs-lookup"><span data-stu-id="d0c2d-114">ArgumentException, ArgumentNullException, and ArgumentOutOfRangeException</span></span>  
 <span data-ttu-id="d0c2d-115">**✓ DO** gerar <xref:System.ArgumentException> ou um de seus subtipos se argumentos inválidos são passados para um membro.</span><span class="sxs-lookup"><span data-stu-id="d0c2d-115">**✓ DO** throw <xref:System.ArgumentException> or one of its subtypes if bad arguments are passed to a member.</span></span> <span data-ttu-id="d0c2d-116">Prefira o tipo de exceção mais derivado, se aplicável.</span><span class="sxs-lookup"><span data-stu-id="d0c2d-116">Prefer the most derived exception type, if applicable.</span></span>  
  
 <span data-ttu-id="d0c2d-117">**✓ DO** definir o `ParamName` propriedade ao lançar uma destas subclasses de `ArgumentException`.</span><span class="sxs-lookup"><span data-stu-id="d0c2d-117">**✓ DO** set the `ParamName` property when throwing one of the subclasses of `ArgumentException`.</span></span>  
  
 <span data-ttu-id="d0c2d-118">Esta propriedade representa o nome do parâmetro que causou a exceção seja lançada.</span><span class="sxs-lookup"><span data-stu-id="d0c2d-118">This property represents the name of the parameter that caused the exception to be thrown.</span></span> <span data-ttu-id="d0c2d-119">Observe que a propriedade pode ser definida usando uma das sobrecargas de construtor.</span><span class="sxs-lookup"><span data-stu-id="d0c2d-119">Note that the property can be set using one of the constructor overloads.</span></span>  
  
 <span data-ttu-id="d0c2d-120">**✓ DO** usar `value` para o nome do parâmetro de valor implícito de setters de propriedade.</span><span class="sxs-lookup"><span data-stu-id="d0c2d-120">**✓ DO** use `value` for the name of the implicit value parameter of property setters.</span></span>  
  
## <a name="nullreferenceexception-indexoutofrangeexception-and-accessviolationexception"></a><span data-ttu-id="d0c2d-121">NullReferenceException IndexOutOfRangeException e AccessViolationException</span><span class="sxs-lookup"><span data-stu-id="d0c2d-121">NullReferenceException, IndexOutOfRangeException, and AccessViolationException</span></span>  
 <span data-ttu-id="d0c2d-122">**X DO NOT** permitir que APIs publicamente que pode ser chamado explicitamente ou implicitamente gerar <xref:System.NullReferenceException>, <xref:System.AccessViolationException>, ou <xref:System.IndexOutOfRangeException>.</span><span class="sxs-lookup"><span data-stu-id="d0c2d-122">**X DO NOT** allow publicly callable APIs to explicitly or implicitly throw <xref:System.NullReferenceException>, <xref:System.AccessViolationException>, or <xref:System.IndexOutOfRangeException>.</span></span> <span data-ttu-id="d0c2d-123">Essas exceções são reservadas e gerada pelo mecanismo de execução e, na que maioria dos casos indicar um bug.</span><span class="sxs-lookup"><span data-stu-id="d0c2d-123">These exceptions are reserved and thrown by the execution engine and in most cases indicate a bug.</span></span>  
  
 <span data-ttu-id="d0c2d-124">Fazer a verificação para evitar gerar essas exceções de argumento.</span><span class="sxs-lookup"><span data-stu-id="d0c2d-124">Do argument checking to avoid throwing these exceptions.</span></span> <span data-ttu-id="d0c2d-125">Gerar essas exceções expõe detalhes de implementação do seu método que pode ser alterado ao longo do tempo.</span><span class="sxs-lookup"><span data-stu-id="d0c2d-125">Throwing these exceptions exposes implementation details of your method that might change over time.</span></span>  
  
## <a name="stackoverflowexception"></a><span data-ttu-id="d0c2d-126">StackOverflowException</span><span class="sxs-lookup"><span data-stu-id="d0c2d-126">StackOverflowException</span></span>  
 <span data-ttu-id="d0c2d-127">**X DO NOT** lançar explicitamente <xref:System.StackOverflowException>.</span><span class="sxs-lookup"><span data-stu-id="d0c2d-127">**X DO NOT** explicitly throw <xref:System.StackOverflowException>.</span></span> <span data-ttu-id="d0c2d-128">A exceção deve ser explicitamente lançada apenas pelo CLR.</span><span class="sxs-lookup"><span data-stu-id="d0c2d-128">The exception should be explicitly thrown only by the CLR.</span></span>  
  
 <span data-ttu-id="d0c2d-129">**X DO NOT** catch `StackOverflowException`.</span><span class="sxs-lookup"><span data-stu-id="d0c2d-129">**X DO NOT** catch `StackOverflowException`.</span></span>  
  
 <span data-ttu-id="d0c2d-130">É quase impossível escrever código gerenciado que permaneça consistente na presença de estouro de pilha arbitrário.</span><span class="sxs-lookup"><span data-stu-id="d0c2d-130">It is almost impossible to write managed code that remains consistent in the presence of arbitrary stack overflows.</span></span> <span data-ttu-id="d0c2d-131">As partes não gerenciadas do CLR permanecem consistentes usando testes para mover o estouro de pilha para locais bem definidos, em vez recuando de estouro de pilha arbitrário.</span><span class="sxs-lookup"><span data-stu-id="d0c2d-131">The unmanaged parts of the CLR remain consistent by using probes to move stack overflows to well-defined places rather than by backing out from arbitrary stack overflows.</span></span>  
  
## <a name="outofmemoryexception"></a><span data-ttu-id="d0c2d-132">OutOfMemoryException</span><span class="sxs-lookup"><span data-stu-id="d0c2d-132">OutOfMemoryException</span></span>  
 <span data-ttu-id="d0c2d-133">**X DO NOT** lançar explicitamente <xref:System.OutOfMemoryException>.</span><span class="sxs-lookup"><span data-stu-id="d0c2d-133">**X DO NOT** explicitly throw <xref:System.OutOfMemoryException>.</span></span> <span data-ttu-id="d0c2d-134">Essa exceção é lançada apenas pela infraestrutura do CLR.</span><span class="sxs-lookup"><span data-stu-id="d0c2d-134">This exception is to be thrown only by the CLR infrastructure.</span></span>  
  
## <a name="comexception-sehexception-and-executionengineexception"></a><span data-ttu-id="d0c2d-135">ComException SEHException e ExecutionEngineException</span><span class="sxs-lookup"><span data-stu-id="d0c2d-135">ComException, SEHException, and ExecutionEngineException</span></span>  
 <span data-ttu-id="d0c2d-136">**X DO NOT** lançar explicitamente <xref:System.Runtime.InteropServices.COMException>, <xref:System.ExecutionEngineException>, e <xref:System.Runtime.InteropServices.SEHException>.</span><span class="sxs-lookup"><span data-stu-id="d0c2d-136">**X DO NOT** explicitly throw <xref:System.Runtime.InteropServices.COMException>,  <xref:System.ExecutionEngineException>, and <xref:System.Runtime.InteropServices.SEHException>.</span></span> <span data-ttu-id="d0c2d-137">Essas exceções devem ser lançada apenas pela infraestrutura do CLR.</span><span class="sxs-lookup"><span data-stu-id="d0c2d-137">These exceptions are to be thrown only by the CLR infrastructure.</span></span>  
  
 <span data-ttu-id="d0c2d-138">*Portions © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*</span><span class="sxs-lookup"><span data-stu-id="d0c2d-138">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="d0c2d-139">*Reimpressas pela permissão de Pearson educação, Inc. de [diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicados 22 de outubro de 2008, Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="d0c2d-139">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0c2d-140">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d0c2d-140">See Also</span></span>  
 [<span data-ttu-id="d0c2d-141">Diretrizes de design do Framework</span><span class="sxs-lookup"><span data-stu-id="d0c2d-141">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
 [<span data-ttu-id="d0c2d-142">Diretrizes de design para exceções</span><span class="sxs-lookup"><span data-stu-id="d0c2d-142">Design Guidelines for Exceptions</span></span>](../../../docs/standard/design-guidelines/exceptions.md)
