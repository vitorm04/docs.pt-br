---
title: 'Como: Configurar a mesclagem de Menu automática para aplicativos MDI'
ms.date: 03/30/2017
helpviewer_keywords:
- MenuStrip [Windows Forms], merging
- Merging [Windows Forms], automatic menu
ms.assetid: 55e32cad-1141-4a56-aa33-d9543ca3d393
ms.openlocfilehash: 152db39e7c947d5a49eaed81b00d13c02aa8014c
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57719722"
---
# <a name="how-to-set-up-automatic-menu-merging-for-mdi-applications"></a><span data-ttu-id="9ee59-102">Como: Configurar a mesclagem de Menu automática para aplicativos MDI</span><span class="sxs-lookup"><span data-stu-id="9ee59-102">How to: Set Up Automatic Menu Merging for MDI Applications</span></span>
<span data-ttu-id="9ee59-103">O procedimento a seguir fornece as etapas básicas para configurar a mesclagem automática em um aplicativo de interface de documentos múltiplos (MDI) com <xref:System.Windows.Forms.MenuStrip>.</span><span class="sxs-lookup"><span data-stu-id="9ee59-103">The following procedure gives the basic steps for setting up automatic merging in a multiple-document interface (MDI) application with <xref:System.Windows.Forms.MenuStrip>.</span></span>  
  
### <a name="to-set-up-automatic-menu-merging"></a><span data-ttu-id="9ee59-104">Para configurar a mesclagem de menu automática</span><span class="sxs-lookup"><span data-stu-id="9ee59-104">To set up automatic menu merging</span></span>  
  
1.  <span data-ttu-id="9ee59-105">Criar o formulário pai MDI, definindo sua <xref:System.Windows.Forms.Form.IsMdiContainer%2A> propriedade para `true`.</span><span class="sxs-lookup"><span data-stu-id="9ee59-105">Create the MDI parent form by setting its <xref:System.Windows.Forms.Form.IsMdiContainer%2A> property to `true`.</span></span>  
  
2.  <span data-ttu-id="9ee59-106">Adicionar um <xref:System.Windows.Forms.MenuStrip> para o pai MDI, configurando seus <xref:System.Windows.Forms.Form.MainMenuStrip%2A> propriedade com a <xref:System.Windows.Forms.MenuStrip>.</span><span class="sxs-lookup"><span data-stu-id="9ee59-106">Add a <xref:System.Windows.Forms.MenuStrip> to the MDI parent, setting its <xref:System.Windows.Forms.Form.MainMenuStrip%2A> property to that <xref:System.Windows.Forms.MenuStrip>.</span></span>  
  
3.  <span data-ttu-id="9ee59-107">Crie um formulário MDI filho e defina seu <xref:System.Windows.Forms.Form.MdiParent%2A> propriedade para o nome do formulário pai.</span><span class="sxs-lookup"><span data-stu-id="9ee59-107">Create an MDI child form, and set its <xref:System.Windows.Forms.Form.MdiParent%2A> property to the name of the parent form.</span></span>  
  
4.  <span data-ttu-id="9ee59-108">Adicionar um <xref:System.Windows.Forms.MenuStrip> ao formulário filho MDI.</span><span class="sxs-lookup"><span data-stu-id="9ee59-108">Add a <xref:System.Windows.Forms.MenuStrip> to the MDI child form.</span></span>  
  
5.  <span data-ttu-id="9ee59-109">No formulário filho, defina as <xref:System.Windows.Forms.ToolStripItem.Visible%2A> propriedade do <xref:System.Windows.Forms.MenuStrip> para `false`.</span><span class="sxs-lookup"><span data-stu-id="9ee59-109">On the child form, set the <xref:System.Windows.Forms.ToolStripItem.Visible%2A> property of the <xref:System.Windows.Forms.MenuStrip> to `false`.</span></span>  
  
6.  <span data-ttu-id="9ee59-110">Adicionar itens de menu para o formulário de filho <xref:System.Windows.Forms.MenuStrip> que você deseja mesclar com o formulário de pai <xref:System.Windows.Forms.MenuStrip> quando o formulário filho é ativado.</span><span class="sxs-lookup"><span data-stu-id="9ee59-110">Add menu items to the child form's <xref:System.Windows.Forms.MenuStrip> that you want to merge into the parent form's <xref:System.Windows.Forms.MenuStrip> when the child form is activated.</span></span>  
  
7.  <span data-ttu-id="9ee59-111">Use o <xref:System.Windows.Forms.ToolStripItem.MergeAction%2A> itens de propriedade no menu do formulário filho <xref:System.Windows.Forms.MenuStrip> para controlar como mesclar o formulário pai.</span><span class="sxs-lookup"><span data-stu-id="9ee59-111">Use the <xref:System.Windows.Forms.ToolStripItem.MergeAction%2A> property on the menu items in the child form's <xref:System.Windows.Forms.MenuStrip> to control how they merge into the parent form.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ee59-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9ee59-112">See also</span></span>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStripMenuItem>
- [<span data-ttu-id="9ee59-113">Visão geral do controle MenuStrip</span><span class="sxs-lookup"><span data-stu-id="9ee59-113">MenuStrip Control Overview</span></span>](menustrip-control-overview-windows-forms.md)
