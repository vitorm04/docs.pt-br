---
title: End &lt;palavra-chave&gt; Statement (Visual Basic) | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.EndDefinition
dev_langs:
- VB
helpviewer_keywords:
- End keyword
ms.assetid: 42d6e088-ab0f-4cda-88e8-fdce3e5fcf4f
caps.latest.revision: 17
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: dc1c456c71efb3cc6e60a8fdc77384e65975f110
ms.openlocfilehash: af38a5b9319a2930c81372488ace99cebba51108
ms.contentlocale: pt-br
ms.lasthandoff: 05/15/2017

---
# <a name="end-ltkeywordgt-statement-visual-basic"></a><span data-ttu-id="1b475-102">End &lt;palavra-chave&gt; Statement (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1b475-102">End &lt;keyword&gt; Statement (Visual Basic)</span></span>
<span data-ttu-id="1b475-103">Quando seguido por uma palavra-chave adicional, finaliza a definição do bloco de declaração introduzido por essa palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="1b475-103">When followed by an additional keyword, terminates the definition of the statement block introduced by that keyword.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1b475-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1b475-104">Syntax</span></span>  
  
```  
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
  
## <a name="parts"></a><span data-ttu-id="1b475-105">Partes</span><span class="sxs-lookup"><span data-stu-id="1b475-105">Parts</span></span>  
 `End`  
 <span data-ttu-id="1b475-106">Necessário.</span><span class="sxs-lookup"><span data-stu-id="1b475-106">Required.</span></span> <span data-ttu-id="1b475-107">Finaliza a definição do elemento de programação.</span><span class="sxs-lookup"><span data-stu-id="1b475-107">Terminates the definition of the programming element.</span></span>  
  
 `AddHandler`  
 <span data-ttu-id="1b475-108">Necessário para finalizar uma `AddHandler` acessador iniciado por uma `AddHandler` instrução em um personalizado [declaração de evento](../../../visual-basic/language-reference/statements/event-statement.md).</span><span class="sxs-lookup"><span data-stu-id="1b475-108">Required to terminate an `AddHandler` accessor begun by a matching `AddHandler` statement in a custom [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md).</span></span>  
  
 `Class`  
 <span data-ttu-id="1b475-109">Necessário para finalizar uma definição de classe iniciada por uma correspondência [instrução Class](../../../visual-basic/language-reference/statements/class-statement.md).</span><span class="sxs-lookup"><span data-stu-id="1b475-109">Required to terminate a class definition begun by a matching [Class Statement](../../../visual-basic/language-reference/statements/class-statement.md).</span></span>  
  
 `Enum`  
 <span data-ttu-id="1b475-110">Necessário para finalizar uma definição de enumeração iniciada por uma correspondência [instrução Enum](../../../visual-basic/language-reference/statements/enum-statement.md).</span><span class="sxs-lookup"><span data-stu-id="1b475-110">Required to terminate an enumeration definition begun by a matching [Enum Statement](../../../visual-basic/language-reference/statements/enum-statement.md).</span></span>  
  
 `Event`  
 <span data-ttu-id="1b475-111">Necessário para finalizar uma `Custom` iniciada por uma definição do evento [declaração de evento](../../../visual-basic/language-reference/statements/event-statement.md).</span><span class="sxs-lookup"><span data-stu-id="1b475-111">Required to terminate a `Custom` event definition begun by a matching [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md).</span></span>  
  
 `Function`  
 <span data-ttu-id="1b475-112">Necessário para finalizar uma `Function` iniciada por uma definição do procedimento [declaração de função](../../../visual-basic/language-reference/statements/function-statement.md).</span><span class="sxs-lookup"><span data-stu-id="1b475-112">Required to terminate a `Function` procedure definition begun by a matching [Function Statement](../../../visual-basic/language-reference/statements/function-statement.md).</span></span> <span data-ttu-id="1b475-113">Se a execução encontrar uma `End``Function` instrução, o controle retorna para o código de chamada.</span><span class="sxs-lookup"><span data-stu-id="1b475-113">If execution encounters an `End``Function` statement, control returns to the calling code.</span></span>  
  
 `Get`  
 <span data-ttu-id="1b475-114">Necessário para finalizar uma `Property` iniciada por uma definição do procedimento [obter instrução](../../../visual-basic/language-reference/statements/get-statement.md).</span><span class="sxs-lookup"><span data-stu-id="1b475-114">Required to terminate a `Property` procedure definition begun by a matching [Get Statement](../../../visual-basic/language-reference/statements/get-statement.md).</span></span> <span data-ttu-id="1b475-115">Se a execução encontrar uma `End``Get` declaração para a instrução solicitando o valor da propriedade.</span><span class="sxs-lookup"><span data-stu-id="1b475-115">If execution encounters an `End``Get` statement, control returns to the statement requesting the property's value.</span></span>  
  
 `If`  
 <span data-ttu-id="1b475-116">Necessário para finalizar uma `If`... `Then`... `Else` iniciada por uma correspondência `If` instrução.</span><span class="sxs-lookup"><span data-stu-id="1b475-116">Required to terminate an `If`...`Then`...`Else` block definition begun by a matching `If` statement.</span></span> <span data-ttu-id="1b475-117">Consulte [se... Then... Instrução else](../../../visual-basic/language-reference/statements/if-then-else-statement.md).</span><span class="sxs-lookup"><span data-stu-id="1b475-117">See [If...Then...Else Statement](../../../visual-basic/language-reference/statements/if-then-else-statement.md).</span></span>  
  
 `Interface`  
 <span data-ttu-id="1b475-118">Necessário para finalizar uma definição de interface iniciada por uma correspondência [instrução Interface](../../../visual-basic/language-reference/statements/interface-statement.md).</span><span class="sxs-lookup"><span data-stu-id="1b475-118">Required to terminate an interface definition begun by a matching [Interface Statement](../../../visual-basic/language-reference/statements/interface-statement.md).</span></span>  
  
 `Module`  
 <span data-ttu-id="1b475-119">Necessário para finalizar uma definição de módulo iniciada por uma correspondência [instrução Module](../../../visual-basic/language-reference/statements/module-statement.md).</span><span class="sxs-lookup"><span data-stu-id="1b475-119">Required to terminate a module definition begun by a matching [Module Statement](../../../visual-basic/language-reference/statements/module-statement.md).</span></span>  
  
 `Namespace`  
 <span data-ttu-id="1b475-120">Necessário para finalizar uma definição de namespace iniciada por uma [declaração de Namespace](../../../visual-basic/language-reference/statements/namespace-statement.md).</span><span class="sxs-lookup"><span data-stu-id="1b475-120">Required to terminate a namespace definition begun by a matching [Namespace Statement](../../../visual-basic/language-reference/statements/namespace-statement.md).</span></span>  
  
 `Operator`  
 <span data-ttu-id="1b475-121">Necessário para finalizar uma definição de operador iniciada por uma correspondência [instrução Operator](../../../visual-basic/language-reference/statements/operator-statement.md).</span><span class="sxs-lookup"><span data-stu-id="1b475-121">Required to terminate an operator definition begun by a matching [Operator Statement](../../../visual-basic/language-reference/statements/operator-statement.md).</span></span>  
  
 `Property`  
 <span data-ttu-id="1b475-122">Necessário para finalizar uma definição de propriedade iniciada por uma correspondência [declaração de propriedade](../../../visual-basic/language-reference/statements/property-statement.md).</span><span class="sxs-lookup"><span data-stu-id="1b475-122">Required to terminate a property definition begun by a matching [Property Statement](../../../visual-basic/language-reference/statements/property-statement.md).</span></span>  
  
 `RaiseEvent`  
 <span data-ttu-id="1b475-123">Necessário para finalizar uma `RaiseEvent` acessador iniciado por uma `RaiseEvent` instrução em um personalizado [declaração de evento](../../../visual-basic/language-reference/statements/event-statement.md).</span><span class="sxs-lookup"><span data-stu-id="1b475-123">Required to terminate a `RaiseEvent` accessor begun by a matching `RaiseEvent` statement in a custom [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md).</span></span>  
  
 `RemoveHandler`  
 <span data-ttu-id="1b475-124">Necessário para finalizar uma `RemoveHandler` acessador iniciado por uma `RemoveHandler` instrução em um personalizado [declaração de evento](../../../visual-basic/language-reference/statements/event-statement.md).</span><span class="sxs-lookup"><span data-stu-id="1b475-124">Required to terminate a `RemoveHandler` accessor begun by a matching `RemoveHandler` statement in a custom [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md).</span></span>  
  
 `Select`  
 <span data-ttu-id="1b475-125">Necessário para finalizar uma `Select`... `Case` iniciada por uma correspondência `Select` instrução.</span><span class="sxs-lookup"><span data-stu-id="1b475-125">Required to terminate a `Select`...`Case` block definition begun by a matching `Select` statement.</span></span> <span data-ttu-id="1b475-126">Consulte [selecione... Instrução Case](../../../visual-basic/language-reference/statements/select-case-statement.md).</span><span class="sxs-lookup"><span data-stu-id="1b475-126">See [Select...Case Statement](../../../visual-basic/language-reference/statements/select-case-statement.md).</span></span>  
  
 `Set`  
 <span data-ttu-id="1b475-127">Necessário para finalizar uma `Property` iniciada por uma definição do procedimento [instrução Set](../../../visual-basic/language-reference/statements/set-statement.md).</span><span class="sxs-lookup"><span data-stu-id="1b475-127">Required to terminate a `Property` procedure definition begun by a matching [Set Statement](../../../visual-basic/language-reference/statements/set-statement.md).</span></span> <span data-ttu-id="1b475-128">Se a execução encontrar uma `End``Set` declaração para a instrução Configurando o valor da propriedade.</span><span class="sxs-lookup"><span data-stu-id="1b475-128">If execution encounters an `End``Set` statement, control returns to the statement setting the property's value.</span></span>  
  
 `Structure`  
 <span data-ttu-id="1b475-129">Necessário para finalizar uma definição de estrutura iniciada por uma correspondência [declaração de estrutura](../../../visual-basic/language-reference/statements/structure-statement.md).</span><span class="sxs-lookup"><span data-stu-id="1b475-129">Required to terminate a structure definition begun by a matching [Structure Statement](../../../visual-basic/language-reference/statements/structure-statement.md).</span></span>  
  
 `Sub`  
 <span data-ttu-id="1b475-130">Necessário para finalizar uma `Sub` iniciada por uma definição do procedimento [instrução Sub](../../../visual-basic/language-reference/statements/sub-statement.md).</span><span class="sxs-lookup"><span data-stu-id="1b475-130">Required to terminate a `Sub` procedure definition begun by a matching [Sub Statement](../../../visual-basic/language-reference/statements/sub-statement.md).</span></span> <span data-ttu-id="1b475-131">Se a execução encontrar uma `End``Sub` instrução, o controle retorna para o código de chamada.</span><span class="sxs-lookup"><span data-stu-id="1b475-131">If execution encounters an `End``Sub` statement, control returns to the calling code.</span></span>  
  
 `SyncLock`  
 <span data-ttu-id="1b475-132">Necessário para finalizar uma `SyncLock` iniciada por uma correspondência `SyncLock` instrução.</span><span class="sxs-lookup"><span data-stu-id="1b475-132">Required to terminate a `SyncLock` block definition begun by a matching `SyncLock` statement.</span></span> <span data-ttu-id="1b475-133">Consulte [Instrução SyncLock](../../../visual-basic/language-reference/statements/synclock-statement.md).</span><span class="sxs-lookup"><span data-stu-id="1b475-133">See [SyncLock Statement](../../../visual-basic/language-reference/statements/synclock-statement.md).</span></span>  
  
 `Try`  
 <span data-ttu-id="1b475-134">Necessário para finalizar uma `Try`... `Catch`... `Finally` iniciada por uma correspondência `Try` instrução.</span><span class="sxs-lookup"><span data-stu-id="1b475-134">Required to terminate a `Try`...`Catch`...`Finally` block definition begun by a matching `Try` statement.</span></span> <span data-ttu-id="1b475-135">Consulte [Try... Catch... Instrução Finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span><span class="sxs-lookup"><span data-stu-id="1b475-135">See [Try...Catch...Finally Statement](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span></span>  
  
 `While`  
 <span data-ttu-id="1b475-136">Necessário para finalizar uma `While` definição iniciada por uma correspondência de loop `While` instrução.</span><span class="sxs-lookup"><span data-stu-id="1b475-136">Required to terminate a `While` loop definition begun by a matching `While` statement.</span></span> <span data-ttu-id="1b475-137">Consulte [enquanto... End While Statement](../../../visual-basic/language-reference/statements/while-end-while-statement.md).</span><span class="sxs-lookup"><span data-stu-id="1b475-137">See [While...End While Statement](../../../visual-basic/language-reference/statements/while-end-while-statement.md).</span></span>  
  
 `With`  
 <span data-ttu-id="1b475-138">Necessário para finalizar uma `With` iniciada por uma correspondência `With` instrução.</span><span class="sxs-lookup"><span data-stu-id="1b475-138">Required to terminate a `With` block definition begun by a matching `With` statement.</span></span> <span data-ttu-id="1b475-139">Consulte [com... Terminar com a instrução](../../../visual-basic/language-reference/statements/with-end-with-statement.md).</span><span class="sxs-lookup"><span data-stu-id="1b475-139">See [With...End With Statement](../../../visual-basic/language-reference/statements/with-end-with-statement.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1b475-140">Comentários</span><span class="sxs-lookup"><span data-stu-id="1b475-140">Remarks</span></span>  
 <span data-ttu-id="1b475-141">O [instrução End](../../../visual-basic/language-reference/statements/end-statement.md), sem uma palavra-chave adicional, finaliza a execução imediatamente.</span><span class="sxs-lookup"><span data-stu-id="1b475-141">The [End Statement](../../../visual-basic/language-reference/statements/end-statement.md), without an additional keyword, terminates execution immediately.</span></span>  
  
 <span data-ttu-id="1b475-142">Quando precedido por um sinal numérico (`#`), o `End` palavra-chave Finaliza um bloco de pré-processamento introduzido pela diretiva correspondente.</span><span class="sxs-lookup"><span data-stu-id="1b475-142">When preceded by a number sign (`#`), the `End` keyword terminates a preprocessing block introduced by the corresponding directive.</span></span>  
  
 `#End`  
 <span data-ttu-id="1b475-143">Necessário.</span><span class="sxs-lookup"><span data-stu-id="1b475-143">Required.</span></span> <span data-ttu-id="1b475-144">Finaliza a definição do bloco de pré-processamento.</span><span class="sxs-lookup"><span data-stu-id="1b475-144">Terminates the definition of the preprocessing block.</span></span>  
  
 `#ExternalSource`  
 <span data-ttu-id="1b475-145">Necessário para finalizar um bloco de origem externa iniciado por uma [#ExternalSource diretiva](../../../visual-basic/language-reference/directives/externalsource-directive.md).</span><span class="sxs-lookup"><span data-stu-id="1b475-145">Required to terminate an external source block begun by a matching [#ExternalSource Directive](../../../visual-basic/language-reference/directives/externalsource-directive.md).</span></span>  
  
 `#If`  
 <span data-ttu-id="1b475-146">Necessário para finalizar um bloco de compilação condicional iniciado por uma `#If` diretiva.</span><span class="sxs-lookup"><span data-stu-id="1b475-146">Required to terminate a conditional compilation block begun by a matching `#If` directive.</span></span> <span data-ttu-id="1b475-147">Consulte [#If... Then... #Else diretivas](../../../visual-basic/language-reference/directives/if-then-else-directives.md).</span><span class="sxs-lookup"><span data-stu-id="1b475-147">See [#If...Then...#Else Directives](../../../visual-basic/language-reference/directives/if-then-else-directives.md).</span></span>  
  
 `#Region`  
 <span data-ttu-id="1b475-148">Necessário para finalizar um bloco de região de origem iniciado por uma [#Region diretiva](../../../visual-basic/language-reference/directives/region-directive.md).</span><span class="sxs-lookup"><span data-stu-id="1b475-148">Required to terminate a source region block begun by a matching [#Region Directive](../../../visual-basic/language-reference/directives/region-directive.md).</span></span>  
  
## <a name="smart-device-developer-notes"></a><span data-ttu-id="1b475-149">Anotações de desenvolvedor de dispositivo inteligente</span><span class="sxs-lookup"><span data-stu-id="1b475-149">Smart Device Developer Notes</span></span>  
 <span data-ttu-id="1b475-150">O `End` instrução, sem uma palavra-chave adicional, não é suportada.</span><span class="sxs-lookup"><span data-stu-id="1b475-150">The `End` statement, without an additional keyword, is not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b475-151">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1b475-151">See Also</span></span>  
 [<span data-ttu-id="1b475-152">Instrução End</span><span class="sxs-lookup"><span data-stu-id="1b475-152">End Statement</span></span>](../../../visual-basic/language-reference/statements/end-statement.md)

