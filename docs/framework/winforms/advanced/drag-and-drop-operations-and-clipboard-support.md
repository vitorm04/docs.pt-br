---
title: Operações de arrastar e soltar e suporte à área de transferência
ms.date: 03/30/2017
helpviewer_keywords:
- drag and drop [Windows Forms]
- drag and drop [Windows Forms], Windows Forms
- Clipboard [Windows Forms], Windows Forms
ms.assetid: 7cce79b6-5835-46fd-b690-73f12ad368b2
ms.openlocfilehash: 281d102ecd02623e7e18ebf4fc569538ebbdaf7f
ms.sourcegitcommit: acd8ed14fe94e9d4e3a7fb685fe83d05e941073c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/20/2019
ms.locfileid: "56442003"
---
# <a name="drag-and-drop-operations-and-clipboard-support"></a><span data-ttu-id="7528b-102">Operações de arrastar e soltar e suporte à área de transferência</span><span class="sxs-lookup"><span data-stu-id="7528b-102">Drag-and-Drop Operations and Clipboard Support</span></span>
<span data-ttu-id="7528b-103">Você pode habilitar operações de arrastar e soltar do usuário dentro de um aplicativo baseado em Windows manipulando uma série de eventos, mais notavelmente os <xref:System.Windows.Forms.Control.DragEnter>, <xref:System.Windows.Forms.Control.DragLeave>, e <xref:System.Windows.Forms.Control.DragDrop> eventos.</span><span class="sxs-lookup"><span data-stu-id="7528b-103">You can enable user drag-and-drop operations within a Windows-based application by handling a series of events, most notably the <xref:System.Windows.Forms.Control.DragEnter>, <xref:System.Windows.Forms.Control.DragLeave>, and <xref:System.Windows.Forms.Control.DragDrop> events.</span></span>  
  
 <span data-ttu-id="7528b-104">Você também pode implementar o suporte ao usuário recortar/copiar/colar e a transferência de dados do usuário para a área de transferência em seus aplicativos baseados no Windows usando chamadas de método simples.</span><span class="sxs-lookup"><span data-stu-id="7528b-104">You can also implement user cut/copy/paste support and user data transfer to the Clipboard within your Windows-based applications by using simple method calls.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7528b-105">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="7528b-105">In This Section</span></span>  
 [<span data-ttu-id="7528b-106">Passo a passo: Executando uma operação de arrastar e soltar no Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7528b-106">Walkthrough: Performing a Drag-and-Drop Operation in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/walkthrough-performing-a-drag-and-drop-operation-in-windows-forms.md)  
 <span data-ttu-id="7528b-107">Explica como iniciar uma operação do tipo "arrastar e soltar".</span><span class="sxs-lookup"><span data-stu-id="7528b-107">Explains how to start a drag-and-drop operation.</span></span>  
  
 [<span data-ttu-id="7528b-108">Como: Executar operações de arrastar e soltar entre aplicativos</span><span class="sxs-lookup"><span data-stu-id="7528b-108">How to: Perform Drag-and-Drop Operations Between Applications</span></span>](../../../../docs/framework/winforms/advanced/how-to-perform-drag-and-drop-operations-between-applications.md)  
 <span data-ttu-id="7528b-109">Ilustra como realizar operações do tipo "arrastar e soltar" entre aplicativos.</span><span class="sxs-lookup"><span data-stu-id="7528b-109">Illustrates how to accomplish drag-and-drop operations across applications.</span></span>  
  
 [<span data-ttu-id="7528b-110">Como: Adicionar dados à área de transferência</span><span class="sxs-lookup"><span data-stu-id="7528b-110">How to: Add Data to the Clipboard</span></span>](../../../../docs/framework/winforms/advanced/how-to-add-data-to-the-clipboard.md)  
 <span data-ttu-id="7528b-111">Descreve uma maneira de inserir via programação informações na área de transferência.</span><span class="sxs-lookup"><span data-stu-id="7528b-111">Describes a way to programmatically insert information on the Clipboard.</span></span>  
  
 [<span data-ttu-id="7528b-112">Como: Recuperar dados da área de transferência</span><span class="sxs-lookup"><span data-stu-id="7528b-112">How to: Retrieve Data from the Clipboard</span></span>](../../../../docs/framework/winforms/advanced/how-to-retrieve-data-from-the-clipboard.md)  
 <span data-ttu-id="7528b-113">Descreve como acessar os dados armazenados na área de transferência.</span><span class="sxs-lookup"><span data-stu-id="7528b-113">Describes how to access the data stored on the Clipboard.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="7528b-114">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="7528b-114">Related Sections</span></span>  
 [<span data-ttu-id="7528b-115">Funcionalidade do tipo "arrastar e soltar" no Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7528b-115">Drag-and-Drop Functionality in Windows Forms</span></span>](../../../../docs/framework/winforms/drag-and-drop-functionality-in-windows-forms.md)  
 <span data-ttu-id="7528b-116">Descreve os métodos, os eventos e as classes usados para implementar o comportamento do tipo "arrastar e soltar".</span><span class="sxs-lookup"><span data-stu-id="7528b-116">Describes the methods, events, and classes used to implement drag-and-drop behavior.</span></span>  
  
 <xref:System.Windows.Forms.Control.QueryContinueDrag>  
 <span data-ttu-id="7528b-117">Descreve a complexidade do evento que pede permissão para continuar a operação de arrastar.</span><span class="sxs-lookup"><span data-stu-id="7528b-117">Describes the intricacies of the event that asks permission to continue the drag operation.</span></span>  
  
 <xref:System.Windows.Forms.Control.DoDragDrop%2A>  
 <span data-ttu-id="7528b-118">Descreve a complexidade do método essencial para começar a operação de arrastar.</span><span class="sxs-lookup"><span data-stu-id="7528b-118">Describes the intricacies of the method that is central to beginning a drag operation.</span></span>  
  
 <xref:System.Windows.Forms.Clipboard>  
 <span data-ttu-id="7528b-119">Consulte também [como: Enviar dados para o filho MDI ativo](how-to-send-data-to-the-active-mdi-child.md).</span><span class="sxs-lookup"><span data-stu-id="7528b-119">Also see [How to: Send Data to the Active MDI Child](how-to-send-data-to-the-active-mdi-child.md).</span></span>
