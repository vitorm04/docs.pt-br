---
title: Controle StatusBar (Windows Forms)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- StatusBar control [Windows Forms]
- status bars [Windows Forms], creating
ms.assetid: 6f543e27-cf78-4b7f-b4d0-6a8030155d48
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 775d1a350075811dc02ae33efd1a6ae05328c4ff
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2017
---
# <a name="statusbar-control-windows-forms"></a><span data-ttu-id="3d1c6-102">Controle StatusBar (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="3d1c6-102">StatusBar Control (Windows Forms)</span></span>
> [!NOTE]
>  <span data-ttu-id="3d1c6-103">O controle <xref:System.Windows.Forms.ToolStripStatusLabel> substitui e adiciona funcionalidade ao controle <xref:System.Windows.Forms.StatusBar>, no entanto, o controle <xref:System.Windows.Forms.StatusBar> é mantido para compatibilidade com versões anteriores e para uso futuro, se desejado.</span><span class="sxs-lookup"><span data-stu-id="3d1c6-103">The <xref:System.Windows.Forms.ToolStripStatusLabel> control replaces and adds functionality to the <xref:System.Windows.Forms.StatusBar> control; however, the <xref:System.Windows.Forms.StatusBar> control is retained for both backward compatibility and future use, if you choose.</span></span>  
  
 <span data-ttu-id="3d1c6-104">Windows Forms <xref:System.Windows.Forms.StatusBar> controle é usado em formulários como uma área, normalmente exibida na parte inferior de uma janela, no qual um aplicativo pode exibir vários tipos de informações de status.</span><span class="sxs-lookup"><span data-stu-id="3d1c6-104">The Windows Forms <xref:System.Windows.Forms.StatusBar> control is used on forms as an area, usually displayed at the bottom of a window, in which an application can display various kinds of status information.</span></span> <span data-ttu-id="3d1c6-105"><xref:System.Windows.Forms.StatusBar>controles podem ter painéis da barra de status neles que exibem ícones para indicar o estado ou uma série de ícones em uma animação que indicam que um processo está funcionando; Por exemplo, Microsoft Word indicando que o documento está sendo salvo.</span><span class="sxs-lookup"><span data-stu-id="3d1c6-105"><xref:System.Windows.Forms.StatusBar> controls can have status-bar panels on them that display icons to indicate state, or a series of icons in an animation that indicate a process is working; for example, Microsoft Word indicating that the document is being saved.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="3d1c6-106">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="3d1c6-106">In This Section</span></span>  
 [<span data-ttu-id="3d1c6-107">Visão geral do controle StatusBar</span><span class="sxs-lookup"><span data-stu-id="3d1c6-107">StatusBar Control Overview</span></span>](../../../../docs/framework/winforms/controls/statusbar-control-overview-windows-forms.md)  
 <span data-ttu-id="3d1c6-108">Apresenta os conceitos gerais do <xref:System.Windows.Forms.StatusBar> controle, que permite que os usuários vejam as informações relevantes para o controle que tem foco.</span><span class="sxs-lookup"><span data-stu-id="3d1c6-108">Introduces the general concepts of the <xref:System.Windows.Forms.StatusBar> control, which enables users to see relevant information for the control that has focus.</span></span>  
  
 [<span data-ttu-id="3d1c6-109">Como adicionar painéis a um controle StatusBar</span><span class="sxs-lookup"><span data-stu-id="3d1c6-109">How to: Add Panels to a StatusBar Control</span></span>](../../../../docs/framework/winforms/controls/how-to-add-panels-to-a-statusbar-control.md)  
 <span data-ttu-id="3d1c6-110">Explica como adicionar painéis programáveis para o <xref:System.Windows.Forms.StatusBar> controle.</span><span class="sxs-lookup"><span data-stu-id="3d1c6-110">Explains how to add programmable panels to the <xref:System.Windows.Forms.StatusBar> control.</span></span>  
  
 [<span data-ttu-id="3d1c6-111">Como determinar qual painel no controle StatusBar dos Windows Forms foi clicado</span><span class="sxs-lookup"><span data-stu-id="3d1c6-111">How to: Determine Which Panel in the Windows Forms StatusBar Control Was Clicked</span></span>](../../../../docs/framework/winforms/controls/determine-which-panel-wf-statusbar-control-was-clicked.md)  
 <span data-ttu-id="3d1c6-112">Explica como manipular <xref:System.Windows.Forms.Control.Click> eventos gerados a partir de <xref:System.Windows.Forms.StatusBar> controle.</span><span class="sxs-lookup"><span data-stu-id="3d1c6-112">Explains how to handle <xref:System.Windows.Forms.Control.Click> events raised from the <xref:System.Windows.Forms.StatusBar> control.</span></span>  
  
 [<span data-ttu-id="3d1c6-113">Como definir o tamanho de painéis da barra de status</span><span class="sxs-lookup"><span data-stu-id="3d1c6-113">How to: Set the Size of Status-Bar Panels</span></span>](../../../../docs/framework/winforms/controls/how-to-set-the-size-of-status-bar-panels.md)  
 <span data-ttu-id="3d1c6-114">Fornece detalhes sobre as propriedades que controlam a largura e redimensionam o comportamento dos painéis da barra de status em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="3d1c6-114">Gives details on the properties that control the width and resize behavior of status-bar panels at run time.</span></span>  
  
 [<span data-ttu-id="3d1c6-115">Passo a passo: atualizando informações da barra de status em tempo de execução</span><span class="sxs-lookup"><span data-stu-id="3d1c6-115">Walkthrough: Updating Status Bar Information at Run Time</span></span>](../../../../docs/framework/winforms/controls/walkthrough-updating-status-bar-information-at-run-time.md)  
 <span data-ttu-id="3d1c6-116">Explica como controlar programaticamente os dados dentro de painéis da barra de status.</span><span class="sxs-lookup"><span data-stu-id="3d1c6-116">Explains how to programmatically control the data within status-bar panels.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="3d1c6-117">Referência</span><span class="sxs-lookup"><span data-stu-id="3d1c6-117">Reference</span></span>  
 <xref:System.Windows.Forms.StatusBar>  
 <span data-ttu-id="3d1c6-118">Fornece informações de referência sobre a classe e seus membros.</span><span class="sxs-lookup"><span data-stu-id="3d1c6-118">Provides reference information on the class and its members.</span></span>  
  
 <xref:System.Windows.Forms.ToolStripStatusLabel>  
 <span data-ttu-id="3d1c6-119">Substitui e adiciona a funcionalidade para o <xref:System.Windows.Forms.StatusBar> controle.</span><span class="sxs-lookup"><span data-stu-id="3d1c6-119">Replaces and adds functionality to the <xref:System.Windows.Forms.StatusBar> control.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="3d1c6-120">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="3d1c6-120">Related Sections</span></span>  
 [<span data-ttu-id="3d1c6-121">Controles a serem usados nos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="3d1c6-121">Controls to Use on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
 <span data-ttu-id="3d1c6-122">Fornece uma lista completa dos controles dos Windows Forms, com links para informações sobre seu uso.</span><span class="sxs-lookup"><span data-stu-id="3d1c6-122">Provides a complete list of Windows Forms controls, with links to information on their use.</span></span>
