---
title: Instrução End <keyword> (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.EndDefinition
helpviewer_keywords:
- End keyword [Visual Basic]
ms.assetid: 42d6e088-ab0f-4cda-88e8-fdce3e5fcf4f
ms.openlocfilehash: 96dc8ce6b0d3b7545f5caeef43358936e426f566
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55273524"
---
# <a name="end-keyword-statement-visual-basic"></a><span data-ttu-id="fdb33-102">End \<palavra-chave > demonstrativo (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fdb33-102">End \<keyword> Statement (Visual Basic)</span></span>

<span data-ttu-id="fdb33-103">Quando seguido por uma palavra-chave adicional, finaliza a definição do bloco de instrução introduzido por essa palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="fdb33-103">When followed by an additional keyword, terminates the definition of the statement block introduced by that keyword.</span></span>

## <a name="syntax"></a><span data-ttu-id="fdb33-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fdb33-104">Syntax</span></span>

```vb
End AddHandler
End Class
End Enum
End Event
End Function
End Get
End If
End Interface
End Module
End Namespace
End Operator
End Property
End RaiseEvent  
End RemoveHandler  
End Select
End Set
End Structure
End Sub
End SyncLock
End Try
End While
End With  
```  
  
## <a name="parts"></a><span data-ttu-id="fdb33-105">Partes</span><span class="sxs-lookup"><span data-stu-id="fdb33-105">Parts</span></span>

|<span data-ttu-id="fdb33-106">Parte</span><span class="sxs-lookup"><span data-stu-id="fdb33-106">Part</span></span>|<span data-ttu-id="fdb33-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="fdb33-107">Description</span></span>|
|---|---|
|`End`|<span data-ttu-id="fdb33-108">Necessário.</span><span class="sxs-lookup"><span data-stu-id="fdb33-108">Required.</span></span> <span data-ttu-id="fdb33-109">Finaliza a definição do elemento de programação.</span><span class="sxs-lookup"><span data-stu-id="fdb33-109">Terminates the definition of the programming element.</span></span>|
|`AddHandler`|<span data-ttu-id="fdb33-110">Necessário para finalizar uma `AddHandler` iniciado por uma correspondência de acessador `AddHandler` instrução em um personalizado [instrução Event](event-statement.md).</span><span class="sxs-lookup"><span data-stu-id="fdb33-110">Required to terminate an `AddHandler` accessor begun by a matching `AddHandler` statement in a custom [Event Statement](event-statement.md).</span></span>|
|`Class`|<span data-ttu-id="fdb33-111">Necessário para finalizar uma definição de classe iniciada por uma correspondência [declaração de classe](class-statement.md).</span><span class="sxs-lookup"><span data-stu-id="fdb33-111">Required to terminate a class definition begun by a matching [Class Statement](class-statement.md).</span></span>|
|`Enum`|<span data-ttu-id="fdb33-112">Necessário para finalizar uma definição de enumeração iniciada por uma correspondência [instrução Enum](enum-statement.md).</span><span class="sxs-lookup"><span data-stu-id="fdb33-112">Required to terminate an enumeration definition begun by a matching [Enum Statement](enum-statement.md).</span></span>|
|`Event`|<span data-ttu-id="fdb33-113">Necessário para finalizar uma `Custom` iniciada por uma correspondência de definição de evento [instrução Event](event-statement.md).</span><span class="sxs-lookup"><span data-stu-id="fdb33-113">Required to terminate a `Custom` event definition begun by a matching [Event Statement](event-statement.md).</span></span>|  
|`Function`|<span data-ttu-id="fdb33-114">Necessário para finalizar uma `Function` iniciada por uma definição do procedimento [instrução Function](function-statement.md).</span><span class="sxs-lookup"><span data-stu-id="fdb33-114">Required to terminate a `Function` procedure definition begun by a matching [Function Statement](function-statement.md).</span></span> <span data-ttu-id="fdb33-115">Se a execução encontrar um `End Function` instrução, o controle retorna para o código de chamada.</span><span class="sxs-lookup"><span data-stu-id="fdb33-115">If execution encounters an `End Function` statement, control returns to the calling code.</span></span>|
|`Get`|<span data-ttu-id="fdb33-116">Necessário para finalizar uma `Property` iniciada por uma definição do procedimento [instrução Get](get-statement.md).</span><span class="sxs-lookup"><span data-stu-id="fdb33-116">Required to terminate a `Property` procedure definition begun by a matching [Get Statement](get-statement.md).</span></span> <span data-ttu-id="fdb33-117">Se a execução encontrar um `End Get` instrução, o controle retorna para a instrução solicitando o valor da propriedade.</span><span class="sxs-lookup"><span data-stu-id="fdb33-117">If execution encounters an `End Get` statement, control returns to the statement requesting the property's value.</span></span>|
|`If`|<span data-ttu-id="fdb33-118">Necessário para finalizar uma `If`... `Then`... `Else` iniciada por uma correspondência `If` instrução.</span><span class="sxs-lookup"><span data-stu-id="fdb33-118">Required to terminate an `If`...`Then`...`Else` block definition begun by a matching `If` statement.</span></span> <span data-ttu-id="fdb33-119">Consulte [se... Then... Instrução else](if-then-else-statement.md).</span><span class="sxs-lookup"><span data-stu-id="fdb33-119">See [If...Then...Else Statement](if-then-else-statement.md).</span></span>|
|`Interface`|<span data-ttu-id="fdb33-120">Necessário para finalizar uma definição de interface iniciada por uma correspondência [declaração de Interface](interface-statement.md).</span><span class="sxs-lookup"><span data-stu-id="fdb33-120">Required to terminate an interface definition begun by a matching [Interface Statement](interface-statement.md).</span></span>|
|`Module`|<span data-ttu-id="fdb33-121">Necessário para finalizar uma definição de módulo iniciada por uma correspondência [declaração de módulo](module-statement.md).</span><span class="sxs-lookup"><span data-stu-id="fdb33-121">Required to terminate a module definition begun by a matching [Module Statement](module-statement.md).</span></span>|
|`Namespace`|<span data-ttu-id="fdb33-122">Necessário para finalizar uma definição de namespace iniciada por uma correspondência [declaração de Namespace](namespace-statement.md).</span><span class="sxs-lookup"><span data-stu-id="fdb33-122">Required to terminate a namespace definition begun by a matching [Namespace Statement](namespace-statement.md).</span></span>|
|`Operator`|<span data-ttu-id="fdb33-123">Necessário para finalizar uma definição de operador iniciada por uma correspondência [instrução Operator](operator-statement.md).</span><span class="sxs-lookup"><span data-stu-id="fdb33-123">Required to terminate an operator definition begun by a matching [Operator Statement](operator-statement.md).</span></span>|
|`Property`|<span data-ttu-id="fdb33-124">Necessário para finalizar uma definição de propriedade iniciada por uma correspondência [declaração de propriedade](property-statement.md).</span><span class="sxs-lookup"><span data-stu-id="fdb33-124">Required to terminate a property definition begun by a matching [Property Statement](property-statement.md).</span></span>|
|`RaiseEvent`|<span data-ttu-id="fdb33-125">Necessário para finalizar uma `RaiseEvent` iniciado por uma correspondência de acessador `RaiseEvent` instrução em um personalizado [instrução Event](event-statement.md).</span><span class="sxs-lookup"><span data-stu-id="fdb33-125">Required to terminate a `RaiseEvent` accessor begun by a matching `RaiseEvent` statement in a custom [Event Statement](event-statement.md).</span></span>|
|`RemoveHandler`|<span data-ttu-id="fdb33-126">Necessário para finalizar uma `RemoveHandler` iniciado por uma correspondência de acessador `RemoveHandler` instrução em um personalizado [instrução Event](event-statement.md).</span><span class="sxs-lookup"><span data-stu-id="fdb33-126">Required to terminate a `RemoveHandler` accessor begun by a matching `RemoveHandler` statement in a custom [Event Statement](event-statement.md).</span></span>|
|`Select`|<span data-ttu-id="fdb33-127">Necessário para finalizar uma `Select`... `Case` iniciada por uma correspondência `Select` instrução.</span><span class="sxs-lookup"><span data-stu-id="fdb33-127">Required to terminate a `Select`...`Case` block definition begun by a matching `Select` statement.</span></span> <span data-ttu-id="fdb33-128">Consulte [selecione... Instrução de caso](select-case-statement.md).</span><span class="sxs-lookup"><span data-stu-id="fdb33-128">See [Select...Case Statement](select-case-statement.md).</span></span>  
|`Set`|<span data-ttu-id="fdb33-129">Necessário para finalizar uma `Property` iniciada por uma definição do procedimento [instrução Set](set-statement.md).</span><span class="sxs-lookup"><span data-stu-id="fdb33-129">Required to terminate a `Property` procedure definition begun by a matching [Set Statement](set-statement.md).</span></span> <span data-ttu-id="fdb33-130">Se a execução encontrar um `End Set` instrução, o controle retorna para a instrução que configura o valor da propriedade.</span><span class="sxs-lookup"><span data-stu-id="fdb33-130">If execution encounters an `End Set` statement, control returns to the statement setting the property's value.</span></span>  
|`Structure`|<span data-ttu-id="fdb33-131">Necessário para finalizar uma definição de estrutura iniciada por uma correspondência [instrução Structure](structure-statement.md).</span><span class="sxs-lookup"><span data-stu-id="fdb33-131">Required to terminate a structure definition begun by a matching [Structure Statement](structure-statement.md).</span></span>  
|`Sub`|<span data-ttu-id="fdb33-132">Necessário para finalizar uma `Sub` iniciada por uma definição do procedimento [instrução Sub](sub-statement.md).</span><span class="sxs-lookup"><span data-stu-id="fdb33-132">Required to terminate a `Sub` procedure definition begun by a matching [Sub Statement](sub-statement.md).</span></span> <span data-ttu-id="fdb33-133">Se a execução encontrar um `End Sub` instrução, o controle retorna para o código de chamada.</span><span class="sxs-lookup"><span data-stu-id="fdb33-133">If execution encounters an `End Sub` statement, control returns to the calling code.</span></span>  
|`SyncLock`|<span data-ttu-id="fdb33-134">Necessário para finalizar uma `SyncLock` iniciada por uma correspondência `SyncLock` instrução.</span><span class="sxs-lookup"><span data-stu-id="fdb33-134">Required to terminate a `SyncLock` block definition begun by a matching `SyncLock` statement.</span></span> <span data-ttu-id="fdb33-135">Ver [Instrução SyncLock](synclock-statement.md).</span><span class="sxs-lookup"><span data-stu-id="fdb33-135">See [SyncLock Statement](synclock-statement.md).</span></span>  
|`Try`|<span data-ttu-id="fdb33-136">Necessário para finalizar uma `Try`... `Catch`... `Finally` iniciada por uma correspondência `Try` instrução.</span><span class="sxs-lookup"><span data-stu-id="fdb33-136">Required to terminate a `Try`...`Catch`...`Finally` block definition begun by a matching `Try` statement.</span></span> <span data-ttu-id="fdb33-137">Consulte [tente... Catch... Instrução Finally](try-catch-finally-statement.md).</span><span class="sxs-lookup"><span data-stu-id="fdb33-137">See [Try...Catch...Finally Statement](try-catch-finally-statement.md).</span></span>  
|`While`|<span data-ttu-id="fdb33-138">Necessário para finalizar uma `While` iniciada por uma correspondência de definição de loop `While` instrução.</span><span class="sxs-lookup"><span data-stu-id="fdb33-138">Required to terminate a `While` loop definition begun by a matching `While` statement.</span></span> <span data-ttu-id="fdb33-139">Consulte [enquanto... Finalizar instrução While](while-end-while-statement.md).</span><span class="sxs-lookup"><span data-stu-id="fdb33-139">See [While...End While Statement](while-end-while-statement.md).</span></span>  
|`With`| <span data-ttu-id="fdb33-140">Necessário para finalizar uma `With` iniciada por uma correspondência `With` instrução.</span><span class="sxs-lookup"><span data-stu-id="fdb33-140">Required to terminate a `With` block definition begun by a matching `With` statement.</span></span> <span data-ttu-id="fdb33-141">Consulte [com... Terminar com a instrução](with-end-with-statement.md).</span><span class="sxs-lookup"><span data-stu-id="fdb33-141">See [With...End With Statement](with-end-with-statement.md).</span></span>  
|||
  
## <a name="directives"></a><span data-ttu-id="fdb33-142">Diretivas</span><span class="sxs-lookup"><span data-stu-id="fdb33-142">Directives</span></span>

<span data-ttu-id="fdb33-143">Quando precedido por um sinal numérico (`#`), o `End` palavra-chave encerra um bloco de pré-processamento introduzido pela diretiva correspondente.</span><span class="sxs-lookup"><span data-stu-id="fdb33-143">When preceded by a number sign (`#`), the `End` keyword terminates a preprocessing block introduced by the corresponding directive.</span></span>  

```vb
#End ExternalSource
#End If
#End Region
```

|<span data-ttu-id="fdb33-144">Parte</span><span class="sxs-lookup"><span data-stu-id="fdb33-144">Part</span></span>|<span data-ttu-id="fdb33-145">Descrição</span><span class="sxs-lookup"><span data-stu-id="fdb33-145">Description</span></span>|
|---|---|
|`#End`|<span data-ttu-id="fdb33-146">Necessário.</span><span class="sxs-lookup"><span data-stu-id="fdb33-146">Required.</span></span> <span data-ttu-id="fdb33-147">Finaliza a definição do bloco de pré-processamento.</span><span class="sxs-lookup"><span data-stu-id="fdb33-147">Terminates the definition of the preprocessing block.</span></span>|
|`ExternalSource`|<span data-ttu-id="fdb33-148">Necessário para finalizar um bloco de origem externa iniciado por uma correspondência [#ExternalSource diretiva](../directives/externalsource-directive.md).</span><span class="sxs-lookup"><span data-stu-id="fdb33-148">Required to terminate an external source block begun by a matching [#ExternalSource Directive](../directives/externalsource-directive.md).</span></span>|
|`If`|<span data-ttu-id="fdb33-149">Necessário para finalizar um bloco de compilação condicional iniciado por uma correspondência `#If` diretiva.</span><span class="sxs-lookup"><span data-stu-id="fdb33-149">Required to terminate a conditional compilation block begun by a matching `#If` directive.</span></span> <span data-ttu-id="fdb33-150">Consulte [#If... Then... #Else diretivas](../directives/if-then-else-directives.md).</span><span class="sxs-lookup"><span data-stu-id="fdb33-150">See [#If...Then...#Else Directives](../directives/if-then-else-directives.md).</span></span>|
|`Region`|<span data-ttu-id="fdb33-151">Necessário para finalizar um bloco de região de origem iniciado por uma correspondência [#Region diretiva](../directives/region-directive.md).</span><span class="sxs-lookup"><span data-stu-id="fdb33-151">Required to terminate a source region block begun by a matching [#Region Directive](../directives/region-directive.md).</span></span>|
|||

## <a name="remarks"></a><span data-ttu-id="fdb33-152">Comentários</span><span class="sxs-lookup"><span data-stu-id="fdb33-152">Remarks</span></span>

<span data-ttu-id="fdb33-153">O [instrução End](end-statement.md), sem uma palavra-chave adicional, finaliza a execução imediatamente.</span><span class="sxs-lookup"><span data-stu-id="fdb33-153">The [End Statement](end-statement.md), without an additional keyword, terminates execution immediately.</span></span>

## <a name="smart-device-developer-notes"></a><span data-ttu-id="fdb33-154">Notas do desenvolvedor de dispositivo inteligente</span><span class="sxs-lookup"><span data-stu-id="fdb33-154">Smart Device Developer Notes</span></span>  

<span data-ttu-id="fdb33-155">O `End` instrução sem uma palavra-chave adicional, não é suportada.</span><span class="sxs-lookup"><span data-stu-id="fdb33-155">The `End` statement, without an additional keyword, is not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fdb33-156">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fdb33-156">See also</span></span>

- [<span data-ttu-id="fdb33-157">Instrução End</span><span class="sxs-lookup"><span data-stu-id="fdb33-157">End Statement</span></span>](end-statement.md)
