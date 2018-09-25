---
title: Criando manipuladores de eventos no Windows Forms
ms.date: 03/30/2017
helpviewer_keywords:
- event handling [Windows Forms]
- Windows Forms controls, event handling
- Windows Forms, event handling
- events [Windows Forms], event handlers
- event handlers [Windows Forms]
ms.assetid: 6514e530-c6b8-489c-a8d2-eda7b7072701
ms.openlocfilehash: 9095946d52360c69fd6c4dd6285039fb3e1874d5
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47082461"
---
# <a name="creating-event-handlers-in-windows-forms"></a><span data-ttu-id="eba64-102">Criando manipuladores de eventos no Windows Forms</span><span class="sxs-lookup"><span data-stu-id="eba64-102">Creating Event Handlers in Windows Forms</span></span>
<span data-ttu-id="eba64-103">Um manipulador de eventos é um procedimento no seu código que determina quais ações são executadas quando ocorre um evento, por exemplo, quando o usuário clica em um botão ou uma fila de mensagens recebe uma mensagem.</span><span class="sxs-lookup"><span data-stu-id="eba64-103">An event handler is a procedure in your code that determines what actions are performed when an event occurs, such as when the user clicks a button or a message queue receives a message.</span></span> <span data-ttu-id="eba64-104">Quando um evento é gerado, o manipulador ou manipuladores de eventos que receberão o evento são executados.</span><span class="sxs-lookup"><span data-stu-id="eba64-104">When an event is raised, the event handler or handlers that receive the event are executed.</span></span> <span data-ttu-id="eba64-105">Os eventos podem ser atribuídos a vários manipuladores e os métodos que manipulam os eventos particulares podem ser alterados dinamicamente.</span><span class="sxs-lookup"><span data-stu-id="eba64-105">Events can be assigned to multiple handlers, and the methods that handle particular events can be changed dynamically.</span></span> <span data-ttu-id="eba64-106">Você também pode usar o Designer de Formulários do Windows para criar manipuladores de eventos.</span><span class="sxs-lookup"><span data-stu-id="eba64-106">You can also use the Windows Forms Designer to create event handlers.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="eba64-107">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="eba64-107">In This Section</span></span>  
 [<span data-ttu-id="eba64-108">Visão geral de eventos</span><span class="sxs-lookup"><span data-stu-id="eba64-108">Events Overview</span></span>](../../../docs/framework/winforms/events-overview-windows-forms.md)  
 <span data-ttu-id="eba64-109">Explica o modelo de evento e a função das classes delegate.</span><span class="sxs-lookup"><span data-stu-id="eba64-109">Explains the event model and the role of delegates.</span></span>  
  
 [<span data-ttu-id="eba64-110">Visão geral de manipuladores de eventos</span><span class="sxs-lookup"><span data-stu-id="eba64-110">Event Handlers Overview</span></span>](../../../docs/framework/winforms/event-handlers-overview-windows-forms.md)  
 <span data-ttu-id="eba64-111">Descreve como manipular eventos.</span><span class="sxs-lookup"><span data-stu-id="eba64-111">Describes how to handle events.</span></span>  
  
 [<span data-ttu-id="eba64-112">Como criar manipuladores de eventos em tempo de execução para Windows Forms</span><span class="sxs-lookup"><span data-stu-id="eba64-112">How to: Create Event Handlers at Run Time for Windows Forms</span></span>](../../../docs/framework/winforms/how-to-create-event-handlers-at-run-time-for-windows-forms.md)  
 <span data-ttu-id="eba64-113">Fornece instruções para responder a eventos de sistema ou de usuário de forma dinâmica.</span><span class="sxs-lookup"><span data-stu-id="eba64-113">Gives directions for responding to system or user events dynamically.</span></span>  
  
 [<span data-ttu-id="eba64-114">Como conectar vários eventos a um único manipulador de eventos nos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="eba64-114">How to: Connect Multiple Events to a Single Event Handler in Windows Forms</span></span>](../../../docs/framework/winforms/how-to-connect-multiple-events-to-a-single-event-handler-in-windows-forms.md)  
 <span data-ttu-id="eba64-115">Fornece instruções para atribuir a mesma funcionalidade a vários controles por meio de eventos.</span><span class="sxs-lookup"><span data-stu-id="eba64-115">Gives directions for assigning the same functionality to multiple controls through events.</span></span>  
  
 [<span data-ttu-id="eba64-116">Ordem de eventos nos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="eba64-116">Order of Events in Windows Forms</span></span>](../../../docs/framework/winforms/order-of-events-in-windows-forms.md)  
 <span data-ttu-id="eba64-117">Descreve a ordem em que os eventos são gerados em controles Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="eba64-117">Describes the order in which events are raised in Windows Forms controls.</span></span>  
  
 [<span data-ttu-id="eba64-118">Como: criar manipuladores de eventos usando o Designer</span><span class="sxs-lookup"><span data-stu-id="eba64-118">How to: Create Event Handlers Using the Designer</span></span>](https://msdn.microsoft.com/library/8461e9b8-14e8-406f-936e-3726732b23d2)  
 <span data-ttu-id="eba64-119">Descreve como usar o Designer de Formulários do Windows para criar manipuladores de eventos.</span><span class="sxs-lookup"><span data-stu-id="eba64-119">Describes how to use the Windows Forms Designer to create event handlers.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="eba64-120">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="eba64-120">Related Sections</span></span>  
 [<span data-ttu-id="eba64-121">Eventos</span><span class="sxs-lookup"><span data-stu-id="eba64-121">Events</span></span>](../../../docs/standard/events/index.md)  
 <span data-ttu-id="eba64-122">Fornece links para tópicos sobre tratamento e geração de eventos usando o [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="eba64-122">Provides links to topics on handling and raising events using the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].</span></span>  
  
 [<span data-ttu-id="eba64-123">Solucionando problemas de manipuladores de eventos herdados no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="eba64-123">Troubleshooting Inherited Event Handlers in Visual Basic</span></span>](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)  
 <span data-ttu-id="eba64-124">Lista problemas comuns que ocorrem com os manipuladores de eventos em componentes herdados.</span><span class="sxs-lookup"><span data-stu-id="eba64-124">Lists common issues that occur with event handlers in inherited components.</span></span>
