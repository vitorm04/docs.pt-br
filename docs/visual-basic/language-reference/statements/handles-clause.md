---
title: Cláusula Handles
ms.date: 07/20/2015
f1_keywords:
- Handles
- vb.Handles
helpviewer_keywords:
- Handles keyword [Visual Basic]
ms.assetid: 1b051c0e-f499-42f6-acb5-6f4f27824b40
ms.openlocfilehash: 347f521267d4fd954ac359ab25ed5810cfd71d34
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90873254"
---
# <a name="handles-clause-visual-basic"></a><span data-ttu-id="ca61f-102">Cláusula Handles (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ca61f-102">Handles Clause (Visual Basic)</span></span>

<span data-ttu-id="ca61f-103">Declara que um procedimento manipula um evento especificado.</span><span class="sxs-lookup"><span data-stu-id="ca61f-103">Declares that a procedure handles a specified event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ca61f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ca61f-104">Syntax</span></span>  
  
```vb  
proceduredeclaration Handles eventlist  
```  
  
## <a name="parts"></a><span data-ttu-id="ca61f-105">Partes</span><span class="sxs-lookup"><span data-stu-id="ca61f-105">Parts</span></span>  

 `proceduredeclaration`  
 <span data-ttu-id="ca61f-106">A `Sub` declaração de procedimento para o procedimento que manipulará o evento.</span><span class="sxs-lookup"><span data-stu-id="ca61f-106">The `Sub` procedure declaration for the procedure that will handle the event.</span></span>  
  
 `eventlist`  
 <span data-ttu-id="ca61f-107">Lista dos eventos `proceduredeclaration` a serem tratados, separados por vírgulas.</span><span class="sxs-lookup"><span data-stu-id="ca61f-107">List of the events for `proceduredeclaration` to handle, separated by commas.</span></span> <span data-ttu-id="ca61f-108">Os eventos devem ser gerados pela classe base para a classe atual ou por um objeto declarado usando a `WithEvents` palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="ca61f-108">The events must be raised by either the base class for the current class, or by an object declared using the `WithEvents` keyword.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ca61f-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="ca61f-109">Remarks</span></span>  

 <span data-ttu-id="ca61f-110">Use a `Handles` palavra-chave no final de uma declaração de procedimento para fazer com que ela manipule eventos gerados por uma variável de objeto declarada usando a `WithEvents` palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="ca61f-110">Use the `Handles` keyword at the end of a procedure declaration to cause it to handle events raised by an object variable declared using the `WithEvents` keyword.</span></span> <span data-ttu-id="ca61f-111">A `Handles` palavra-chave também pode ser usada em uma classe derivada para manipular eventos de uma classe base.</span><span class="sxs-lookup"><span data-stu-id="ca61f-111">The `Handles` keyword can also be used in a derived class to handle events from a base class.</span></span>  
  
 <span data-ttu-id="ca61f-112">A `Handles` palavra-chave e a `AddHandler` instrução permitem que você especifique que procedimentos específicos manipulam eventos específicos, mas há diferenças.</span><span class="sxs-lookup"><span data-stu-id="ca61f-112">The `Handles` keyword and the `AddHandler` statement both allow you to specify that particular procedures handle particular events, but there are differences.</span></span> <span data-ttu-id="ca61f-113">Use a `Handles` palavra-chave ao definir um procedimento para especificar que ele trata de um evento específico.</span><span class="sxs-lookup"><span data-stu-id="ca61f-113">Use the `Handles` keyword when defining a procedure to specify that it handles a particular event.</span></span> <span data-ttu-id="ca61f-114">A `AddHandler` instrução conecta procedimentos a eventos em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="ca61f-114">The `AddHandler` statement connects procedures to events at run time.</span></span> <span data-ttu-id="ca61f-115">Para obter mais informações, consulte [instrução AddHandler](addhandler-statement.md).</span><span class="sxs-lookup"><span data-stu-id="ca61f-115">For more information, see [AddHandler Statement](addhandler-statement.md).</span></span>  
  
 <span data-ttu-id="ca61f-116">Para eventos personalizados, o aplicativo invoca o `AddHandler` acessador do evento quando ele adiciona o procedimento como um manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="ca61f-116">For custom events, the application invokes the event's `AddHandler` accessor when it adds the procedure as an event handler.</span></span> <span data-ttu-id="ca61f-117">Para obter mais informações sobre eventos personalizados, consulte [Event Statement](event-statement.md).</span><span class="sxs-lookup"><span data-stu-id="ca61f-117">For more information on custom events, see [Event Statement](event-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ca61f-118">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ca61f-118">Example</span></span>  

 [!code-vb[VbVbalrEvents#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#2)]  
  
 <span data-ttu-id="ca61f-119">O exemplo a seguir demonstra como uma classe derivada pode usar a `Handles` instrução para manipular um evento de uma classe base.</span><span class="sxs-lookup"><span data-stu-id="ca61f-119">The following example demonstrates how a derived class can use the `Handles` statement to handle an event from a base class.</span></span>  
  
 [!code-vb[VbVbalrEvents#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#3)]  
  
## <a name="example"></a><span data-ttu-id="ca61f-120">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ca61f-120">Example</span></span>  

 <span data-ttu-id="ca61f-121">O exemplo a seguir contém dois manipuladores de eventos de botão para um projeto de **aplicativo WPF** .</span><span class="sxs-lookup"><span data-stu-id="ca61f-121">The following example contains two button event handlers for a **WPF Application** project.</span></span>  
  
 [!code-vb[VbVbalrEvents#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/class3.vb#41)]  
  
## <a name="example"></a><span data-ttu-id="ca61f-122">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ca61f-122">Example</span></span>  

 <span data-ttu-id="ca61f-123">O exemplo a seguir é equivalente ao exemplo anterior.</span><span class="sxs-lookup"><span data-stu-id="ca61f-123">The following example is equivalent to the previous example.</span></span> <span data-ttu-id="ca61f-124">O `eventlist` na `Handles` cláusula contém os eventos para ambos os botões.</span><span class="sxs-lookup"><span data-stu-id="ca61f-124">The `eventlist` in the `Handles` clause contains the events for both buttons.</span></span>  
  
 [!code-vb[VbVbalrEvents#42](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/class3.vb#42)]  
  
## <a name="see-also"></a><span data-ttu-id="ca61f-125">Confira também</span><span class="sxs-lookup"><span data-stu-id="ca61f-125">See also</span></span>

- [<span data-ttu-id="ca61f-126">WithEvents</span><span class="sxs-lookup"><span data-stu-id="ca61f-126">WithEvents</span></span>](../modifiers/withevents.md)
- [<span data-ttu-id="ca61f-127">Instrução AddHandler</span><span class="sxs-lookup"><span data-stu-id="ca61f-127">AddHandler Statement</span></span>](addhandler-statement.md)
- [<span data-ttu-id="ca61f-128">Instrução RemoveHandler</span><span class="sxs-lookup"><span data-stu-id="ca61f-128">RemoveHandler Statement</span></span>](removehandler-statement.md)
- [<span data-ttu-id="ca61f-129">Instrução Event</span><span class="sxs-lookup"><span data-stu-id="ca61f-129">Event Statement</span></span>](event-statement.md)
- [<span data-ttu-id="ca61f-130">Instrução RaiseEvent</span><span class="sxs-lookup"><span data-stu-id="ca61f-130">RaiseEvent Statement</span></span>](raiseevent-statement.md)
- [<span data-ttu-id="ca61f-131">Eventos</span><span class="sxs-lookup"><span data-stu-id="ca61f-131">Events</span></span>](../../programming-guide/language-features/events/index.md)
