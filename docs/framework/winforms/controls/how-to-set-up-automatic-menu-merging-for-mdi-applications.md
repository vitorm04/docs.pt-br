---
title: "Como configurar a mesclagem de menu automática para aplicativos MDI"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MenuStrip [Windows Forms], merging
- Merging [Windows Forms], automatic menu
ms.assetid: 55e32cad-1141-4a56-aa33-d9543ca3d393
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 1e99aed38ed6c3af3424c264631f0eaf27e46af7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-set-up-automatic-menu-merging-for-mdi-applications"></a><span data-ttu-id="8c6ff-102">Como configurar a mesclagem de menu automática para aplicativos MDI</span><span class="sxs-lookup"><span data-stu-id="8c6ff-102">How to: Set Up Automatic Menu Merging for MDI Applications</span></span>
<span data-ttu-id="8c6ff-103">O procedimento a seguir fornece as etapas básicas para configurar uma mesclagem automática em um aplicativo de interface de documentos múltiplos (MDI) com <xref:System.Windows.Forms.MenuStrip>.</span><span class="sxs-lookup"><span data-stu-id="8c6ff-103">The following procedure gives the basic steps for setting up automatic merging in a multiple-document interface (MDI) application with <xref:System.Windows.Forms.MenuStrip>.</span></span>  
  
### <a name="to-set-up-automatic-menu-merging"></a><span data-ttu-id="8c6ff-104">Para configurar a mesclagem de menu automática</span><span class="sxs-lookup"><span data-stu-id="8c6ff-104">To set up automatic menu merging</span></span>  
  
1.  <span data-ttu-id="8c6ff-105">Criar o formulário pai MDI definindo seu <xref:System.Windows.Forms.Form.IsMdiContainer%2A> propriedade `true`.</span><span class="sxs-lookup"><span data-stu-id="8c6ff-105">Create the MDI parent form by setting its <xref:System.Windows.Forms.Form.IsMdiContainer%2A> property to `true`.</span></span>  
  
2.  <span data-ttu-id="8c6ff-106">Adicionar um <xref:System.Windows.Forms.MenuStrip> para o pai MDI, definindo seu <xref:System.Windows.Forms.Form.MainMenuStrip%2A> propriedade ao <xref:System.Windows.Forms.MenuStrip>.</span><span class="sxs-lookup"><span data-stu-id="8c6ff-106">Add a <xref:System.Windows.Forms.MenuStrip> to the MDI parent, setting its <xref:System.Windows.Forms.Form.MainMenuStrip%2A> property to that <xref:System.Windows.Forms.MenuStrip>.</span></span>  
  
3.  <span data-ttu-id="8c6ff-107">Criar um formulário MDI filho e defina seu <xref:System.Windows.Forms.Form.MdiParent%2A> propriedade para o nome do formulário pai.</span><span class="sxs-lookup"><span data-stu-id="8c6ff-107">Create an MDI child form, and set its <xref:System.Windows.Forms.Form.MdiParent%2A> property to the name of the parent form.</span></span>  
  
4.  <span data-ttu-id="8c6ff-108">Adicionar um <xref:System.Windows.Forms.MenuStrip> para o formulário filho MDI.</span><span class="sxs-lookup"><span data-stu-id="8c6ff-108">Add a <xref:System.Windows.Forms.MenuStrip> to the MDI child form.</span></span>  
  
5.  <span data-ttu-id="8c6ff-109">No formulário filho, defina a <xref:System.Windows.Forms.ToolStripItem.Visible%2A> propriedade o <xref:System.Windows.Forms.MenuStrip> para `false`.</span><span class="sxs-lookup"><span data-stu-id="8c6ff-109">On the child form, set the <xref:System.Windows.Forms.ToolStripItem.Visible%2A> property of the <xref:System.Windows.Forms.MenuStrip> to `false`.</span></span>  
  
6.  <span data-ttu-id="8c6ff-110">Adicionar itens de menu do formulário filho <xref:System.Windows.Forms.MenuStrip> que você deseja mesclar do formulário pai <xref:System.Windows.Forms.MenuStrip> quando o formulário filho é ativado.</span><span class="sxs-lookup"><span data-stu-id="8c6ff-110">Add menu items to the child form's <xref:System.Windows.Forms.MenuStrip> that you want to merge into the parent form's <xref:System.Windows.Forms.MenuStrip> when the child form is activated.</span></span>  
  
7.  <span data-ttu-id="8c6ff-111">Use o <xref:System.Windows.Forms.ToolStripItem.MergeAction%2A> itens de propriedade no menu do formulário filho <xref:System.Windows.Forms.MenuStrip> para controlar como mesclar o formulário pai.</span><span class="sxs-lookup"><span data-stu-id="8c6ff-111">Use the <xref:System.Windows.Forms.ToolStripItem.MergeAction%2A> property on the menu items in the child form's <xref:System.Windows.Forms.MenuStrip> to control how they merge into the parent form.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c6ff-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8c6ff-112">See Also</span></span>  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStripMenuItem>  
 [<span data-ttu-id="8c6ff-113">Visão geral do controle MenuStrip</span><span class="sxs-lookup"><span data-stu-id="8c6ff-113">MenuStrip Control Overview</span></span>](../../../../docs/framework/winforms/controls/menustrip-control-overview-windows-forms.md)
