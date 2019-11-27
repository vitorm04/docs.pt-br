---
title: Cláusula Handles
ms.date: 07/20/2015
f1_keywords:
- Handles
- vb.Handles
helpviewer_keywords:
- Handles keyword [Visual Basic]
ms.assetid: 1b051c0e-f499-42f6-acb5-6f4f27824b40
ms.openlocfilehash: 2fecad919722f3da25c48f133a9c92b5e683d5e4
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345904"
---
# <a name="handles-clause-visual-basic"></a><span data-ttu-id="9b6d2-102">Cláusula Handles (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9b6d2-102">Handles Clause (Visual Basic)</span></span>
<span data-ttu-id="9b6d2-103">Declara que um procedimento manipula um evento especificado.</span><span class="sxs-lookup"><span data-stu-id="9b6d2-103">Declares that a procedure handles a specified event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9b6d2-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9b6d2-104">Syntax</span></span>  
  
```vb  
proceduredeclaration Handles eventlist  
```  
  
## <a name="parts"></a><span data-ttu-id="9b6d2-105">Partes</span><span class="sxs-lookup"><span data-stu-id="9b6d2-105">Parts</span></span>  
 `proceduredeclaration`  
 <span data-ttu-id="9b6d2-106">A declaração de procedimento `Sub` para o procedimento que manipulará o evento.</span><span class="sxs-lookup"><span data-stu-id="9b6d2-106">The `Sub` procedure declaration for the procedure that will handle the event.</span></span>  
  
 `eventlist`  
 <span data-ttu-id="9b6d2-107">Lista de eventos para `proceduredeclaration` manipular, separados por vírgulas.</span><span class="sxs-lookup"><span data-stu-id="9b6d2-107">List of the events for `proceduredeclaration` to handle, separated by commas.</span></span> <span data-ttu-id="9b6d2-108">Os eventos devem ser gerados pela classe base para a classe atual ou por um objeto declarado usando a palavra-chave `WithEvents`.</span><span class="sxs-lookup"><span data-stu-id="9b6d2-108">The events must be raised by either the base class for the current class, or by an object declared using the `WithEvents` keyword.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9b6d2-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="9b6d2-109">Remarks</span></span>  
 <span data-ttu-id="9b6d2-110">Use a palavra-chave `Handles` no final de uma declaração de procedimento para fazer com que ele manipule eventos gerados por uma variável de objeto declarada usando a palavra-chave `WithEvents`.</span><span class="sxs-lookup"><span data-stu-id="9b6d2-110">Use the `Handles` keyword at the end of a procedure declaration to cause it to handle events raised by an object variable declared using the `WithEvents` keyword.</span></span> <span data-ttu-id="9b6d2-111">A palavra-chave `Handles` também pode ser usada em uma classe derivada para manipular eventos de uma classe base.</span><span class="sxs-lookup"><span data-stu-id="9b6d2-111">The `Handles` keyword can also be used in a derived class to handle events from a base class.</span></span>  
  
 <span data-ttu-id="9b6d2-112">A palavra-chave `Handles` e a instrução `AddHandler` permitem que você especifique que procedimentos específicos manipulam eventos específicos, mas há diferenças.</span><span class="sxs-lookup"><span data-stu-id="9b6d2-112">The `Handles` keyword and the `AddHandler` statement both allow you to specify that particular procedures handle particular events, but there are differences.</span></span> <span data-ttu-id="9b6d2-113">Use a palavra-chave `Handles` ao definir um procedimento para especificar que ele trata de um evento específico.</span><span class="sxs-lookup"><span data-stu-id="9b6d2-113">Use the `Handles` keyword when defining a procedure to specify that it handles a particular event.</span></span> <span data-ttu-id="9b6d2-114">A instrução `AddHandler` conecta procedimentos a eventos em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="9b6d2-114">The `AddHandler` statement connects procedures to events at run time.</span></span> <span data-ttu-id="9b6d2-115">Para obter mais informações, consulte [instrução AddHandler](../../../visual-basic/language-reference/statements/addhandler-statement.md).</span><span class="sxs-lookup"><span data-stu-id="9b6d2-115">For more information, see [AddHandler Statement](../../../visual-basic/language-reference/statements/addhandler-statement.md).</span></span>  
  
 <span data-ttu-id="9b6d2-116">Para eventos personalizados, o aplicativo invoca o acessador de `AddHandler` do evento ao adicionar o procedimento como um manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="9b6d2-116">For custom events, the application invokes the event's `AddHandler` accessor when it adds the procedure as an event handler.</span></span> <span data-ttu-id="9b6d2-117">Para obter mais informações sobre eventos personalizados, consulte [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md).</span><span class="sxs-lookup"><span data-stu-id="9b6d2-117">For more information on custom events, see [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="9b6d2-118">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9b6d2-118">Example</span></span>  
 [!code-vb[VbVbalrEvents#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#2)]  
  
 <span data-ttu-id="9b6d2-119">O exemplo a seguir demonstra como uma classe derivada pode usar a instrução `Handles` para manipular um evento de uma classe base.</span><span class="sxs-lookup"><span data-stu-id="9b6d2-119">The following example demonstrates how a derived class can use the `Handles` statement to handle an event from a base class.</span></span>  
  
 [!code-vb[VbVbalrEvents#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#3)]  
  
## <a name="example"></a><span data-ttu-id="9b6d2-120">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9b6d2-120">Example</span></span>  
 <span data-ttu-id="9b6d2-121">O exemplo a seguir contém dois manipuladores de eventos de botão para um projeto de **aplicativo WPF** .</span><span class="sxs-lookup"><span data-stu-id="9b6d2-121">The following example contains two button event handlers for a **WPF Application** project.</span></span>  
  
 [!code-vb[VbVbalrEvents#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/class3.vb#41)]  
  
## <a name="example"></a><span data-ttu-id="9b6d2-122">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9b6d2-122">Example</span></span>  
 <span data-ttu-id="9b6d2-123">O exemplo a seguir é equivalente ao exemplo anterior.</span><span class="sxs-lookup"><span data-stu-id="9b6d2-123">The following example is equivalent to the previous example.</span></span> <span data-ttu-id="9b6d2-124">O `eventlist` na cláusula `Handles` contém os eventos para ambos os botões.</span><span class="sxs-lookup"><span data-stu-id="9b6d2-124">The `eventlist` in the `Handles` clause contains the events for both buttons.</span></span>  
  
 [!code-vb[VbVbalrEvents#42](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/class3.vb#42)]  
  
## <a name="see-also"></a><span data-ttu-id="9b6d2-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9b6d2-125">See also</span></span>

- [<span data-ttu-id="9b6d2-126">WithEvents</span><span class="sxs-lookup"><span data-stu-id="9b6d2-126">WithEvents</span></span>](../../../visual-basic/language-reference/modifiers/withevents.md)
- [<span data-ttu-id="9b6d2-127">Instrução AddHandler</span><span class="sxs-lookup"><span data-stu-id="9b6d2-127">AddHandler Statement</span></span>](../../../visual-basic/language-reference/statements/addhandler-statement.md)
- [<span data-ttu-id="9b6d2-128">Instrução RemoveHandler</span><span class="sxs-lookup"><span data-stu-id="9b6d2-128">RemoveHandler Statement</span></span>](../../../visual-basic/language-reference/statements/removehandler-statement.md)
- [<span data-ttu-id="9b6d2-129">Instrução Event</span><span class="sxs-lookup"><span data-stu-id="9b6d2-129">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)
- [<span data-ttu-id="9b6d2-130">Instrução RaiseEvent</span><span class="sxs-lookup"><span data-stu-id="9b6d2-130">RaiseEvent Statement</span></span>](../../../visual-basic/language-reference/statements/raiseevent-statement.md)
- [<span data-ttu-id="9b6d2-131">Eventos</span><span class="sxs-lookup"><span data-stu-id="9b6d2-131">Events</span></span>](../../../visual-basic/programming-guide/language-features/events/index.md)
