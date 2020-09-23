---
title: Como declarar eventos personalizados para conservar memória
ms.date: 07/20/2015
helpviewer_keywords:
- declaring events [Visual Basic], custom
- events [Visual Basic], custom
- custom events [Visual Basic]
ms.assetid: 87ebee87-260c-462f-979c-407874debd19
ms.openlocfilehash: 78934e3e5ae7d5a3f5867c99a9f1db760c65ecbf
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91075116"
---
# <a name="how-to-declare-custom-events-to-conserve-memory-visual-basic"></a><span data-ttu-id="07574-102">Como declarar eventos personalizados para conservar memória (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="07574-102">How to: Declare Custom Events To Conserve Memory (Visual Basic)</span></span>

<span data-ttu-id="07574-103">Há várias circunstâncias em que é importante que um aplicativo Mantenha seu uso de memória baixo.</span><span class="sxs-lookup"><span data-stu-id="07574-103">There are several circumstances when it is important that an application keep its memory usage low.</span></span> <span data-ttu-id="07574-104">Os eventos personalizados permitem que o aplicativo use a memória apenas para os eventos que ele manipula.</span><span class="sxs-lookup"><span data-stu-id="07574-104">Custom events allow the application to use memory only for the events that it handles.</span></span>  
  
 <span data-ttu-id="07574-105">Por padrão, quando uma classe declara um evento, o compilador aloca memória para um campo para armazenar as informações do evento.</span><span class="sxs-lookup"><span data-stu-id="07574-105">By default, when a class declares an event, the compiler allocates memory for a field to store the event information.</span></span> <span data-ttu-id="07574-106">Se uma classe tiver muitos eventos não utilizados, eles ocupam desnecessariamente a memória.</span><span class="sxs-lookup"><span data-stu-id="07574-106">If a class has many unused events, they needlessly take up memory.</span></span>  
  
 <span data-ttu-id="07574-107">Em vez de usar a implementação padrão de eventos que Visual Basic fornece, você pode usar eventos personalizados para gerenciar o uso de memória com mais cuidado.</span><span class="sxs-lookup"><span data-stu-id="07574-107">Instead of using the default implementation of events that Visual Basic provides, you can use custom events to manage the memory usage more carefully.</span></span>  
  
## <a name="example"></a><span data-ttu-id="07574-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="07574-108">Example</span></span>  

 <span data-ttu-id="07574-109">Neste exemplo, a classe usa uma instância da <xref:System.ComponentModel.EventHandlerList> classe, armazenada no `Events` campo, para armazenar informações sobre os eventos em uso.</span><span class="sxs-lookup"><span data-stu-id="07574-109">In this example, the class uses one instance of the <xref:System.ComponentModel.EventHandlerList> class, stored in the `Events` field, to store information about the events in use.</span></span> <span data-ttu-id="07574-110">A <xref:System.ComponentModel.EventHandlerList> classe é uma classe de lista otimizada projetada para manter delegados.</span><span class="sxs-lookup"><span data-stu-id="07574-110">The <xref:System.ComponentModel.EventHandlerList> class is an optimized list class designed to hold delegates.</span></span>  
  
 <span data-ttu-id="07574-111">Todos os eventos na classe usam o `Events` campo para controlar quais métodos estão manipulando cada evento.</span><span class="sxs-lookup"><span data-stu-id="07574-111">All events in the class use the `Events` field to keep track of what methods are handling each event.</span></span>  
  
 [!code-vb[VbVbalrEvents#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#22)]  
  
## <a name="see-also"></a><span data-ttu-id="07574-112">Confira também</span><span class="sxs-lookup"><span data-stu-id="07574-112">See also</span></span>

- <xref:System.ComponentModel.EventHandlerList>
- [<span data-ttu-id="07574-113">Eventos</span><span class="sxs-lookup"><span data-stu-id="07574-113">Events</span></span>](index.md)
- [<span data-ttu-id="07574-114">Como declarar eventos personalizados para evitar bloqueio</span><span class="sxs-lookup"><span data-stu-id="07574-114">How to: Declare Custom Events To Avoid Blocking</span></span>](how-to-declare-custom-events-to-avoid-blocking.md)
