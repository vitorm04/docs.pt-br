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
ms.openlocfilehash: e90e1d6643a30c1d2f4438e77317a2348b07fd71
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2019
ms.locfileid: "65882421"
---
# <a name="creating-event-handlers-in-windows-forms"></a><span data-ttu-id="93f0c-102">Criando manipuladores de eventos no Windows Forms</span><span class="sxs-lookup"><span data-stu-id="93f0c-102">Creating Event Handlers in Windows Forms</span></span>

<span data-ttu-id="93f0c-103">Um manipulador de eventos é um procedimento no seu código que determina quais ações são executadas quando ocorre um evento, por exemplo, quando o usuário clica em um botão ou uma fila de mensagens recebe uma mensagem.</span><span class="sxs-lookup"><span data-stu-id="93f0c-103">An event handler is a procedure in your code that determines what actions are performed when an event occurs, such as when the user clicks a button or a message queue receives a message.</span></span> <span data-ttu-id="93f0c-104">Quando um evento é gerado, o manipulador ou manipuladores de eventos que receberão o evento são executados.</span><span class="sxs-lookup"><span data-stu-id="93f0c-104">When an event is raised, the event handler or handlers that receive the event are executed.</span></span> <span data-ttu-id="93f0c-105">Os eventos podem ser atribuídos a vários manipuladores e os métodos que manipulam os eventos particulares podem ser alterados dinamicamente.</span><span class="sxs-lookup"><span data-stu-id="93f0c-105">Events can be assigned to multiple handlers, and the methods that handle particular events can be changed dynamically.</span></span> <span data-ttu-id="93f0c-106">Você também pode usar o Designer de formulários do Windows no Visual Studio para criar manipuladores de eventos.</span><span class="sxs-lookup"><span data-stu-id="93f0c-106">You can also use the Windows Forms Designer in Visual Studio to create event handlers.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="93f0c-107">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="93f0c-107">In This Section</span></span>

 <span data-ttu-id="93f0c-108">[Visão geral de eventos](events-overview-windows-forms.md)\\</span><span class="sxs-lookup"><span data-stu-id="93f0c-108">[Events Overview](events-overview-windows-forms.md)\\</span></span>
 <span data-ttu-id="93f0c-109">Explica o modelo de evento e a função das classes delegate.</span><span class="sxs-lookup"><span data-stu-id="93f0c-109">Explains the event model and the role of delegates.</span></span>

 <span data-ttu-id="93f0c-110">[Visão geral do manipulador de eventos](event-handlers-overview-windows-forms.md)\\</span><span class="sxs-lookup"><span data-stu-id="93f0c-110">[Event Handlers Overview](event-handlers-overview-windows-forms.md)\\</span></span>
 <span data-ttu-id="93f0c-111">Descreve como manipular eventos.</span><span class="sxs-lookup"><span data-stu-id="93f0c-111">Describes how to handle events.</span></span>

 <span data-ttu-id="93f0c-112">[Como: Criar manipuladores de eventos em tempo de execução para formulários do Windows](how-to-create-event-handlers-at-run-time-for-windows-forms.md)\\</span><span class="sxs-lookup"><span data-stu-id="93f0c-112">[How to: Create Event Handlers at Run Time for Windows Forms](how-to-create-event-handlers-at-run-time-for-windows-forms.md)\\</span></span>
 <span data-ttu-id="93f0c-113">Fornece instruções para responder a eventos de sistema ou de usuário de forma dinâmica.</span><span class="sxs-lookup"><span data-stu-id="93f0c-113">Gives directions for responding to system or user events dynamically.</span></span>

 <span data-ttu-id="93f0c-114">[Como: Conectar vários eventos a um único manipulador de eventos nos Windows Forms](how-to-connect-multiple-events-to-a-single-event-handler-in-windows-forms.md)\\</span><span class="sxs-lookup"><span data-stu-id="93f0c-114">[How to: Connect Multiple Events to a Single Event Handler in Windows Forms](how-to-connect-multiple-events-to-a-single-event-handler-in-windows-forms.md)\\</span></span>
 <span data-ttu-id="93f0c-115">Fornece instruções para atribuir a mesma funcionalidade a vários controles por meio de eventos.</span><span class="sxs-lookup"><span data-stu-id="93f0c-115">Gives directions for assigning the same functionality to multiple controls through events.</span></span>

 <span data-ttu-id="93f0c-116">[Ordem de eventos nos Windows Forms](order-of-events-in-windows-forms.md)\\</span><span class="sxs-lookup"><span data-stu-id="93f0c-116">[Order of Events in Windows Forms](order-of-events-in-windows-forms.md)\\</span></span>
 <span data-ttu-id="93f0c-117">Descreve a ordem em que os eventos são gerados em controles Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="93f0c-117">Describes the order in which events are raised in Windows Forms controls.</span></span>

 <span data-ttu-id="93f0c-118">[Como: Criar manipuladores de eventos usando o Designer](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/zwwsdtbk(v=vs.100)) descreve como usar o Designer de formulários do Windows para criar manipuladores de eventos.</span><span class="sxs-lookup"><span data-stu-id="93f0c-118">[How to: Create Event Handlers Using the Designer](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/zwwsdtbk(v=vs.100)) Describes how to use the Windows Forms Designer to create event handlers.</span></span>

## <a name="related-sections"></a><span data-ttu-id="93f0c-119">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="93f0c-119">Related Sections</span></span>

 <span data-ttu-id="93f0c-120">[Eventos](../../standard/events/index.md)\\</span><span class="sxs-lookup"><span data-stu-id="93f0c-120">[Events](../../standard/events/index.md)\\</span></span>
 <span data-ttu-id="93f0c-121">Fornece links para tópicos sobre tratamento e geração de eventos usando o .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="93f0c-121">Provides links to topics on handling and raising events using the .NET Framework.</span></span>

 <span data-ttu-id="93f0c-122">[Solução de problemas de manipuladores de eventos herdados no Visual Basic](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)\\</span><span class="sxs-lookup"><span data-stu-id="93f0c-122">[Troubleshooting Inherited Event Handlers in Visual Basic](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)\\</span></span>
 <span data-ttu-id="93f0c-123">Lista problemas comuns que ocorrem com os manipuladores de eventos em componentes herdados.</span><span class="sxs-lookup"><span data-stu-id="93f0c-123">Lists common issues that occur with event handlers in inherited components.</span></span>
