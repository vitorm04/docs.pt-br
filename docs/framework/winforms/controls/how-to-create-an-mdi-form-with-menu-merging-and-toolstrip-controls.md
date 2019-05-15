---
title: 'Como: Criar um formulário MDI com mesclagem de menu e controles ToolStrip'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- toolbars [Windows Forms]
- ToolStripPanel control [Windows Forms]
- ToolStrip control [Windows Forms]
- MenuStrip control [Windows Forms]
ms.assetid: 64992ed9-44af-4baf-b45f-863e6ab35711
ms.openlocfilehash: 0edcc27968c55908cda0e881ed66f83323316711
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65591309"
---
# <a name="how-to-create-an-mdi-form-with-menu-merging-and-toolstrip-controls"></a><span data-ttu-id="b3505-102">Como: Criar um formulário MDI com mesclagem de menu e controles ToolStrip</span><span class="sxs-lookup"><span data-stu-id="b3505-102">How to: Create an MDI Form with Menu Merging and ToolStrip Controls</span></span>
<span data-ttu-id="b3505-103">O <xref:System.Windows.Forms?displayProperty=nameWithType> namespace oferece suporte a vários aplicativos MDI (interface MDI) de documento e o <xref:System.Windows.Forms.MenuStrip> controle dá suporte à mesclagem de menu.</span><span class="sxs-lookup"><span data-stu-id="b3505-103">The <xref:System.Windows.Forms?displayProperty=nameWithType> namespace supports multiple document interface (MDI) applications, and the <xref:System.Windows.Forms.MenuStrip> control supports menu merging.</span></span> <span data-ttu-id="b3505-104">Formulários MDI também podem <xref:System.Windows.Forms.ToolStrip> controles.</span><span class="sxs-lookup"><span data-stu-id="b3505-104">MDI forms can also <xref:System.Windows.Forms.ToolStrip> controls.</span></span>  
  
 <span data-ttu-id="b3505-105">Há suporte abrangente para este recurso no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b3505-105">There is extensive support for this feature in Visual Studio.</span></span>  
  
 <span data-ttu-id="b3505-106">Consulte também [passo a passo: Criando um formulário MDI com mesclagem de Menu e controles ToolStrip](walkthrough-creating-an-mdi-form-with-menu-merging-and-toolstrip-controls.md).</span><span class="sxs-lookup"><span data-stu-id="b3505-106">Also see [Walkthrough: Creating an MDI Form with Menu Merging and ToolStrip Controls](walkthrough-creating-an-mdi-form-with-menu-merging-and-toolstrip-controls.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b3505-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b3505-107">Example</span></span>  
 <span data-ttu-id="b3505-108">O exemplo de código a seguir demonstra como usar <xref:System.Windows.Forms.ToolStripPanel> controles com um formulário MDI.</span><span class="sxs-lookup"><span data-stu-id="b3505-108">The following code example demonstrates how to use <xref:System.Windows.Forms.ToolStripPanel> controls with an MDI form.</span></span> <span data-ttu-id="b3505-109">O formulário também dá suporte à mesclagem com menus filho.</span><span class="sxs-lookup"><span data-stu-id="b3505-109">The form also supports menu merging with child menus.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.MdiForm#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.MdiForm/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStrip.MdiForm#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.MdiForm/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="b3505-110">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="b3505-110">Compiling the Code</span></span>  
 <span data-ttu-id="b3505-111">Este exemplo de código requer:</span><span class="sxs-lookup"><span data-stu-id="b3505-111">This code example requires:</span></span>  
  
- <span data-ttu-id="b3505-112">Referências aos assemblies System.Drawing e System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="b3505-112">References to the System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3505-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b3505-113">See also</span></span>

- [<span data-ttu-id="b3505-114">Controle ToolStrip</span><span class="sxs-lookup"><span data-stu-id="b3505-114">ToolStrip Control</span></span>](toolstrip-control-windows-forms.md)
