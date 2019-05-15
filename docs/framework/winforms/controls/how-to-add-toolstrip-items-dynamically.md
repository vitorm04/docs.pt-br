---
title: 'Como: Adicionar itens do ToolStrip de forma dinâmica'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ContextMenuStrip control [Windows Forms]
- toolbars [Windows Forms], adding items dynamically
- ToolStrip control [Windows Forms]
ms.assetid: 0e8dea56-5f46-408b-914d-7e360341a234
ms.openlocfilehash: 08d08a292995cc5e12fbab3e91a0962c3b895a02
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65588881"
---
# <a name="how-to-add-toolstrip-items-dynamically"></a><span data-ttu-id="9799d-102">Como: Adicionar itens do ToolStrip de forma dinâmica</span><span class="sxs-lookup"><span data-stu-id="9799d-102">How to: Add ToolStrip Items Dynamically</span></span>
<span data-ttu-id="9799d-103">Você pode preencher a coleção de itens de menu de dinamicamente um <xref:System.Windows.Forms.ToolStrip> controlar quando o menu é aberto.</span><span class="sxs-lookup"><span data-stu-id="9799d-103">You can dynamically populate the menu item collection of a <xref:System.Windows.Forms.ToolStrip> control when the menu opens.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9799d-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9799d-104">Example</span></span>  
 <span data-ttu-id="9799d-105">O exemplo de código a seguir demonstra como adicionar dinamicamente os itens para um <xref:System.Windows.Forms.ContextMenuStrip> controle.</span><span class="sxs-lookup"><span data-stu-id="9799d-105">The following code example demonstrates how to dynamically add items to a <xref:System.Windows.Forms.ContextMenuStrip> control.</span></span> <span data-ttu-id="9799d-106">O exemplo também mostra como reutilizar o mesmo <xref:System.Windows.Forms.ContextMenuStrip> para três diferentes controles no formulário.</span><span class="sxs-lookup"><span data-stu-id="9799d-106">The example also shows how to reuse the same <xref:System.Windows.Forms.ContextMenuStrip> for three different controls on the form.</span></span>  
  
 <span data-ttu-id="9799d-107">No exemplo, um <xref:System.Windows.Forms.ToolStripDropDown.Opening> manipulador de eventos preenche a coleção de itens de menu.</span><span class="sxs-lookup"><span data-stu-id="9799d-107">In the example, an <xref:System.Windows.Forms.ToolStripDropDown.Opening> event handler populates the menu item collection.</span></span> <span data-ttu-id="9799d-108">O <xref:System.Windows.Forms.ToolStripDropDown.Opening> examina de manipulador de eventos do <xref:System.Windows.Forms.ContextMenuStrip.SourceControl%2A?displayProperty=nameWithType> e <xref:System.Windows.Forms.ToolStripItem.OwnerItem%2A?displayProperty=nameWithType> propriedades e adiciona um <xref:System.Windows.Forms.ToolStripItem> que descreve o controle do código-fonte.</span><span class="sxs-lookup"><span data-stu-id="9799d-108">The <xref:System.Windows.Forms.ToolStripDropDown.Opening> event handler examines the <xref:System.Windows.Forms.ContextMenuStrip.SourceControl%2A?displayProperty=nameWithType> and <xref:System.Windows.Forms.ToolStripItem.OwnerItem%2A?displayProperty=nameWithType> properties and adds a <xref:System.Windows.Forms.ToolStripItem> describing the source control.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#1)]  
[!code-csharp[System.Windows.Forms.ToolStrip.Misc#40](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#40)]
[!code-vb[System.Windows.Forms.ToolStrip.Misc#40](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#40)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="9799d-109">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="9799d-109">Compiling the Code</span></span>  
 <span data-ttu-id="9799d-110">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="9799d-110">This example requires:</span></span>  
  
- <span data-ttu-id="9799d-111">Referências aos assemblies System.Drawing e System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="9799d-111">References to the System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9799d-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9799d-112">See also</span></span>

- <xref:System.Windows.Forms.ContextMenuStrip>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.ToolStripItem>
- <xref:System.Windows.Forms.ToolStripMenuItem>
- <xref:System.Windows.Forms.ToolStripDropDownButton>
- [<span data-ttu-id="9799d-113">Controle ToolStrip</span><span class="sxs-lookup"><span data-stu-id="9799d-113">ToolStrip Control</span></span>](toolstrip-control-windows-forms.md)
