---
title: Instrução End <keyword>
ms.date: 07/20/2015
f1_keywords:
- vb.EndDefinition
helpviewer_keywords:
- End keyword [Visual Basic]
ms.assetid: 42d6e088-ab0f-4cda-88e8-fdce3e5fcf4f
ms.openlocfilehash: 87f4724cc036e6e0bdf0b558854a4034f45b9ab5
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343745"
---
# <a name="end-keyword-statement-visual-basic"></a><span data-ttu-id="e5371-102">Instrução End \<palavra-chave > (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e5371-102">End \<keyword> Statement (Visual Basic)</span></span>

<span data-ttu-id="e5371-103">Quando seguido por uma palavra-chave adicional, termina a definição do bloco de instrução introduzido por essa palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="e5371-103">When followed by an additional keyword, terminates the definition of the statement block introduced by that keyword.</span></span>

## <a name="syntax"></a><span data-ttu-id="e5371-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e5371-104">Syntax</span></span>

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
  
## <a name="parts"></a><span data-ttu-id="e5371-105">Partes</span><span class="sxs-lookup"><span data-stu-id="e5371-105">Parts</span></span>

|<span data-ttu-id="e5371-106">Parte</span><span class="sxs-lookup"><span data-stu-id="e5371-106">Part</span></span>|<span data-ttu-id="e5371-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="e5371-107">Description</span></span>|
|---|---|
|`End`|<span data-ttu-id="e5371-108">Necessária.</span><span class="sxs-lookup"><span data-stu-id="e5371-108">Required.</span></span> <span data-ttu-id="e5371-109">Encerra a definição do elemento de programação.</span><span class="sxs-lookup"><span data-stu-id="e5371-109">Terminates the definition of the programming element.</span></span>|
|`AddHandler`|<span data-ttu-id="e5371-110">Necessário para encerrar um acessador `AddHandler` iniciado por uma instrução `AddHandler` correspondente em uma [instrução de evento](event-statement.md)personalizado.</span><span class="sxs-lookup"><span data-stu-id="e5371-110">Required to terminate an `AddHandler` accessor begun by a matching `AddHandler` statement in a custom [Event Statement](event-statement.md).</span></span>|
|`Class`|<span data-ttu-id="e5371-111">Necessário para encerrar uma definição de classe iniciada por uma [instrução de classe](class-statement.md)correspondente.</span><span class="sxs-lookup"><span data-stu-id="e5371-111">Required to terminate a class definition begun by a matching [Class Statement](class-statement.md).</span></span>|
|`Enum`|<span data-ttu-id="e5371-112">Necessário para encerrar uma definição de enumeração iniciada por uma [instrução enum](enum-statement.md)correspondente.</span><span class="sxs-lookup"><span data-stu-id="e5371-112">Required to terminate an enumeration definition begun by a matching [Enum Statement](enum-statement.md).</span></span>|
|`Event`|<span data-ttu-id="e5371-113">Necessário para encerrar uma definição de evento `Custom` iniciada por uma [instrução de evento](event-statement.md)correspondente.</span><span class="sxs-lookup"><span data-stu-id="e5371-113">Required to terminate a `Custom` event definition begun by a matching [Event Statement](event-statement.md).</span></span>|  
|`Function`|<span data-ttu-id="e5371-114">Necessário para encerrar uma definição de procedimento `Function` iniciada por uma [instrução de função](function-statement.md)correspondente.</span><span class="sxs-lookup"><span data-stu-id="e5371-114">Required to terminate a `Function` procedure definition begun by a matching [Function Statement](function-statement.md).</span></span> <span data-ttu-id="e5371-115">Se a execução encontrar uma instrução `End Function`, o controle retornará ao código de chamada.</span><span class="sxs-lookup"><span data-stu-id="e5371-115">If execution encounters an `End Function` statement, control returns to the calling code.</span></span>|
|`Get`|<span data-ttu-id="e5371-116">Necessário para encerrar uma definição de procedimento `Property` iniciada por uma [instrução Get](get-statement.md)correspondente.</span><span class="sxs-lookup"><span data-stu-id="e5371-116">Required to terminate a `Property` procedure definition begun by a matching [Get Statement](get-statement.md).</span></span> <span data-ttu-id="e5371-117">Se a execução encontrar uma instrução `End Get`, o controle retornará à instrução que solicita o valor da propriedade.</span><span class="sxs-lookup"><span data-stu-id="e5371-117">If execution encounters an `End Get` statement, control returns to the statement requesting the property's value.</span></span>|
|`If`|<span data-ttu-id="e5371-118">Necessário para encerrar uma `If`...`Then`...`Else` definição de bloco iniciada por uma instrução `If` correspondente.</span><span class="sxs-lookup"><span data-stu-id="e5371-118">Required to terminate an `If`...`Then`...`Else` block definition begun by a matching `If` statement.</span></span> <span data-ttu-id="e5371-119">Veja [se... Então... Else](if-then-else-statement.md).</span><span class="sxs-lookup"><span data-stu-id="e5371-119">See [If...Then...Else Statement](if-then-else-statement.md).</span></span>|
|`Interface`|<span data-ttu-id="e5371-120">Necessário para encerrar uma definição de interface iniciada por uma [instrução de interface](interface-statement.md)correspondente.</span><span class="sxs-lookup"><span data-stu-id="e5371-120">Required to terminate an interface definition begun by a matching [Interface Statement](interface-statement.md).</span></span>|
|`Module`|<span data-ttu-id="e5371-121">Necessário para encerrar uma definição de módulo iniciada por uma [instrução de módulo](module-statement.md)correspondente.</span><span class="sxs-lookup"><span data-stu-id="e5371-121">Required to terminate a module definition begun by a matching [Module Statement](module-statement.md).</span></span>|
|`Namespace`|<span data-ttu-id="e5371-122">Necessário para encerrar uma definição de namespace iniciada por uma [instrução de namespace](namespace-statement.md)correspondente.</span><span class="sxs-lookup"><span data-stu-id="e5371-122">Required to terminate a namespace definition begun by a matching [Namespace Statement](namespace-statement.md).</span></span>|
|`Operator`|<span data-ttu-id="e5371-123">Necessário para encerrar uma definição de operador iniciada por uma [instrução de operador](operator-statement.md)correspondente.</span><span class="sxs-lookup"><span data-stu-id="e5371-123">Required to terminate an operator definition begun by a matching [Operator Statement](operator-statement.md).</span></span>|
|`Property`|<span data-ttu-id="e5371-124">Necessário para encerrar uma definição de propriedade iniciada por uma [instrução de propriedade](property-statement.md)correspondente.</span><span class="sxs-lookup"><span data-stu-id="e5371-124">Required to terminate a property definition begun by a matching [Property Statement](property-statement.md).</span></span>|
|`RaiseEvent`|<span data-ttu-id="e5371-125">Necessário para encerrar um acessador `RaiseEvent` iniciado por uma instrução `RaiseEvent` correspondente em uma [instrução de evento](event-statement.md)personalizado.</span><span class="sxs-lookup"><span data-stu-id="e5371-125">Required to terminate a `RaiseEvent` accessor begun by a matching `RaiseEvent` statement in a custom [Event Statement](event-statement.md).</span></span>|
|`RemoveHandler`|<span data-ttu-id="e5371-126">Necessário para encerrar um acessador `RemoveHandler` iniciado por uma instrução `RemoveHandler` correspondente em uma [instrução de evento](event-statement.md)personalizado.</span><span class="sxs-lookup"><span data-stu-id="e5371-126">Required to terminate a `RemoveHandler` accessor begun by a matching `RemoveHandler` statement in a custom [Event Statement](event-statement.md).</span></span>|
|`Select`|<span data-ttu-id="e5371-127">Necessário para encerrar uma `Select`...`Case` definição de bloco iniciada por uma instrução `Select` correspondente.</span><span class="sxs-lookup"><span data-stu-id="e5371-127">Required to terminate a `Select`...`Case` block definition begun by a matching `Select` statement.</span></span> <span data-ttu-id="e5371-128">Consulte [selecionar... Instrução Case](select-case-statement.md).</span><span class="sxs-lookup"><span data-stu-id="e5371-128">See [Select...Case Statement](select-case-statement.md).</span></span>  
|`Set`|<span data-ttu-id="e5371-129">Necessário para encerrar uma definição de procedimento `Property` iniciada por uma [instrução SET](set-statement.md)correspondente.</span><span class="sxs-lookup"><span data-stu-id="e5371-129">Required to terminate a `Property` procedure definition begun by a matching [Set Statement](set-statement.md).</span></span> <span data-ttu-id="e5371-130">Se a execução encontrar uma instrução `End Set`, o controle retornará à instrução definindo o valor da propriedade.</span><span class="sxs-lookup"><span data-stu-id="e5371-130">If execution encounters an `End Set` statement, control returns to the statement setting the property's value.</span></span>  
|`Structure`|<span data-ttu-id="e5371-131">Necessário para encerrar uma definição de estrutura iniciada por uma [instrução de estrutura](structure-statement.md)correspondente.</span><span class="sxs-lookup"><span data-stu-id="e5371-131">Required to terminate a structure definition begun by a matching [Structure Statement](structure-statement.md).</span></span>  
|`Sub`|<span data-ttu-id="e5371-132">Necessário para encerrar uma definição de procedimento `Sub` iniciada por uma [instrução sub](sub-statement.md)correspondente.</span><span class="sxs-lookup"><span data-stu-id="e5371-132">Required to terminate a `Sub` procedure definition begun by a matching [Sub Statement](sub-statement.md).</span></span> <span data-ttu-id="e5371-133">Se a execução encontrar uma instrução `End Sub`, o controle retornará ao código de chamada.</span><span class="sxs-lookup"><span data-stu-id="e5371-133">If execution encounters an `End Sub` statement, control returns to the calling code.</span></span>  
|`SyncLock`|<span data-ttu-id="e5371-134">Necessário para encerrar uma definição de bloco de `SyncLock` iniciada por uma instrução `SyncLock` correspondente.</span><span class="sxs-lookup"><span data-stu-id="e5371-134">Required to terminate a `SyncLock` block definition begun by a matching `SyncLock` statement.</span></span> <span data-ttu-id="e5371-135">Consulte a [instrução SyncLock](synclock-statement.md).</span><span class="sxs-lookup"><span data-stu-id="e5371-135">See [SyncLock Statement](synclock-statement.md).</span></span>  
|`Try`|<span data-ttu-id="e5371-136">Necessário para encerrar uma `Try`...`Catch`...`Finally` definição de bloco iniciada por uma instrução `Try` correspondente.</span><span class="sxs-lookup"><span data-stu-id="e5371-136">Required to terminate a `Try`...`Catch`...`Finally` block definition begun by a matching `Try` statement.</span></span> <span data-ttu-id="e5371-137">Consulte [tentar... Capturar... Instrução Finally](try-catch-finally-statement.md).</span><span class="sxs-lookup"><span data-stu-id="e5371-137">See [Try...Catch...Finally Statement](try-catch-finally-statement.md).</span></span>  
|`While`|<span data-ttu-id="e5371-138">Necessário para encerrar uma definição de loop `While` iniciada por uma instrução `While` correspondente.</span><span class="sxs-lookup"><span data-stu-id="e5371-138">Required to terminate a `While` loop definition begun by a matching `While` statement.</span></span> <span data-ttu-id="e5371-139">Consulte [while... Instrução End While](while-end-while-statement.md).</span><span class="sxs-lookup"><span data-stu-id="e5371-139">See [While...End While Statement](while-end-while-statement.md).</span></span>  
|`With`| <span data-ttu-id="e5371-140">Necessário para encerrar uma definição de bloco de `With` iniciada por uma instrução `With` correspondente.</span><span class="sxs-lookup"><span data-stu-id="e5371-140">Required to terminate a `With` block definition begun by a matching `With` statement.</span></span> <span data-ttu-id="e5371-141">Ver [com... Instrução End With](with-end-with-statement.md).</span><span class="sxs-lookup"><span data-stu-id="e5371-141">See [With...End With Statement](with-end-with-statement.md).</span></span>  
|||
  
