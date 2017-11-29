---
title: "Operações de arrastar e soltar e suporte à área de transferência"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- drag and drop [Windows Forms]
- drag and drop [Windows Forms], Windows Forms
- Clipboard [Windows Forms], Windows Forms
ms.assetid: 7cce79b6-5835-46fd-b690-73f12ad368b2
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 722c37645d95009ce03bbbf813bc9f9fb2418e60
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2017
---
# <a name="drag-and-drop-operations-and-clipboard-support"></a><span data-ttu-id="e6b9e-102">Operações de arrastar e soltar e suporte à área de transferência</span><span class="sxs-lookup"><span data-stu-id="e6b9e-102">Drag-and-Drop Operations and Clipboard Support</span></span>
<span data-ttu-id="e6b9e-103">Você pode habilitar operações arrastar e soltar do usuário dentro de um aplicativo baseado em Windows manipulando uma série de eventos, particularmente o <xref:System.Windows.Forms.Control.DragEnter>, <xref:System.Windows.Forms.Control.DragLeave>, e <xref:System.Windows.Forms.Control.DragDrop> eventos.</span><span class="sxs-lookup"><span data-stu-id="e6b9e-103">You can enable user drag-and-drop operations within a Windows-based application by handling a series of events, most notably the <xref:System.Windows.Forms.Control.DragEnter>, <xref:System.Windows.Forms.Control.DragLeave>, and <xref:System.Windows.Forms.Control.DragDrop> events.</span></span>  
  
 <span data-ttu-id="e6b9e-104">Você também pode implementar o suporte ao usuário recortar/copiar/colar e a transferência de dados do usuário para a área de transferência em seus aplicativos baseados no Windows usando chamadas de método simples.</span><span class="sxs-lookup"><span data-stu-id="e6b9e-104">You can also implement user cut/copy/paste support and user data transfer to the Clipboard within your Windows-based applications by using simple method calls.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e6b9e-105">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="e6b9e-105">In This Section</span></span>  
 [<span data-ttu-id="e6b9e-106">Instruções Passo a Passo: Executando uma Operação do Tipo "Arrastar e Soltar" nos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e6b9e-106">Walkthrough: Performing a Drag-and-Drop Operation in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/walkthrough-performing-a-drag-and-drop-operation-in-windows-forms.md)  
 <span data-ttu-id="e6b9e-107">Explica como iniciar uma operação do tipo "arrastar e soltar".</span><span class="sxs-lookup"><span data-stu-id="e6b9e-107">Explains how to start a drag-and-drop operation.</span></span>  
  
 [<span data-ttu-id="e6b9e-108">Como Executar Operações de do Tipo "Arrastar e Soltar" entre Aplicativos</span><span class="sxs-lookup"><span data-stu-id="e6b9e-108">How to: Perform Drag-and-Drop Operations Between Applications</span></span>](../../../../docs/framework/winforms/advanced/how-to-perform-drag-and-drop-operations-between-applications.md)  
 <span data-ttu-id="e6b9e-109">Ilustra como realizar operações do tipo "arrastar e soltar" entre aplicativos.</span><span class="sxs-lookup"><span data-stu-id="e6b9e-109">Illustrates how to accomplish drag-and-drop operations across applications.</span></span>  
  
 [<span data-ttu-id="e6b9e-110">Como Adicionar Dados à Área de Transferência</span><span class="sxs-lookup"><span data-stu-id="e6b9e-110">How to: Add Data to the Clipboard</span></span>](../../../../docs/framework/winforms/advanced/how-to-add-data-to-the-clipboard.md)  
 <span data-ttu-id="e6b9e-111">Descreve uma maneira de inserir via programação informações na área de transferência.</span><span class="sxs-lookup"><span data-stu-id="e6b9e-111">Describes a way to programmatically insert information on the Clipboard.</span></span>  
  
 [<span data-ttu-id="e6b9e-112">Como Recuperar Dados da Área de Transferência</span><span class="sxs-lookup"><span data-stu-id="e6b9e-112">How to: Retrieve Data from the Clipboard</span></span>](../../../../docs/framework/winforms/advanced/how-to-retrieve-data-from-the-clipboard.md)  
 <span data-ttu-id="e6b9e-113">Descreve como acessar os dados armazenados na área de transferência.</span><span class="sxs-lookup"><span data-stu-id="e6b9e-113">Describes how to access the data stored on the Clipboard.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="e6b9e-114">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="e6b9e-114">Related Sections</span></span>  
 [<span data-ttu-id="e6b9e-115">Funcionalidade do tipo "arrastar e soltar" nos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e6b9e-115">Drag-and-Drop Functionality in Windows Forms</span></span>](../../../../docs/framework/winforms/drag-and-drop-functionality-in-windows-forms.md)  
 <span data-ttu-id="e6b9e-116">Descreve os métodos, os eventos e as classes usados para implementar o comportamento do tipo "arrastar e soltar".</span><span class="sxs-lookup"><span data-stu-id="e6b9e-116">Describes the methods, events, and classes used to implement drag-and-drop behavior.</span></span>  
  
 <xref:System.Windows.Forms.Control.QueryContinueDrag>  
 <span data-ttu-id="e6b9e-117">Descreve a complexidade do evento que pede permissão para continuar a operação de arrastar.</span><span class="sxs-lookup"><span data-stu-id="e6b9e-117">Describes the intricacies of the event that asks permission to continue the drag operation.</span></span>  
  
 <xref:System.Windows.Forms.Control.DoDragDrop%2A>  
 <span data-ttu-id="e6b9e-118">Descreve a complexidade do método essencial para começar a operação de arrastar.</span><span class="sxs-lookup"><span data-stu-id="e6b9e-118">Describes the intricacies of the method that is central to beginning a drag operation.</span></span>  
  
 <xref:System.Windows.Forms.Clipboard>  
 <span data-ttu-id="e6b9e-119">Veja também [Como enviar dados para o filho MDI ativo](http://msdn.microsoft.com/library/y0hkh2c8\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="e6b9e-119">Also see [How to: Send Data to the Active MDI Child](http://msdn.microsoft.com/library/y0hkh2c8\(v=vs.110\)).</span></span>
