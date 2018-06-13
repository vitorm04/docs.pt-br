---
title: Como declarar eventos personalizados para conservar memória (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- declaring events [Visual Basic], custom
- events [Visual Basic], custom
- custom events [Visual Basic]
ms.assetid: 87ebee87-260c-462f-979c-407874debd19
ms.openlocfilehash: d19c91d66e458ca2317dc049d517b92fa7406ef6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33647161"
---
# <a name="how-to-declare-custom-events-to-conserve-memory-visual-basic"></a><span data-ttu-id="f277c-102">Como declarar eventos personalizados para conservar memória (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f277c-102">How to: Declare Custom Events To Conserve Memory (Visual Basic)</span></span>
<span data-ttu-id="f277c-103">Há várias circunstâncias quando é importante que um aplicativo mantenha seu uso de memória baixa.</span><span class="sxs-lookup"><span data-stu-id="f277c-103">There are several circumstances when it is important that an application keep its memory usage low.</span></span> <span data-ttu-id="f277c-104">Eventos personalizados permitem que o aplicativo use memória somente para os eventos que trata.</span><span class="sxs-lookup"><span data-stu-id="f277c-104">Custom events allow the application to use memory only for the events that it handles.</span></span>  
  
 <span data-ttu-id="f277c-105">Por padrão, quando uma classe declara um evento, o compilador aloca memória para um campo armazenar as informações do evento.</span><span class="sxs-lookup"><span data-stu-id="f277c-105">By default, when a class declares an event, the compiler allocates memory for a field to store the event information.</span></span> <span data-ttu-id="f277c-106">Se uma classe tem muitos eventos não utilizados, eles desnecessariamente ocupam de memória.</span><span class="sxs-lookup"><span data-stu-id="f277c-106">If a class has many unused events, they needlessly take up memory.</span></span>  
  
 <span data-ttu-id="f277c-107">Em vez de usar a implementação padrão de eventos que o Visual Basic fornece, você pode usar eventos personalizados para gerenciar o uso de memória mais cuidadosamente.</span><span class="sxs-lookup"><span data-stu-id="f277c-107">Instead of using the default implementation of events that Visual Basic provides, you can use custom events to manage the memory usage more carefully.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f277c-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f277c-108">Example</span></span>  
 <span data-ttu-id="f277c-109">Neste exemplo, a classe usa uma instância do <xref:System.ComponentModel.EventHandlerList> classe, armazenado no `Events` campo, para armazenar informações sobre os eventos em uso.</span><span class="sxs-lookup"><span data-stu-id="f277c-109">In this example, the class uses one instance of the <xref:System.ComponentModel.EventHandlerList> class, stored in the `Events` field, to store information about the events in use.</span></span> <span data-ttu-id="f277c-110">O <xref:System.ComponentModel.EventHandlerList> classe é uma classe lista otimizada projetada para armazenar representantes.</span><span class="sxs-lookup"><span data-stu-id="f277c-110">The <xref:System.ComponentModel.EventHandlerList> class is an optimized list class designed to hold delegates.</span></span>  
  
 <span data-ttu-id="f277c-111">Todos os eventos na classe usam o `Events` campo para controlar quais métodos estão manipulando cada evento.</span><span class="sxs-lookup"><span data-stu-id="f277c-111">All events in the class use the `Events` field to keep track of what methods are handling each event.</span></span>  
  
 [!code-vb[VbVbalrEvents#22](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-custom-events-to-conserve-memory_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="f277c-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f277c-112">See Also</span></span>  
 <xref:System.ComponentModel.EventHandlerList>  
 [<span data-ttu-id="f277c-113">Eventos</span><span class="sxs-lookup"><span data-stu-id="f277c-113">Events</span></span>](../../../../visual-basic/programming-guide/language-features/events/index.md)  
 [<span data-ttu-id="f277c-114">Como declarar eventos personalizados para evitar bloqueio</span><span class="sxs-lookup"><span data-stu-id="f277c-114">How to: Declare Custom Events To Avoid Blocking</span></span>](../../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-avoid-blocking.md)