## <a name="directives"></a><span data-ttu-id="e5371-142">Diretivas</span><span class="sxs-lookup"><span data-stu-id="e5371-142">Directives</span></span>

<span data-ttu-id="e5371-143">Quando precedido por um sinal numérico (`#`), a palavra-chave `End` encerra um bloco de pré-processamento introduzido pela diretiva correspondente.</span><span class="sxs-lookup"><span data-stu-id="e5371-143">When preceded by a number sign (`#`), the `End` keyword terminates a preprocessing block introduced by the corresponding directive.</span></span>  

```vb
#End ExternalSource
#End If
#End Region
```

|<span data-ttu-id="e5371-144">Parte</span><span class="sxs-lookup"><span data-stu-id="e5371-144">Part</span></span>|<span data-ttu-id="e5371-145">Descrição</span><span class="sxs-lookup"><span data-stu-id="e5371-145">Description</span></span>|
|---|---|
|`#End`|<span data-ttu-id="e5371-146">Necessária.</span><span class="sxs-lookup"><span data-stu-id="e5371-146">Required.</span></span> <span data-ttu-id="e5371-147">Encerra a definição do bloco de pré-processamento.</span><span class="sxs-lookup"><span data-stu-id="e5371-147">Terminates the definition of the preprocessing block.</span></span>|
|`ExternalSource`|<span data-ttu-id="e5371-148">Necessário para encerrar um bloco de origem externo iniciado por uma [diretiva de #ExternalSource](../directives/externalsource-directive.md)correspondente.</span><span class="sxs-lookup"><span data-stu-id="e5371-148">Required to terminate an external source block begun by a matching [#ExternalSource Directive](../directives/externalsource-directive.md).</span></span>|
|`If`|<span data-ttu-id="e5371-149">Necessário para encerrar um bloco de compilação condicional iniciado por uma diretiva de `#If` correspondente.</span><span class="sxs-lookup"><span data-stu-id="e5371-149">Required to terminate a conditional compilation block begun by a matching `#If` directive.</span></span> <span data-ttu-id="e5371-150">Consulte [#If... Em seguida,... #Else diretivas](../directives/if-then-else-directives.md).</span><span class="sxs-lookup"><span data-stu-id="e5371-150">See [#If...Then...#Else Directives](../directives/if-then-else-directives.md).</span></span>|
|`Region`|<span data-ttu-id="e5371-151">Necessário para encerrar um bloco de região de origem iniciado por uma [diretiva de #Region](../directives/region-directive.md)correspondente.</span><span class="sxs-lookup"><span data-stu-id="e5371-151">Required to terminate a source region block begun by a matching [#Region Directive](../directives/region-directive.md).</span></span>|
|||

## <a name="remarks"></a><span data-ttu-id="e5371-152">Comentários</span><span class="sxs-lookup"><span data-stu-id="e5371-152">Remarks</span></span>

<span data-ttu-id="e5371-153">A [instrução End](end-statement.md), sem uma palavra-chave adicional, encerra a execução imediatamente.</span><span class="sxs-lookup"><span data-stu-id="e5371-153">The [End Statement](end-statement.md), without an additional keyword, terminates execution immediately.</span></span>

## <a name="smart-device-developer-notes"></a><span data-ttu-id="e5371-154">Notas para desenvolvedores de dispositivos inteligentes</span><span class="sxs-lookup"><span data-stu-id="e5371-154">Smart Device Developer Notes</span></span>  

<span data-ttu-id="e5371-155">Não há suporte para a instrução `End`, sem uma palavra-chave adicional.</span><span class="sxs-lookup"><span data-stu-id="e5371-155">The `End` statement, without an additional keyword, is not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5371-156">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e5371-156">See also</span></span>

- [<span data-ttu-id="e5371-157">Instrução End</span><span class="sxs-lookup"><span data-stu-id="e5371-157">End Statement</span></span>](end-statement.md)
