---
title: Captura do mouse no Windows Forms
ms.date: 03/30/2017
helpviewer_keywords:
- mouse [Windows Forms], capture
ms.assetid: 8911d4b0-a4f8-4f93-8246-371aebd27d0c
ms.openlocfilehash: 30432c6978f60cc9ad47d5df5dafc7aa45229f3b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59151639"
---
# <a name="mouse-capture-in-windows-forms"></a><span data-ttu-id="f2398-102">Captura do mouse no Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f2398-102">Mouse Capture in Windows Forms</span></span>
<span data-ttu-id="f2398-103">*Captura do mouse* significa quando um controle toma o comando todas as entradas do mouse.</span><span class="sxs-lookup"><span data-stu-id="f2398-103">*Mouse capture* refers to when a control takes command of all mouse input.</span></span> <span data-ttu-id="f2398-104">Quando um controle tiver capturado o mouse, ele recebe a entrada do mouse com o ponteiro estando ou não dentro de suas bordas.</span><span class="sxs-lookup"><span data-stu-id="f2398-104">When a control has captured the mouse, it receives mouse input whether or not the pointer is within its borders.</span></span>  
  
## <a name="setting-mouse-capture"></a><span data-ttu-id="f2398-105">Configuração da captura do mouse</span><span class="sxs-lookup"><span data-stu-id="f2398-105">Setting Mouse Capture</span></span>  
 <span data-ttu-id="f2398-106">nos Windows Forms, o mouse é capturado pelo controle quando o usuário pressiona um botão do mouse em um controle e o mouse é liberado pelo controle quando o usuário solta o botão do mouse.</span><span class="sxs-lookup"><span data-stu-id="f2398-106">In Windows Forms the mouse is captured by the control when the user presses a mouse button on a control, and the mouse is released by the control when the user releases the mouse button.</span></span>  
  
 <span data-ttu-id="f2398-107">O <xref:System.Windows.Forms.Control.Capture%2A> propriedade do <xref:System.Windows.Forms.Control> classe Especifica se um controle capturou o mouse.</span><span class="sxs-lookup"><span data-stu-id="f2398-107">The <xref:System.Windows.Forms.Control.Capture%2A> property of the <xref:System.Windows.Forms.Control> class specifies whether a control has captured the mouse.</span></span> <span data-ttu-id="f2398-108">Para determinar quando um controle perde a captura do mouse, manipule o <xref:System.Windows.Forms.Control.MouseCaptureChanged> eventos.</span><span class="sxs-lookup"><span data-stu-id="f2398-108">To determine when a control loses mouse capture, handle the <xref:System.Windows.Forms.Control.MouseCaptureChanged> event.</span></span>  
  
 <span data-ttu-id="f2398-109">Somente a janela em primeiro plano pode capturar o mouse.</span><span class="sxs-lookup"><span data-stu-id="f2398-109">Only the foreground window can capture the mouse.</span></span> <span data-ttu-id="f2398-110">Quando uma janela de tela de fundo tenta capturar o mouse, a janela recebe mensagens apenas de eventos de mouse que ocorrerem quando o ponteiro do mouse estiver dentro a parte visível da janela.</span><span class="sxs-lookup"><span data-stu-id="f2398-110">When a background window attempts to capture the mouse, the window receives messages only for mouse events that occur when the mouse pointer is within the visible portion of the window.</span></span> <span data-ttu-id="f2398-111">Além disso, mesmo que a janela em primeiro plano tenha capturado o mouse, o usuário ainda poderá clicar em outra janela, colocando-a em primeiro plano.</span><span class="sxs-lookup"><span data-stu-id="f2398-111">Also, even if the foreground window has captured the mouse, the user can still click another window, bringing it to the foreground.</span></span> <span data-ttu-id="f2398-112">Quando o mouse é capturado, as teclas de atalho não funcionam.</span><span class="sxs-lookup"><span data-stu-id="f2398-112">When the mouse is captured, shortcut keys do not work.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2398-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f2398-113">See also</span></span>

- [<span data-ttu-id="f2398-114">Entrada do mouse em um aplicativo do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f2398-114">Mouse Input in a Windows Forms Application</span></span>](mouse-input-in-a-windows-forms-application.md)
